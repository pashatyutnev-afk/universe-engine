# KB — KB RELATION MODEL STANDARD (REL + XREF) (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/24__KB_RELATION_MODEL_STANDARD.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.STD.RELATION_MODEL.024
OWNER: SYSTEM
ROLE: Defines the canonical relation model for KB modules: how REL (semantic edges) and XREF (UID-only pointers) coexist, where each belongs, allowed formats, and validation rules. Ensures the KB graph is consistent and machine-checkable.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Defined canonical KB relation model: REL semantics + UID-only XREF pointers, placement rules, and validation."
- REASON: "If REL and XREF are mixed inconsistently, dependency graphs break and entities cannot reason deterministically."
- IMPACT: "KB becomes graph-consistent; enables audits, tooling, and reliable scope selection."
- CHANGE_ID: UE.CHG.2026-01-14.KB.STD.024

---

## 0) PURPOSE (KB)
Standardize relationships across KB:
- REL expresses meaning (dependency, governance, validation, deprecation)
- XREF expresses identity pointers (UID-only)
- both must be consistent and minimal

Navigation remains in KB master index (RAW-only).

---

## 1) DEFINITIONS (STRICT)
### REL (semantic edge)
A directed edge that states meaning:
- depends_on, complements, governed_by, validated_by, etc.

### XREF (identity pointer)
A UID-only pointer:
- "this module points to that module UID" (no semantics beyond WHY).

### Relation graph
Union of REL edges + XREF pointers.

---

## 2) ABSOLUTE RULES
R1 — UID-only targets
- Any target that is a module must be referenced by UID in XREF.
- REL targets may be UID or stable label depending on module type, but recommended UID when available.

R2 — No URLs/PATH in XREF
- XREF is UID-only. URLs/paths are forbidden.

R3 — REL is optional but XREF is mandatory
- If your KB module schema requires RELATED (UID-only), at least one XREF must exist (usually governance links).
- REL edges should be used when semantics matter.

R4 — Minimal graph
- Do not list everything; keep edges to essential dependencies and governance.

---

## 3) WHEN TO USE REL VS XREF
Use REL when you need semantics:
- prerequisites (depends_on/requires)
- governance (governed_by/constrained_by)
- validation (validated_by)
- replacement (supersedes/deprecated_by)
- mapping semantics (maps_to)

Use XREF when you need identity pointers without semantics:
- governance baseline pointers
- companion module pointers
- “see also” stable references

---

## 4) PLACEMENT RULES (WHERE TO PUT REL/XREF)
### 4.1 In TOPIC modules
- REL block: optional (if dependencies/governance/validation exist)
- XREF block: mandatory (at least governance UIDs)

### 4.2 In MAP modules
- REL block: recommended (maps_to / governed_by)
- XREF block: mandatory (companion map UIDs)

### 4.3 In STANDARD/PROTOCOL modules
- REL block: recommended (governed_by / constrained_by / supersedes)
- XREF block: mandatory (core dictionaries/policies)

### 4.4 In DEPRECATED pointer modules
- REL block: mandatory (deprecated_by)
- XREF block: mandatory (replacement UID)

---

## 5) CANONICAL FORMATS
### 5.1 REL format
REL:
- REL: <rel_type> -> <TARGET_UID_OR_LABEL> | WHY: <short reason>

Rules:
- rel_type must be from canonical REL dictionary.
- direction must match meaning.

### 5.2 XREF format (UID-only)
XREF:
- XREF: <TARGET_UID> | WHY: <short reason>

Rules:
- one UID per line
- WHY mandatory
- no URL/PATH anywhere in XREF

---

## 6) VALIDATION RULES (PASS/FAIL)
PASS IF:
- REL uses only canonical types
- XREF is UID-only and has WHY on each line
- no URL/PATH present in XREF
- relation count is minimal and relevant
- deprecation edges are paired correctly (supersedes + deprecated_by)

FAIL IF:
- custom relation types appear
- missing WHY
- any URL/PATH in XREF
- deprecation without pointer standard
- REL direction used incorrectly (depends_on inverted)

---

## 7) RECOMMENDED MINIMUM XREF SET
Any KB module should include at least:
- XREF: UE.KB.DICT.XREF_RULES.005 | WHY: uid-only reference policy
- XREF: UE.KB.DICT.REL_TYPES.004 | WHY: relation vocabulary (if REL used)

Optional:
- governance/meta usage protocol UIDs (if required by your governance minimum set)

---

## 8) EXAMPLES
Example A (topic with dependency):
REL:
- REL: depends_on -> UE.KB.TOPIC.MUSIC.PROMPT_CONTRACT.001 | WHY: contract required before phrasebook deltas
XREF:
- XREF: UE.KB.DICT.XREF_RULES.005 | WHY: uid-only rule

Example B (deprecation):
New:
- REL: supersedes -> UE.KB.TOPIC.X.010 | WHY: replaced by improved module
Old:
- REL: deprecated_by -> UE.KB.TOPIC.X.011 | WHY: new canon
- XREF: UE.KB.TOPIC.X.011 | WHY: replacement

---

## 9) HARD FAIL CONDITIONS
FAIL IF:
- module is missing XREF block (if schema requires)
- XREF contains non-UID target
- REL types not canonical
- mixing URLs into relations
- semantics required but omitted (e.g., deprecation without REL)

---

## 10) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.DICT.REL_TYPES.004 | WHY: canonical relation types
- XREF: UE.KB.DICT.XREF_RULES.005 | WHY: uid-only xref rules
- XREF: UE.KB.TPL.REL_GRAPH.006 | WHY: relation graph template

--- END.
