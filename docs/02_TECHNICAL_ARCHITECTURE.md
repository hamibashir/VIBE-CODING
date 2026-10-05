# 02: Technical Architecture & System Design

> **DOCUMENT STATUS: GENERIC TEMPLATE (AWAITING PROJECT IDEA)**  
> *When a project idea is chosen, this document will be populated with the concrete tech stack, directory structure, API contracts, and deployment choices.*

---

## 1. Confirmed Technology Stack

| Layer | Selected Technology | Version / Tool | Rationale |
|---|---|---|---|
| **Framework** | `[REPLACE: e.g. Next.js App Router / Vite React / Express]` | `[REPLACE]` | Fast SSR / SPA performance |
| **Language** | `TypeScript` | Strict mode | Type safety & fewer runtime errors |
| **Styling** | `[REPLACE: e.g. Tailwind CSS / Vanilla CSS]` | `[REPLACE]` | Modern maintainable design system |
| **Database** | `[REPLACE: e.g. PostgreSQL / SQLite / Supabase]` | `[REPLACE]` | Relational integrity |
| **ORM / Query** | `[REPLACE: e.g. Prisma / Drizzle / Kysely]` | `[REPLACE]` | Type-safe queries & migrations |
| **Auth** | `[REPLACE: e.g. Auth.js / Supabase Auth / Custom JWT]` | `[REPLACE]` | Secure session management |
| **Validation** | `Zod` | `[REPLACE]` | Input validation at boundary |
| **Package Manager**| `npm` (Windows PowerShell compatible) | Default | Project standard |

---

## 2. System Architecture & Data Flow

```
[ Browser / Client UI ]
        │  (HTTP / Fetch / JSON)
        ▼
[ API Routes / Server Actions ] ──► (Zod Validation)
        │
        ▼
[ Authentication & Authorization Guard ]
        │
        ▼
[ Service / Business Logic Layer ]
        │
        ▼
[ Data Access / ORM Layer ]
        │
        ▼
[ Relational Database (PostgreSQL / SQLite) ]
```

### Architectural Principles:
1. **Thin UI Components:** Keep business and DB logic out of client components.
2. **Server-Side Security:** Secrets, API keys, and sensitive business rules stay strictly on the server.
3. **Validate at the Perimeter:** Validate all inbound requests with Zod before processing.
4. **No Multiple Stack Choices:** Settle on ONE ORM, ONE styling system, and ONE state strategy.

---

## 3. Standard Directory Structure

```
[REPLACE: Customize for chosen framework, e.g. Next.js App Router]:
src/
├── app/                  # Routes, layouts, and page components
│   ├── api/              # API endpoints / Route Handlers
│   ├── (auth)/           # Authentication routes (login, register)
│   └── (dashboard)/      # Protected application views
├── components/           # Reusable UI components
│   ├── ui/               # Base design system primitives (buttons, inputs, modal)
│   └── shared/           # Compound domain components
├── lib/                  # Shared utilities, DB client, auth helpers
│   ├── db.ts             # Database connection singleton
│   ├── auth.ts           # Authentication config & session helper
│   └── utils.ts          # Formatting, classnames, helpers
├── server/               # Server-side services & data access functions
│   └── services/         # Pure business logic
├── types/                # Shared TypeScript types & interfaces
└── styles/               # Global CSS & theme tokens
```

---

## 4. API Design & Conventions
- **Base URL:** `/api/v1` (or framework native routes)
- **Format:** Strict JSON request and response payloads.
- **HTTP Methods:**
  - `GET`: Read records (idempotent, no mutations).
  - `POST`: Create a new record.
  - `PUT` / `PATCH`: Update an existing record.
  - `DELETE`: Remove a record.
- **Standard JSON Response Envelope:**
  ```typescript
  // Success
  { "success": true, "data": { ... } }

  // Error
  { "success": false, "error": { "code": "VALIDATION_ERROR", "message": "Field 'email' is invalid" } }
  ```

---

## 5. Environment Variables & Configuration

| Variable | Description | Required? | Exposed to Client? |
|---|---|---|---|
| `DATABASE_URL` | Connection string for database | Yes | ❌ NO (Server only) |
| `AUTH_SECRET` | Secret key for session/JWT encryption | Yes | ❌ NO (Server only) |
| `NEXT_PUBLIC_APP_URL` | Public origin URL | Yes | ✅ YES |
| `[REPLACE: SERVICE_API_KEY]` | External service credential | If needed | ❌ NO |

*Rule:* Never commit `.env` or `.env.local` to git. Provide `.env.example` with dummy values.

---

## 6. Deployment & Hosting Strategy
- **Target Platform:** `[REPLACE: e.g. Vercel / Netlify / Render / Docker]`
- **Build Command:** `npm run build`
- **Start Command:** `npm start`
- **Database Migrations:** Executed during build or via automated release step (e.g. `npx prisma migrate deploy`).
