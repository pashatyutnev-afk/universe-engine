# KB — MODULE STATUS & LOCK POLICY (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/29__KB_MODULE_STATUS_LOCK_POLICY.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: POLICY
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.POL.STATUS_LOCK.029
OWNER: SYSTEM
ROLE: Canonical policy for KB module lifecycle control: STATUS (DRAFT/ACTIVE/DEPRECATED) and LOCK (OPEN/FIXED), with deterministic transition rules, usage permissions for entities, and hard fail conditions.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Defined STATUS/LOCK lifecycle policy for KB modules: transitions, usage permissions, and fail conditions."
- REASON: "Without status/lock policy, entities cannot know what is safe to use; KB drifts and duplicates persist."
- IMPACT: "KB becomes controllable: stable ACTIVE canon, explicit DRAFT iteration, and safe DEPRECATED pointers."
- CHANGE_ID: UE.CHG.2026-01-14.KB.POL.029

---

## 0) PURPOSE (KB)
This policy defines:
- what STATUS values mean
- what LOCK values mean
- when and how modules transition
- what entities are allowed to use in production runs
- hard fail conditions

Navigation is still master-index RAW-only; this policy controls lifecycle.

---

## 1) DEFINITIONS (STRICT)
### STATUS
- DRAFT: module is being built or revised; may change.
- ACTIVE: module is canonical and safe to use.
- DEPRECATED: module is no longer authoritative; must be pointer-first to replacement.

### LOCK
- OPEN: content is editable; iteration allowed.
- FIXED: content is locked; changes require controlled update and versioning discipline.

---

## 2) STATUS POLICY (MEANING + USAGE PERMISSIONS)
### 2.1 DRAFT
Meaning:
- incomplete or unstable
- may lack full coverage or mature examples
Allowed usage:
- allowed for internal iteration and early runs
- must be explicitly acknowledged in outputs if used (trace)
Restrictions:
- cannot be the sole source of truth if an ACTIVE equivalent exists

### 2.2 ACTIVE
Meaning:
- canonical module
- meets minimum schema and QA
Allowed usage:
- default for entities
Restrictions:
- changes must follow change discipline and bump VERSION

### 2.3 DEPRECATED
Meaning:
- non-canon operationally (for execution)
Allowed usage:
- only as pointer for migration/audit
Restrictions:
- must not contain runnable procedures that could be used accidentally
- must point to replacement UID

---

## 3) LOCK POLICY (MEANING + EDIT RIGHTS)
### 3.1 OPEN
Meaning:
- editable
Rules:
- may iterate frequently
- must keep CHANGE_NOTE accurate on meaningful changes
Recommended:
- use OPEN during early drafting

### 3.2 FIXED
Meaning:
- stable lock
Rules:
- do not edit without a controlled change (version bump + change note)
- use FIXED for:
  - ACTIVE canonical modules
  - DEPRECATED pointer modules
  - standards/policies/dictionaries that must remain stable

---

## 4) TRANSITION RULES (DETERMINISTIC)
### 4.1 Promote DRAFT → ACTIVE
Required conditions:
- module follows KB module schema (header complete)
- procedure/templates present (if applicable)
- hard fail conditions present
- related/XREF (UID-only) present
- passes domain boundary checks (no mixing)
- registered in KB master index (RAW exists)
Transition:
- set STATUS: ACTIVE
- set LOCK: FIXED
- bump VERSION (minor or major)
- update CHANGE_NOTE (promotion)

### 4.2 Active maintenance (ACTIVE stays ACTIVE)
Allowed changes:
- patch fixes: typos, clarity improvements, non-semantic formatting
- minor: add examples, tighten rules, small expansions
- major: restructure method, change thresholds, split modules
Required:
- bump VERSION accordingly
- update CHANGE_NOTE

### 4.3 Replace ACTIVE → DEPRECATED (via new canon)
Use deprecation standard:
- create NEW canon module first
- new module supersedes old
- old becomes pointer-first and DEPRECATED
Transition:
- old: STATUS DEPRECATED, LOCK FIXED
- old must point to new UID
- update master index (mark deprecated entry)

### 4.4 Draft retirement (DRAFT → DEPRECATED)
If draft is abandoned or replaced:
- set STATUS DEPRECATED
- convert to pointer or delete (based on policy)
- if kept, it must point to replacement UID or be marked “do not use”

---

## 5) ENTITY USAGE RULES (OPERATIONAL)
Entities MUST:
- prefer ACTIVE over DRAFT when both exist for same function
- never execute from DEPRECATED modules (pointer-only only)
- include in KB_SOURCES trace:
  - module UID
  - status at time of use (optional but recommended)
- if forced to use DRAFT:
  - declare it explicitly in output (risk acknowledged)

---

## 6) VERSIONING GUIDANCE (NON-NUMERIC)
Use semantic intent:
- PATCH: wording/typos/clarity, no method change
- MINOR: additive improvements, new examples, small optional sections
- MAJOR: method/structure changes, thresholds changed, splitting/merging modules, behavior changes

---

## 7) QA CHECKLIST (PASS/FAIL)
PASS IF:
- status meaning matches module reality
- ACTIVE modules are FIXED and registered
- DEPRECATED modules are pointer-first and FIXED
- DRAFT modules are not used as authority when ACTIVE exists
- transitions follow deterministic rules

FAIL IF:
- ACTIVE module is OPEN (unstable) without reason
- DEPRECATED module contains runnable procedures
- DRAFT used silently as canon when ACTIVE exists
- module not registered in master index but treated as usable

---

## 8) HARD FAIL CONDITIONS
FAIL IF:
- STATUS is missing or unknown
- LOCK is missing or unknown
- DEPRECATED module lacks replacement UID pointer
- entity output relies on DEPRECATED as authority
- module is used operationally without master-index registration (existence rule)

---

## 9) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.MODULE_SCHEMA.023 | WHY: module schema required for promotion to ACTIVE
- XREF: UE.KB.TOPIC.META.QA_AUDIT.005 | WHY: audit checks enforce lifecycle correctness
- XREF: UE.KB.STD.MASTER_INDEX_REG.008 | WHY: registration/existence required for operational use
- XREF: UE.KB.STD.DEPRECATION_POINTER.007 | WHY: required flow for ACTIVE→DEPRECATED replacement

--- END.
