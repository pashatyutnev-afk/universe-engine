# KB — TASK → KB SCOPE MAP (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: MAP
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.MAP.TASK_SCOPE.001
OWNER: SYSTEM
ROLE: Deterministic map that tells any entity which KB knowledge scope is REQUIRED vs OPTIONAL for a given task class (prevents “random browsing” and prevents hallucination)

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Introduced canonical TASK→KB scope selection map for all entities."
- REASON: "Entities need deterministic KB scope selection to ensure quality and prevent fantasy; KB must be executable and reproducible."
- IMPACT: "All entity workflows gain consistent KB intake; reduces drift; improves auditability."
- CHANGE_ID: UE.CHG.2026-01-14.KB.MAP.001

---

## 0) PURPOSE (KB)
This module defines a deterministic rule-map:
- classify the task
- select REQUIRED KB governance knowledge (always)
- select REQUIRED domain knowledge (by task class)
- select OPTIONAL deepening packs (only if needed)

This is a MAP, not an index. It must not contain RAW URLs or PATH navigation.
All navigation is performed via the KB master index (RAW-only) and via UID-only references.

---

## 1) ABSOLUTE RULES (NO-FANTASY)
1.1 NO-FANTASY (ABSOLUTE)
- If you have not opened a referenced knowledge source (via the KB master index RAW link), you MUST NOT invent or “fill gaps”.
- If you opened it before, you may reuse from memory, but MUST NOT distort.

1.2 KB GOVERNANCE FIRST (ABSOLUTE)
For any task, the entity MUST be aligned with KB governance:
- KB rules
- relation types
- XREF rules (UID-only)

1.3 UID-ONLY REFERENCES (ABSOLUTE)
- Inside KB modules, all references MUST be UID-only.
- No URLs. No PATHs. No “guess links”.

---

## 2) TASK CLASSIFICATION (STRICT ENUM)
Choose exactly one PRIMARY task class:

T0 — NAVIGATION / LOOKUP  
T1 — DOCUMENT AUTHORING (new doc / rewrite / standard / spec)  
T2 — CANON / GOVERNANCE CHANGE (indexes, laws, standards, registries, existence maps)  
T3 — ENTITY WORK (create/update entity definition, passport, role rules)  
T4 — PIPELINE / PROCESS DESIGN (gates, stages, orchestration flows)  
T5 — CONTENT PRODUCTION (story, scenes, lore, narrative assets)  
T6 — ANALYSIS / RESEARCH (comparative analysis, structured synthesis)  
T7 — IMPLEMENTATION (code/assets generation inside allowed scopes)

Optional SECONDARY flags (0..N):
- F1: HIGH_RISK (breaking change potential)
- F2: NEED_XREF (requires relation mapping)
- F3: NEED_TEMPLATE (must use canonical template)
- F4: NEED_GATES (quality gates required)

---

## 3) REQUIRED KB INTAKE (ALWAYS)
For any task class T0..T7, these are mandatory:

- UID: UE.KB.RULES.001  | WHY: KB minimum standard + governance baseline
- UID: UE.KB.DICT.REL_TYPES.001 | WHY: allowed relation vocabulary
- UID: UE.KB.DICT.XREF_RULES.001 | WHY: UID-only XREF rules (no URL/PATH)

If any of the above is missing/unavailable → STOP (KB governance missing).

---

## 4) SCOPE MATRIX — WHAT ELSE TO READ (BY TASK CLASS)

### T0 — NAVIGATION / LOOKUP
REQUIRED:
- KB governance (Section 3)
OPTIONAL:
- Any domain KB module that matches the requested topic (selected via KB master index)

### T1 — DOCUMENT AUTHORING
REQUIRED:
- KB governance (Section 3)
- UID: UE.STD.DOC_CONTROL.001 | WHY: header/control + doc discipline
- UID: UE.LAW.NAMING.001 | WHY: naming constraints
- UID: UE.LAW.UID.001 | WHY: UID rules
- UID: UE.LAW.VERSIONING.001 | WHY: change note / version semantics
OPTIONAL:
- Templates relevant to the document type (found via KB master index, then opened)

