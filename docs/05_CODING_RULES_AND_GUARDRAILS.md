# 05: Coding Rules, Error Handling & Anti-Hallucination Guardrails

> **DOCUMENT STATUS: PERMANENT OPERATING GUARDRAILS**  
> *These rules apply unconditionally across all phases of software design and implementation. The AI Agent must follow every rule without exception.*

---

## 1. Anti-Hallucination Directives
- **Inspect Before Edit:** Always inspect the actual file before modifying it. Never write replacements from memory or assume what lines exist.
- **Verify Before Assuming:** Check `package.json` for installed packages, check directory trees for actual filenames, and check schema files for field names.
- **No Invented Dependencies:** Never import a third-party package unless confirmed installed in `package.json`.
- **No Invented APIs:** Never invent query parameters, endpoints, or response payloads. Follow explicit contracts defined in `02_TECHNICAL_ARCHITECTURE.md`.
- **No Invented Results:** Never claim a test passed, a build succeeded, or a route worked unless the command was actually executed and returned exit code 0.

---

## 2. Incomplete Code Is Forbidden
The AI Agent must NEVER produce:
- `// TODO: Implement this later`
- Empty function bodies or truncated logic
- Fake mock return data in place of real backend services
- Stubbed components with placeholder `<div>Coming Soon</div>`
- Hardcoded success states bypassing real error paths

*Rule:* If an implementation cannot be completed due to missing configuration or blocked dependencies, stop immediately and report the specific blocker to the user.

---

## 3. Code Change Discipline & Atomic Edits
- **Smallest Correct Change:** Modify only the exact lines necessary to satisfy the current task.
- **No Unrelated Refactoring:** Do not reformat untouched functions, reorder unrelated imports, or rewrite working files simply for style.
- **Surgical Edits:** Use localized text replacement (`replace_file_content` / `multi_replace_file_content`). Never overwrite an entire 500-line file to change 3 lines.
- **Preserve Existing Behavior:** Ensure existing features, exports, and routes continue functioning without regression.

---

## 4. TypeScript & Typing Standards
- **Strict Mode:** Always adhere to strict TypeScript settings.
- **Ban `any`:** Use explicit interfaces or types. When type is unknown at runtime (e.g. external API response), use `unknown` and validate via Zod.
- **Single Source of Truth:** Reuse existing type definitions from `types/` or ORM-generated models. Do not create competing duplicate interfaces.

---

## 5. Defensive Error Handling & Resilience
- **Explicit Catching:** Never leave catch blocks empty (`catch (e) {}`). Always log the error or return a structured error response.
- **Structured Error Envelope:**
  ```typescript
  return { success: false, error: { code: 'NOT_FOUND', message: 'Resource not found' } };
  ```
- **Boundary Validation:** Validate all incoming HTTP data, form submissions, and webhook payloads using Zod before processing.
- **Safe User Messages:** Never expose internal database errors, SQL queries, or stack traces in user-facing UI or API error responses.

---

## 6. Security & Credential Protection
- **No Hardcoded Secrets:** Passwords, API tokens, webhook secrets, and private keys must only be loaded via `process.env`.
- **Client/Server Boundary:** Never import server-only database clients or secrets into client-rendered UI components.
- **SQL / Injection Defense:** Use parameterized queries or ORMs (Prisma, Drizzle) exclusively. Never concatenate raw SQL strings with user input.
- **Authorization Verification:** Always verify user session and ownership (`record.user_id === session.user.id`) before allowing mutations.

---

## 7. Windows PowerShell Platform Rules
- Commands must be compatible with **Windows PowerShell 5.1 / 7+**.
- **No Linux-only commands:** Avoid `cat` (for file writing), `export VAR=val` (use `$env:VAR='val'`), `rm -rf` (use `Remove-Item -Recurse -Force`), or bash chaining with `&&` if running in older PowerShell (use sequential commands or verify PowerShell 7+).
- **Use npm scripts:** Prefer running `npm run <script>` defined in `package.json`.
