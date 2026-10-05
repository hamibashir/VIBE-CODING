# 07: Quality Assurance, Security Audit & Release Gate

> **DOCUMENT STATUS: PERMANENT QUALITY CRITERIA**  
> *No feature, milestone, or release is marked complete without satisfying the verification criteria in this document.*

---

## 1. Quality Gate Principles
- **Verify Before Sign-Off:** Never claim a feature is complete based only on visual inspection or writing code. Run tests, run type checking, or perform manual UI journey tests.
- **Failures Block Completion:** If a security or correctness check fails, the task remains incomplete until fixed and verified.
- **Use Project-Configured Commands:** Always inspect `package.json` and use the actual scripts (e.g. `npm test`, `npm run lint`, `npm run build`). Never invent command names.

---

## 2. Testing Pyramid & Verification Focus

| Test Layer | Scope | Key Focus |
|---|---|---|
| **Unit Tests** | Utilities, schemas, pure functions | Zod schemas, calculations, date helpers, sanitizers |
| **Integration Tests** | API routes & DB interactions | Auth checks, DB transactions, CRUD boundaries, error responses |
| **End-to-End (E2E)** | Critical user journeys | Signup/login, core product workflow, creation & deletion |
| **Manual / Visual** | Browser viewport & interaction | Responsive design (375px to 1440px), empty states, focus rings |

---

## 3. Pre-Flight Security Audit Checklist

### 3.1 Access Control & Authorization
- [ ] Server-side authentication check on every protected route / server action.
- [ ] Resource ownership verified (`WHERE user_id = current_user.id`).
- [ ] No client-only route protection (client redirects alone are not security).

### 3.2 Secrets & Credential Management
- [ ] No hardcoded passwords, tokens, API keys, or JWT secrets in code.
- [ ] All sensitive keys are loaded via environment variables (`process.env`).
- [ ] `.env` is included in `.gitignore`; `.env.example` contains dummy values only.
- [ ] No server environment variables leaked through `NEXT_PUBLIC_` prefixes.

### 3.3 Data Injection & Input Validation
- [ ] All external input validated through Zod or strict typing before DB operations.
- [ ] No raw SQL string concatenation (ORM parameterized queries only).
- [ ] User-generated content properly escaped to prevent Cross-Site Scripting (XSS).

---

## 4. UI, Accessibility & Performance Checks
- [ ] **Contrast:** Minimum 4.5:1 text-to-background contrast ratio.
- [ ] **Keyboard Nav:** Complete primary flow using only `Tab`, `Enter`, `Space`, `Esc`.
- [ ] **Responsive:** No layout breakage or horizontal scrolling on mobile (375px) or tablet (768px).
- [ ] **States:** Verified 4 states for all dynamic screens: `Loading`, `Empty`, `Success`, `Error`.

---

## 5. Production Release Gate
Before declaring the application ready for deployment or handoff:
1. `npm run build` runs with zero errors.
2. `npm run type-check` (or `tsc --noEmit`) passes cleanly.
3. `npm run lint` passes without unresolved errors.
4. Core user journey verified end-to-end without unhandled console errors.
5. All P0 roadmap tasks in `docs/06_IMPLEMENTATION_ROADMAP.md` are checked `[x]`.
