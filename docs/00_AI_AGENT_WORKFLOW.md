# 00: AI Agent Workflow

> **FRAMEWORK STATUS: GENERIC STARTER TEMPLATE**  
> **OPERATIONAL MODE:** Currently in **Template Mode**. When the user provides a project idea, the AI Agent must execute the **Specification & Activation Loop (Section 0)** to replace generic placeholders across `docs/01` through `docs/07` with project-specific definitions before writing production code.

---

## 0. Project Initialization & Activation Protocol
When starting a new software project:
1. **Intake & Clarification:** Receive the user's project vision. Ask targeted questions regarding primary target users, MVP feature boundaries, preferred stack, and styling preferences.
2. **Populate Source of Truth:** Update the placeholder sections in `docs/`:
   - `01_PRD_AND_PRODUCT_SCOPE.md` (Product goals, user personas, MVP features, non-goals)
   - `02_TECHNICAL_ARCHITECTURE.md` (Concrete stack, directory layout, APIs, env variables)
   - `03_DATA_MODELS_AND_SCHEMA.md` (Database tables, entities, fields, relationships)
   - `04_UI_UX_AND_DESIGN_SYSTEM.md` (Visual theme, colors, typography, components)
   - `06_IMPLEMENTATION_ROADMAP.md` (Phased task breakdown with checkboxes `[ ]`)
3. **User Approval Gate:** Present the populated roadmap and architecture for user confirmation.
4. **Transition to Active Mode:** Switch header to `[STATUS: ACTIVE PROJECT - <Name>]`.
5. **Execution:** Begin Phase 1, Task 1 strictly following the One-Task Rule.

---

## 1. Core Operating Principles

### 1.1 Inspect Before Acting
Before touching code:
1. Inspect relevant project files, configs, and dependencies.
2. Understand surrounding implementation and existing patterns.
3. Identify existing utilities or components that can be reused.
4. Never guess file paths, function names, export names, schema fields, or dependencies.
*If the answer can be found in the workspace, inspect it.*

### 1.2 Do Not Invent
Never invent:
- APIs, external endpoints, or payload schemas
- Libraries or npm packages
- Database columns or tables
- Requirements or business rules not specified in `docs/`
- Test results or build passes

### 1.3 Follow Existing Architecture
- Always respect patterns established in `02_TECHNICAL_ARCHITECTURE.md`.
- Prefer existing project conventions over third-party alternatives.
- Avoid unnecessary abstractions or premature optimization.

### 1.4 Preserve Existing Functionality
- Modify only what is strictly required for the current task.
- Never delete or alter unrelated features or UI flows.
- Preserve existing APIs and interfaces unless the roadmap specifically requires an update.

---

## 2. Documentation Map & Precedence

```
00_AI_AGENT_WORKFLOW.md          # Agent lifecycle & behavior
01_PRD_AND_PRODUCT_SCOPE.md      # Product goals & scope boundaries
02_TECHNICAL_ARCHITECTURE.md     # Stack, system design & APIs
03_DATA_MODELS_AND_SCHEMA.md     # Entities, tables & constraints
04_UI_UX_AND_DESIGN_SYSTEM.md    # Design system, tokens & UI rules
05_CODING_RULES_AND_GUARDRAILS.md# Anti-hallucination & safety rules
06_IMPLEMENTATION_ROADMAP.md     # Task order & milestone gates
07_QUALITY_SECURITY_AND_REVIEW.md# QA, security & release checklist
```

**Precedence Order:**  
`GEMINI.md` > `Vibe Coding Master Pack.md` > `01_PRD` > `02_ARCHITECTURE` > `03_SCHEMA` > `04_UI_UX` > `05_GUARDRAILS` > `06_ROADMAP` > `07_QUALITY`

---

## 3. Required Execution Loop (Per Task)

```
Understand ──► Inspect ──► Plan ──► Implement ──► Test ──► Verify ──► Report
```

1. **Understand:** Identify user requirements, affected modules, and constraints.
2. **Inspect:** Read relevant files, check dependencies in `package.json`, inspect schemas.
3. **Plan:** Outline minimal surgical changes and verification steps.
4. **Implement:** Write production-grade code without TODOs, fake stubs, or shortcuts.
5. **Test & Verify:** Run type checking, linting, tests, or manual UI verification.
6. **Report:** Provide concise summary of changes, verified proofs, and update `06_IMPLEMENTATION_ROADMAP.md`.

---

## 4. Implementation Guardrails

- **One-Task Rule:** Complete, verify, and document one atomic task before proceeding.
- **No Incomplete Code:** Never leave `// TODO`, fake mock responses, or stubbed methods.
- **Error Handling:** Intentionally handle edge cases, empty states, and errors.
- **Security:** Never expose secrets, hardcode API keys, or trust unvalidated user inputs.
- **Windows PowerShell:** Use PowerShell-compatible syntax for all commands.

---

## 5. Definition of Done
A task is marked complete `[x]` ONLY when:
- Code is fully implemented (no placeholders or stubs).
- Relevant tests, builds, or visual checks pass without errors.
- Existing functionality is verified intact.
- Relevant documentation in `docs/` is updated if decisions evolved.