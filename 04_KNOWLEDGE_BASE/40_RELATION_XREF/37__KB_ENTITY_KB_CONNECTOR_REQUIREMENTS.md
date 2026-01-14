# KB — ENTITY ↔ KB CONNECTOR REQUIREMENTS (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/37__KB_ENTITY_KB_CONNECTOR_REQUIREMENTS.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.STD.ENTITY_KB_CONNECTOR.037
OWNER: SYSTEM
ROLE: Defines the minimum required “connector” interface between any entity and the Knowledge Base: required KB scopes, required governance baseline, how an entity declares KB dependencies, and mandatory trace output.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Defined canonical entity↔KB connector requirements: scope declaration + governance baseline + trace."
- REASON: "Entities must know what knowledge to load; connectors make KB consumption deterministic and auditable."
- IMPACT: "Consistent KB intake for every entity; reduces hallucination and improves quality."
- CHANGE_ID: UE.CHG.2026-01-14.KB.STD.037

---

## 0) PURPOSE (KB)
A connector is the contract:
- what KB knowledge an entity requires
- how it selects scopes/modules deterministically
- how it outputs trace for audit

This standard is shared across all entity classes.

---

## 1) ABSOLUTE RULES
R1 — Governance baseline required
- Every connector MUST include KB_SCOPE.GOVERNANCE minimum set requirement.

R2 — Deterministic scope selection
- Entity must select scopes using canonical scope maps (task/entity scope maps), not ad-hoc browsing.

R3 — UID-only references
- Any references to KB modules in connector declarations must be UID-only (no URL/PATH).

R4 — Trace is mandatory
- Every run must output KB_SOURCES trace of what was used.

---

## 2) CONNECTOR DECLARATION (MINIMUM FIELDS)
Each entity must declare:

ENTITY_KB_CONNECTOR:
- ENTITY_UID: <entity UID>
- ENTITY_CLASS: SPC | ENG | ORC | CTL | VAL | QA | XREF
- REQUIRED_SCOPES:
  - KB_SCOPE.GOVERNANCE
  - KB_SCOPE.TOPICS.<DOMAIN> (one or more, depending on entity)
- OPTIONAL_SCOPES:
  - <list>
- REQUIRED_MODULE_UIDS (optional but recommended):
  - <governance dict/policies or core domain modules>
- SELECTION_MAP_UIDS:
  - UE.KB.MAP.TASK_SCOPE.001 (if task-based selection shows up)
  - UE.KB.MAP.ENTITY_SCOPE.002 (entity-based selection)
- DEFAULT_TRACE_MODE:
  - KB_SOURCES required: YES
  - MEMORY_REUSE allowed: YES/NO
  - STATUS_ALLOWED: ACTIVE_ONLY | ACTIVE_PLUS_DRAFT (per access policy)

Notes:
- REQUIRED_MODULE_UIDS should stay small; prefer scopes + selection maps.

---

## 3) CONNECTOR USAGE (RUN BEHAVIOR)
Run behavior must follow:
Step 1: Load governance minimum set.  
Step 2: Choose scopes using maps (task or entity).  
Step 3: Open required modules via KB master index (RAW-only) or trusted memory reuse.  
Step 4: Apply methods.  
Step 5: Emit trace (KB_SOURCES).  

---

## 4) TRACE FORMAT (MANDATORY)
Every run must output:

KB_SOURCES:
- XREF: <KB_MODULE_UID> | WHY: <used for>
- XREF: <KB_MODULE_UID> | WHY: <used for>
MEMORY_REUSE: YES/NO
STATUS_USED: ACTIVE_ONLY | MIXED
WEB_LOOKUP_USED: YES/NO (if yes, include WEB_LOOKUP_NOTICE template)

---

## 5) VALIDATION RULES (PASS/FAIL)
PASS IF:
- governance baseline included
- scope selection uses canonical maps
- connector does not embed URLs/PATH
- trace format is present and complete
- access control policy is respected (ACTIVE-first, no deprecated authority)

FAIL IF:
- entity runs without governance baseline
- scope selection is ad-hoc or random
- connector uses URL/PATH as references
- trace missing or incomplete
- deprecated modules used as authority

---

## 6) HARD FAIL CONDITIONS
FAIL IF:
- REQUIRED_SCOPES missing KB_SCOPE.GOVERNANCE
- SELECTION_MAP_UIDS missing when needed for the entity
- trace omitted
- entity uses non-registered module as operational knowledge

---

## 7) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.MAP.TASK_SCOPE.001 | WHY: deterministic task→scope selection
- XREF: UE.KB.MAP.ENTITY_SCOPE.002 | WHY: deterministic entity→scope selection
- XREF: UE.KB.STD.SCOPE.GOVERNANCE_MIN.009 | WHY: governance minimum set
- XREF: UE.KB.POL.ENTITY_ACCESS.031 | WHY: status-based access control for entities
- XREF: UE.KB.DICT.XREF_RULES.005 | WHY: uid-only reference rules
- XREF: UE.KB.TPL.WEB_LOOKUP_NOTICE.035 | WHY: web lookup disclosure template

--- END.
