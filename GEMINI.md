# ANTIGRAVITY AND GEMINI WORKSPACE DIRECTIVES

> **FRAMEWORK STATUS: GENERIC STARTER PACK (TEMPLATE MODE)**  
> **CURRENT STATE:** No software is currently being implemented. This workspace holds the master blueprint and behavioral guardrails for AI-assisted development.  
> **ACTIVATION RULE:** When the user provides a project idea, the AI coding agent must execute the **Project Onboarding & Activation Protocol (Section 0)** to replace all placeholder documents in `docs/` with concrete project specifications before any production code is written.

---

## 0. PROJECT ONBOARDING & ACTIVATION PROTOCOL
When the user introduces a new project idea or software requirements:
1. **Interactive Alignment:** Ask focused clarifying questions (or confirm understanding) regarding target users, MVP features, preferred tech stack, and design preferences.
2. **Populate Source of Truth Docs:** Replace the generic placeholders across `docs/` with project-specific details:
   - `docs/01_PRD_AND_PRODUCT_SCOPE.md` → Goals, user stories, MVP scope, and non-goals.
   - `docs/02_TECHNICAL_ARCHITECTURE.md` → Frameworks, folder structure, API conventions, and environment variables.
   - `docs/03_DATA_MODELS_AND_SCHEMA.md` → Database tables, fields, constraints, and relationships.
   - `docs/04_UI_UX_AND_DESIGN_SYSTEM.md` → Palette, typography, layout hierarchy, and component rules.
   - `docs/06_IMPLEMENTATION_ROADMAP.md` → Phased task breakdown with checkboxes `[ ]` and verification methods.
3. **User Approval:** Present the summary to the user for confirmation.
4. **Switch State:** Update the status header in `GEMINI.md` and `docs/` to `[STATUS: ACTIVE PROJECT - <Project Name>]`.
5. **Execution:** Begin Phase 1, Task 1 strictly following the One-Task Rule.

---

## 1. CORE OPERATING PRINCIPLES
Always:
- **Inspect before assuming:** Always check existing files, configs, and dependencies before writing code.
- **Read documentation first:** Consult the corresponding `docs/` document before implementing any layer.
- **Follow approved architecture:** Do not deviate from the tech stack and patterns approved in `docs/`.
- **Make atomic, correct changes:** Make the smallest appropriate change; do not perform unrelated refactoring.
- **Preserve existing functionality:** Never delete or break working features unless explicitly instructed.
- **Verify before reporting:** Always execute tests, builds, or visual verification before marking a task complete.
- **Keep it simple:** Prefer standard, maintainable code over clever or bloated abstractions.

---

## 2. DOCUMENTATION MAP (SINGLE SOURCE OF TRUTH)
Each document owns a distinct responsibility:
- **`00_AI_AGENT_WORKFLOW.md`**: Agent execution loop (`Inspect → Understand → Plan → Implement → Verify → Report`).
- **`01_PRD_AND_PRODUCT_SCOPE.md`**: Product goals, user personas, MVP features, and anti-scope.
- **`02_TECHNICAL_ARCHITECTURE.md`**: Tech stack, directory layout, APIs, integrations, and deployment.
- **`03_DATA_MODELS_AND_SCHEMA.md`**: Database entities, relationships, constraints, and migrations.
- **`04_UI_UX_AND_DESIGN_SYSTEM.md`**: Design tokens, layout hierarchy, accessibility, and anti-AI design rules.
- **`05_CODING_RULES_AND_GUARDRAILS.md`**: Coding standards, error handling, anti-hallucination rules, and safety.
- **`06_IMPLEMENTATION_ROADMAP.md`**: Phased execution steps, dependencies, checklist, and definition of done.
- **`07_QUALITY_SECURITY_AND_REVIEW.md`**: Testing gates, security audit, accessibility, and release checklist.

---

