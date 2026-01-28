# KB — ENTITY ACCESS CONTROL POLICY (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/31__KB_ENTITY_ACCESS_CONTROL_POLICY.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: POLICY
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.POL.ENTITY_ACCESS.031
OWNER: SYSTEM
ROLE: Define deterministic access rules for entities consuming KB modules: which STATUS levels are allowed for which entity classes, how to treat DEPRECATED modules, how to handle external/world sources, and required trace behavior.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Established entity access control for KB consumption (status-based permissions and hard fail rules)."
- REASON: "Without access control, entities may use unstable drafts or deprecated modules as authority, causing drift and inconsistent outputs."
- IMPACT: "Predictable KB consumption: ACTIVE-first, controlled DRAFT usage, DEPRECATED blocked, world-sources ingested before operational use."
- CHANGE_ID: UE.CHG.2026-01-14.KB.POL.031

---

## 0) PURPOSE (KB)
Define which KB modules entities are allowed to use based on:
- entity class (SPC/ENG/ORC/CTL/VAL/QA/XREF)
- module status (DRAFT/ACTIVE/DEPRECATED)
- risk context (high-risk vs normal)

This policy complements status/lock and world knowledge policies.

---

## 1) ABSOLUTE RULES
R1 — ACTIVE-first
- If an ACTIVE module exists for a function, entities must use it instead of DRAFT.

R2 — DEPRECATED is blocked for execution
- Entities must not execute procedures from DEPRECATED modules.
- DEPRECATED may be used only as a pointer to the replacement UID.

R3 — World knowledge is not operational by default
- External sources must be ingested into KB modules before repeated operational use.

R4 — Trace is mandatory
- Outputs must include KB_SOURCES with UIDs used and MEMORY_REUSE marker.

---

## 2) PERMISSION MATRIX (ENTITY × STATUS)
### SPC
- ACTIVE: allowed (default)
- DRAFT: allowed only if no ACTIVE equivalent exists OR explicitly requested; must declare DRAFT use in trace
- DEPRECATED: forbidden (pointer-only allowed)

### ENG
- ACTIVE: allowed (default)
- DRAFT: allowed in development runs only; prefer ACTIVE
- DEPRECATED: forbidden

### ORC
- ACTIVE: allowed (default)
- DRAFT: allowed only for pipeline experimentation; must declare
- DEPRECATED: forbidden

### CTL
- ACTIVE: allowed (default)
- DRAFT: discouraged; allowed only for temporary testing controls; must declare
- DEPRECATED: forbidden

### VAL
- ACTIVE: allowed (default)
- DRAFT: allowed if validating new drafts or when no ACTIVE exists; must declare
- DEPRECATED: forbidden

### QA
- ACTIVE: allowed (default)
- DRAFT: allowed for testing and audits; must declare
- DEPRECATED: forbidden

### XREF
- ACTIVE: allowed (default)
- DRAFT: allowed for mapping drafts; must declare
- DEPRECATED: allowed only as pointer resolution (to find replacement UID), not as authority

---

## 3) HIGH-RISK OVERRIDE
If task is high-risk (canon/governance change, system law, breaking changes):
- Only ACTIVE modules may be used as authority.
- DRAFT usage requires explicit stop-or-create decision:
  - create/upgrade module first, or stop.
- External web lookup must be converted into a KB module before it becomes guidance.

---

## 4) POINTER MODULE HANDLING
If a module is POINTER/ALIAS:
- Entities must follow CANON_TARGET_UID to the authoritative module.
- Pointer content must not be treated as a source of rules.

---

## 5) TRACE REQUIREMENTS (MANDATORY)
Every run that uses KB must emit:

KB_SOURCES:
- XREF: <UID> | WHY: ...
MEMORY_REUSE: YES/NO
STATUS_USED: ACTIVE_ONLY | MIXED (ACTIVE+DRAFT)

Rules:
- If any DRAFT is used → STATUS_USED must be MIXED.
- If any external lookup influenced output → must be declared (outside scope here; required by world-sources policy).

---

## 6) HARD FAIL CONDITIONS
FAIL IF:
- entity uses DEPRECATED module as authority (not pointer)
- entity uses DRAFT while ACTIVE equivalent exists (without explicit reason)
- entity produces output without KB_SOURCES trace
- pointer module contains procedures or is treated as authority
- external sources used as operational rules without KB ingestion

---

## 7) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.POL.STATUS_LOCK.029 | WHY: defines module statuses and lock semantics
- XREF: UE.KB.POL.WORLD_SOURCES.030 | WHY: governs external/world knowledge ingestion
- XREF: UE.KB.STD.DEPRECATION_POINTER.007 | WHY: defines deprecation and pointer-first behavior
- XREF: UE.KB.POL.POINTERS_ALIASES.028 | WHY: pointer/alias policy and constraints

--- END.
