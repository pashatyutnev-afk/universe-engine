# KB — NAVIGATION QUICKSTART (FOR ENTITIES) (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/62__KB_NAVIGATION_QUICKSTART.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: PLAYBOOK
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.PLAYBOOK.NAV_QUICKSTART.062
OWNER: SYSTEM
ROLE: Fast operational guide for entities on how to use the Knowledge Base deterministically: governance baseline first, scope selection via maps, open modules via master index (RAW-only), and emit trace. No RAW links inside; points to canonical UIDs.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created KB navigation quickstart playbook for entity runs."
- REASON: "Entities must follow a consistent KB usage sequence; quickstart reduces errors and drift."
- IMPACT: "Faster onboarding and fewer navigation/trace violations."
- CHANGE_ID: UE.CHG.2026-01-14.KB.PLAYBOOK.062

---

## 0) PURPOSE (KB)
Teach the minimal deterministic sequence:
- governance first
- maps choose scope
- master index opens modules (RAW-only)
- no fantasy
- trace mandatory

This is a quickstart, not a law file.

---

## 1) REQUIRED INPUTS
- Task intent (what are we doing?)
- Entity class + primary domain
- Governance minimum set UID
- Selection map UIDs

---

## 2) QUICKSTART FLOW (DETERMINISTIC)
### Step 1 — Load governance baseline
- Load governance minimum set first.
- If governance baseline missing: STOP or trigger gap fill.

### Step 2 — Select scope using maps (not intuition)
- Use entity→scope map first.
- If task classification is needed, use task→scope map.

Output:
- REQUIRED_SCOPES
- OPTIONAL_SCOPES

### Step 3 — Open KB modules via master index
Rule:
- Master index is the only navigation mechanism to open KB modules (RAW-only).
- Do not navigate by PATH in your head.

Open:
- 1–3 domain topics for the task
- required checklists/gates
- optional companion modules if needed

### Step 4 — Apply methods and templates
- Follow procedures
- Use copy templates/cards
- Run QA gates

### Step 5 — Emit trace (mandatory)
Output:
KB_SOURCES:
- XREF: <uid> | WHY: <used for>
MEMORY_REUSE: YES/NO
STATUS_USED: ACTIVE_ONLY | MIXED
WEB_LOOKUP_USED: YES/NO

If web lookup used:
- include WEB_LOOKUP_NOTICE.

---

## 3) DO / DO NOT
DO:
- prefer ACTIVE modules
- stop if missing governance or missing required inputs
- label hypothesis vs fact

DO NOT:
- invent facts
- treat browsing as operational truth without ingestion
- embed URLs in XREF blocks

---

## 4) COMMON FAILS (AND FIXES)
FAIL: started domain work without governance
- FIX: load governance minimum set first

FAIL: used deprecated module as authority
- FIX: follow pointer to replacement UID

FAIL: missing trace
- FIX: add KB_SOURCES + memory reuse markers

FAIL: ad-hoc web browsing
- FIX: ingest into KB modules + source records

---

## 5) HARD FAIL CONDITIONS
FAIL IF:
- governance baseline not loaded
- no trace output
- deprecated authority used
- invented facts claimed as sourced truth
- scope selection skipped and replaced by intuition

---

## 6) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.SCOPE.GOVERNANCE_MIN.009 | WHY: governance baseline required
- XREF: UE.KB.MAP.ENTITY_SCOPE.002 | WHY: entity→scope selection
- XREF: UE.KB.MAP.TASK_SCOPE.001 | WHY: task→scope selection (if needed)
- XREF: UE.KB.STD.ENTITY_KB_CONNECTOR.037 | WHY: connector requirements
- XREF: UE.KB.TPL.WEB_LOOKUP_NOTICE.035 | WHY: web lookup disclosure template
- XREF: UE.KB.POL.ENTITY_ACCESS.031 | WHY: access control (ACTIVE-first)

--- END.
