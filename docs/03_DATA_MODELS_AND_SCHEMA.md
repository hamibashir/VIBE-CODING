# 03: Data Models & Database Schema

> **DOCUMENT STATUS: GENERIC TEMPLATE (AWAITING PROJECT IDEA)**  
> *When a project idea is chosen, this document will define the concrete tables, columns, indexes, foreign keys, and migration rules.*

---

## 1. Core Database Principles
- **Relational Integrity:** Enforce foreign keys and uniqueness at the database level, not only in application code.
- **Audit Columns:** Every main table must include `id`, `created_at`, and `updated_at`.
- **Primary Keys:** Consistent strategy (`UUID v4` or `cuid2` for distributed/web apps, or `BIGINT IDENTITY` for simple SQL).
- **Naming Conventions:**
  - Table names: `snake_case`, plural (e.g. `users`, `projects`, `task_items`).
  - Column names: `snake_case` (e.g. `user_id`, `created_at`).
  - Foreign keys: `<singular_table>_id` (e.g. `user_id` references `users(id)`).
- **Transactions:** Use database transactions (`db.$transaction` or `BEGIN ... COMMIT`) whenever updating multiple related records.

---

## 2. Core Entity Definitions (Template)

### 2.1 Entity: `users`
*Represents an authenticated user account.*

| Column | Type | Constraints | Description |
|---|---|---|---|
| `id` | `UUID` / `TEXT` | `PRIMARY KEY` | Unique user ID |
| `email` | `VARCHAR(255)` | `UNIQUE, NOT NULL` | Login email address |
| `password_hash` | `TEXT` | `NULLABLE` | Argon2/Bcrypt hash (null if OAuth) |
| `name` | `VARCHAR(100)` | `NULLABLE` | Display name |
| `role` | `VARCHAR(20)` | `DEFAULT 'user'` | Role: `user`, `admin` |
| `created_at` | `TIMESTAMP` | `DEFAULT NOW()` | Record creation timestamp |
| `updated_at` | `TIMESTAMP` | `DEFAULT NOW()` | Record update timestamp |

### 2.2 Entity: `[REPLACE: Primary Domain Entity, e.g. projects / documents]`
*Represents the core application item owned by a user.*

| Column | Type | Constraints | Description |
|---|---|---|---|
| `id` | `UUID` / `TEXT` | `PRIMARY KEY` | Unique record ID |
| `user_id` | `UUID` / `TEXT` | `NOT NULL, REFERENCES users(id) ON DELETE CASCADE` | Owner user |
| `title` | `VARCHAR(255)` | `NOT NULL` | Main title/name |
| `status` | `VARCHAR(50)` | `DEFAULT 'draft'` | Status enum/string |
| `metadata` | `JSONB` | `DEFAULT '{}'` | Flexible attributes (if needed) |
| `created_at` | `TIMESTAMP` | `DEFAULT NOW()` | Creation timestamp |
| `updated_at` | `TIMESTAMP` | `DEFAULT NOW()` | Update timestamp |

*(Add secondary entities here when project idea is defined)*

---

## 3. Relationships & Foreign Key Rules
- **Cascade Rules:** Explicitly declare `ON DELETE CASCADE` or `ON DELETE RESTRICT`. Never leave orphan records in the database.
- **Foreign Key Indexing:** Every foreign key column (e.g. `user_id`) must have an index to ensure fast JOIN and lookup performance.

---

## 4. Migration & Schema Discipline
- **Migrations are Code:** Schema changes must be checked into version control (e.g. Prisma migrations or SQL migration files).
- **No Manual Direct Edits:** Never alter columns or tables directly in production DB without a tracked migration file.
- **Rollback Safety:** Avoid destructive migrations (dropping active columns) without deprecation phases.