## 3. BEFORE IMPLEMENTATION
Before starting any significant task or feature:
1. Read `00_AI_AGENT_WORKFLOW.md`.
2. Read the specific document governing the task (e.g., `03` for database, `04` for UI).
3. Review coding guardrails in `05_CODING_RULES_AND_GUARDRAILS.md`.
4. Inspect the existing codebase to verify assumptions.
5. If requirements or architecture are ambiguous, **do not guess**—ask the user for clarification.

---

## 4. DURING IMPLEMENTATION (ONE-TASK RULE)
- Strictly execute one roadmap task at a time.
- Standard task cycle: **Inspect → Understand → Plan → Implement → Verify → Report**.
- Never silently skip roadmap tasks or batch multiple tasks without verification.
- Never mark unverified code as complete.

---

## 5. ANTI-HALLUCINATION GUARDRAILS
Never invent:
- Files, directory structures, or exports.
- Functions, classes, or parameters.
- API endpoints or payload shapes.
- Database tables or schema fields.
- External libraries or package versions.
- Test execution results or build statuses.

*Rule:* If the information exists in the project, inspect it. If it does not exist, ask or decide explicitly before writing code.

---

## 6. CODE DISCIPLINE & MUTATION RULES
- Inspect the target file and surrounding context before modifying.
- Make targeted, surgical edits (`replace_file_content` / `multi_replace_file_content`).
- Do not overwrite entire files for small changes.
- Do not perform unsolicited refactoring or stylistic cleanups on untouched code.

---

## 7. DEPENDENCY RULES
- Check `package.json` before importing any package.
- Confirm the dependency is installed.
- Do not add packages if an existing built-in or installed tool can solve the problem.
- Never install packages without explicit architectural justification.

---

## 8. NO INCOMPLETE OR PLACEHOLDER CODE
The agent must never leave:
- `// TODO: Implement later`
- Stubbed functions returning fake data in production flows.
- Truncated files or placeholder components.
- Mock API responses when real backend logic is required.
*If blocked or missing credentials/APIs, stop and explicitly report the blocker.*

---

## 9. DESIGN RULES & ANTI-AI TROPES
Follow `docs/04_UI_UX_AND_DESIGN_SYSTEM.md`.  
**Avoid generic AI aesthetic clichés:**
- Neon green accents and glowing borders/badges.
- Monospace font for non-code text.
- Rocket 🚀 or lightning ⚡ emojis in headings.
- Eyebrow chips above every title.
- Heavy icon-only navigation and excessive Lucide icon clutter.
- Useless cards inside cards and bloated glassmorphism.
**Favor:** Clean visual hierarchy, intentional typography, purposeful spacing, and accessible contrast.

---

## 10. PLATFORM & TOOLING (WINDOWS POWERSHELL)
- The local environment is **Windows PowerShell**.
- Use Windows-compatible command syntax (avoid bash-only flags or Linux-specific utilities like `grep -P`, `rm -rf`, `export`).
- Use npm scripts configured in `package.json` whenever available.

---

## 11. QUALITY, VERIFICATION & SECURITY
Before declaring any task or phase complete:
- Run type-checking (`npm run type-check` or `tsc --noEmit` if configured).
- Run linting (`npm run lint` if configured).
- Run unit/integration tests (`npm test` if configured).
- Verify the affected user journey or run the dev server to confirm UI responsiveness.
- Ensure no sensitive credentials, secrets, or API keys are exposed on the client.

---

## 12. DOCUMENTATION SYNCHRONIZATION
When an architectural, data, or product decision changes during development:
1. Update the corresponding document in `docs/` immediately.
2. Ensure code and documentation stay synchronized. Never allow silent drift.

---

## 13. CONFLICT RESOLUTION
When documents appear to conflict:
1. Identify which document owns the decision (e.g., `01` owns product scope, `02` owns architecture, `03` owns schema).
2. If conflict cannot be safely resolved from existing code, ask the user. Security, correctness, and data integrity always take precedence over shortcuts.

---

## 14. FINAL SUMMARY
**Inspect → Understand → Plan → Implement → Verify → Report.**  
Build simple, secure, verifiable, and maintainable software.
