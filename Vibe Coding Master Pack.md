# VIBE CODING MASTER PACK
### AI-First Software Engineering Framework (Optimized for Google Antigravity & Gemini)

> **FRAMEWORK STATUS: GENERIC STARTER TEMPLATE**  
> **PURPOSE:** This pack provides a battle-tested, structured development system for building robust software with an AI coding agent.  
> **HOW IT WORKS:** All files inside `docs/` currently contain structural templates and operational guardrails. When you bring your software idea, the AI coding agent will collaborate with you to replace the template placeholders with the actual product specifications (PRD, technical architecture, database schemas, design tokens, and implementation roadmap) before coding begins.

---

## 1. FRAMEWORK ARCHITECTURE & DOCUMENT MAP

```
Project Vibecode/
├── GEMINI.md                          # Workspace entry point & operational directives
├── Vibe Coding Master Pack.md          # Framework guide & quick reference
└── docs/
    ├── 00_AI_AGENT_WORKFLOW.md        # AI agent execution loop & behavior rules
    ├── 01_PRD_AND_PRODUCT_SCOPE.md    # Product requirements, personas, scope, non-goals
    ├── 02_TECHNICAL_ARCHITECTURE.md   # Tech stack, directory structure, APIs, deployment
    ├── 03_DATA_MODELS_AND_SCHEMA.md   # Database tables, relationships, constraints, migrations
    ├── 04_UI_UX_AND_DESIGN_SYSTEM.md  # Design tokens, layout, accessibility, anti-AI tropes
    ├── 05_CODING_RULES_AND_GUARDRAILS.md # Anti-hallucination, error handling, code discipline
    ├── 06_IMPLEMENTATION_ROADMAP.md   # Phased step-by-step checklist & task gates
    └── 07_QUALITY_SECURITY_AND_REVIEW.md # QA gates, security audits, pre-release checklist
```

### Document Ownership & Responsibilities
- **`00`** controls **how the AI agent operates**.
- **`01`** controls **what product is being built** (scope & requirements).
- **`02`** controls **how the system is architected** (tech choices & structure).
- **`03`** controls **how data is stored & modeled** (entities & integrity).
- **`04`** controls **how the UI looks and interacts** (visual system).
- **`05`** controls **how code is written safely** (guardrails & error handling).
- **`06`** controls **the sequence of implementation** (roadmap & tasks).
- **`07`** controls **verification, testing, and security gates**.

---

## 2. HOW TO ACTIVATE FOR A NEW PROJECT

When you are ready to build a new software project:

### Step 1: Provide Your Project Idea
Give the agent your high-level concept:
> *"I want to build [App Name / Idea Description]. Let's activate the Vibe Coding Master Pack."*

### Step 2: Agent populates the Source of Truth Docs
The agent inspects the workspace, asks any clarifying questions, and fills out:
- `docs/01_PRD_AND_PRODUCT_SCOPE.md` with your user stories, core features, and MVP boundaries.
- `docs/02_TECHNICAL_ARCHITECTURE.md` with the confirmed tech stack (e.g. Next.js, Vite, Node, etc.).
- `docs/03_DATA_MODELS_AND_SCHEMA.md` with concrete schemas and relations.
- `docs/04_UI_UX_AND_DESIGN_SYSTEM.md` with theme, colors, and layout rules.
- `docs/06_IMPLEMENTATION_ROADMAP.md` with actionable phases and tasks (`[ ] Task 1.1...`).

### Step 3: Review & Confirm
Review the generated specifications. Once aligned, confirm with:
> *"Approved. Proceed with Phase 1 Task 1."*

### Step 4: Phased Implementation (The One-Task Rule)
The agent executes tasks one by one from `06_IMPLEMENTATION_ROADMAP.md`:
1. **Inspect** relevant files.
2. **Plan** the atomic change.
3. **Implement** without stubs or fake code.
4. **Verify** (type check, build, tests, or UI test).
5. **Report** verified progress and move to the next task.

---

## 3. CORE AI AGENT GUARDRAILS SUMMARY

| Rule | Description |
|---|---|
| **Inspect First** | Never guess paths, exports, schemas, or dependencies. Always check files first. |
| **No Incomplete Code** | Never leave `// TODO`, mock responses, or stubbed components. |
| **No Invented Packages** | Only use dependencies present in `package.json` or explicitly approved. |
| **One Task at a Time** | Never batch multiple roadmap phases together without verification. |
| **Verify Before Done** | Never mark a task complete without executing builds, tests, or manual checks. |
| **Clean Design** | Avoid generic AI slop (no neon green glow, no rocket emojis, no unnecessary cards). |
| **Sync Docs** | Keep `docs/` updated whenever decisions or architectures evolve. |

---

## 4. LIFECYCLE SUMMARY
```
[ User Idea ] 
      │
      ▼
[ Docs 01-07 Populated & Approved ] 
      │
      ▼
[ Phase 1: Foundation & Setup ] ──► (Verify)
      │
      ▼
[ Phase 2: Core Data & Backend ] ──► (Verify)
      │
      ▼
[ Phase 3: Frontend & Features ] ──► (Verify)
      │
      ▼
[ Phase 4: QA & Security Audit ] ──► (Verify)
      │
      ▼
[ Production Release ]
```
