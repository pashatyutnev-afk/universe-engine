# KB — SCOPE → MODULE LOADING RULES (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/74__KB_SCOPE_TO_MODULE_LOADING_RULES.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: RULE
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.RULE.SCOPE_MODULE_LOAD.074
OWNER: SYSTEM
ROLE: Defines deterministic rules for loading KB modules after scopes are selected: minimal set, priority order, module type preferences, and overload prevention. Ensures entities don’t load “everything” and remain efficient and consistent.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created scope→module loading rules with priority order and minimal set limits."
- REASON: "Scope selection is not enough; entities need rules to load the right modules (not too many) in a consistent order."
- IMPACT: "More efficient runs, less contradiction, better trace clarity."
- CHANGE_ID: UE.CHG.2026-01-14.KB.RULE.074

---

## 0) PURPOSE (KB)
After selecting scopes, entities must load modules deterministically:
- minimal set sufficient for the task
- consistent module type priority order
- avoid loading too many modules (overload)

---

## 1) ABSOLUTE RULES
R1 — Governance first
- Always load governance baseline modules before any domain modules.

R2 — ACTIVE-first
- Prefer ACTIVE modules when available.

R3 — Minimal set
- Load the smallest module set that enables PASS-quality output.

R4 — Master index navigation only
- Modules are opened via the master index (RAW-only navigation).

---

## 2) MODULE TYPE PRIORITY ORDER
When selecting what to load inside a scope, prefer:
1) POLICY / RULE / STANDARD (constraints, definitions, boundaries)
2) MAP (selection/decision tables)
3) CHECKLIST / GATE (validation, pass/fail)
4) PLAYBOOK / PROTOCOL (step-by-step execution)
5) TOPIC (domain knowledge / craft)
6) TEMPLATE (copy artifacts)
7) EXAMPLE (good/bad exemplars)

Reason:
- constraints first, then decision maps, then validation, then execution guidance, then knowledge enrichment.

---

## 3) LOADING LIMITS (DEFAULT)
Default maximum modules per run:
- Governance: 2–5
- Domain scope: 2–6
- Extra scopes (production/marketing): 1–3 each
Total typical: 6–12 modules

If more needed:
- declare reason and keep trace minimal (drivers only).

---

## 4) DETERMINISTIC LOADING SEQUENCE
Step A: Load governance minimum set (required).
Step B: For each selected scope:
- Load 1–2 constraint modules (policy/standard)
- Load 1 map/checklist if available
- Load 1–3 topic/playbook modules relevant to task
- Load templates as needed for output artifacts
Step C: Run gates/checklists for validation.
Step D: Emit trace.

---

## 5) OVERLOAD PREVENTION
If too many modules are available:
- choose the most specific modules:
  - domain-specific over generic
  - task-specific over broad topic
  - newest ACTIVE canon over older versions
- avoid loading overlapping modules that duplicate meaning
If conflict suspected:
- trigger contradiction protocol or reduce set to a single canon source.

---

## 6) FALLBACK RULES
If no module exists for a selected scope:
- trigger gap handling protocol
- choose STOP or INGEST, not invention

---

## 7) HARD FAIL CONDITIONS
FAIL IF:
- governance omitted
- more than 20 modules loaded without explicit justification
- module type priority is ignored and topics are loaded before constraints/gates
- missing modules are “filled” by invention instead of gap protocol

---

## 8) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.README.SCOPE_MAPS.073 | WHY: explains how scopes are selected
- XREF: UE.KB.PLAYBOOK.NAV_QUICKSTART.062 | WHY: run sequence for KB usage
- XREF: UE.KB.PROC.GAP_HANDLING.066 | WHY: missing modules trigger gap handling
- XREF: UE.KB.PROC.CONTRADICTIONS.065 | WHY: conflicts trigger contradiction handling
- XREF: UE.KB.STD.RUN_TRACE_MIN.067 | WHY: trace lists loaded modules

--- END.