### T2 — CANON / GOVERNANCE CHANGE
REQUIRED:
- All REQUIRED of T1
- UID: UE.LAW.CANON_PROTOCOL.001 | WHY: canon change workflow and index authority
OPTIONAL:
- Any layer-specific governance KB modules (selected via KB master index)

### T3 — ENTITY WORK
REQUIRED:
- KB governance (Section 3)
- UID: UE.LAW.UID.001 | WHY: identity stability for entities
- UID: UE.LAW.NAMING.001 | WHY: entity naming discipline
OPTIONAL:
- The entity-model specification / templates (selected via KB master index)

### T4 — PIPELINE / PROCESS DESIGN
REQUIRED:
- KB governance (Section 3)
- UID: UE.KB.DICT.REL_TYPES.001 | WHY: relations must be expressible
- UID: UE.KB.DICT.XREF_RULES.001 | WHY: mapping must be UID-only
OPTIONAL:
- Any pipeline registries / gate standards as required (selected via KB master index)

### T5 — CONTENT PRODUCTION
REQUIRED:
- KB governance (Section 3) (still mandatory to prevent hallucination about system facts)
OPTIONAL (most common):
- Domain KB modules for: lore rules, canon constraints, style/voice, scene standards (selected via KB master index)

### T6 — ANALYSIS / RESEARCH
REQUIRED:
- KB governance (Section 3)
OPTIONAL:
- Domain KB modules relevant to the subject
- If output becomes canon documentation → upgrade to T1/T2 rules

### T7 — IMPLEMENTATION
REQUIRED:
- KB governance (Section 3)
- If output includes canon doc changes → apply T1/T2
OPTIONAL:
- Any implementation templates/policies as required (selected via KB master index)

---

## 5) SELECTION ALGORITHM (DETERMINISTIC)
Step 1: Pick PRIMARY task class T0..T7 (Section 2).  
Step 2: Load REQUIRED KB intake (Section 3).  
Step 3: Apply the matrix rules for your task class (Section 4).  
Step 4: If flags F1/F2/F3/F4 are present:
- F1 HIGH_RISK → treat as T2 (canon discipline) until proven safe
- F2 NEED_XREF → ensure XREF format compliance (UID-only)
- F3 NEED_TEMPLATE → locate required template via KB master index, open it, then use it
- F4 NEED_GATES → apply the relevant gates standards (via KB master index)

Step 5: Only after required scope is loaded, produce output.

---

## 6) FAIL CONDITIONS (HARD STOP)
- Any attempt to use URL/PATH inside XREF or as “navigation”
- Any attempt to “invent” missing facts not opened
- Missing any REQUIRED UID from Section 3
- Task class mismatch (e.g., doing canon change under T5)

---

## 7) EXAMPLES (UID-ONLY)

Example A — “Write a new KB module”
- Task class: T1
- Required UIDs:
  - UE.KB.RULES.001
  - UE.KB.DICT.REL_TYPES.001
  - UE.KB.DICT.XREF_RULES.001
  - UE.STD.DOC_CONTROL.001
  - UE.LAW.NAMING.001
  - UE.LAW.UID.001
  - UE.LAW.VERSIONING.001

Example B — “Change a canonical index”
- Task class: T2
- Required UIDs:
  - (All from Example A)
  - UE.LAW.CANON_PROTOCOL.001

Example C — “Generate story scene”
- Task class: T5
- Required UIDs:
  - UE.KB.RULES.001
  - UE.KB.DICT.REL_TYPES.001
  - UE.KB.DICT.XREF_RULES.001
- Optional:
  - Select the scene/canon/style modules via KB master index and open them before writing.

---

## 8) RELATED (XREF, UID-ONLY)
- XREF: UE.KB.RULES.001 | WHY: KB governance + minimum standard
- XREF: UE.KB.DICT.REL_TYPES.001 | WHY: relation vocabulary
- XREF: UE.KB.DICT.XREF_RULES.001 | WHY: UID-only reference rules
- XREF: UE.STD.DOC_CONTROL.001 | WHY: doc header/control requirements
- XREF: UE.LAW.NAMING.001 | WHY: naming constraints
- XREF: UE.LAW.UID.001 | WHY: identity stability
- XREF: UE.LAW.VERSIONING.001 | WHY: change semantics
- XREF: UE.LAW.CANON_PROTOCOL.001 | WHY: canon change workflow

--- END.
