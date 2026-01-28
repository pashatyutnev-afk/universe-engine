# KB — GATE VERSIONING POLICY (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/94__KB_GATE_VERSIONING_POLICY.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: POLICY
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.POL.GATE_VERSIONING.094
OWNER: SYSTEM
ROLE: Defines versioning discipline for gates: what changes are PATCH/MINOR/MAJOR, when recalibration is required, and when to replace a gate with a new UID instead of editing in place.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created gate versioning policy with recalibration triggers and UID replacement rules."
- REASON: "Gates affect many dependents; versioning prevents silent behavior changes and keeps QA calibration stable."
- IMPACT: "Predictable gate evolution, safer upgrades, and fewer regressions."
- CHANGE_ID: UE.CHG.2026-01-14.KB.POL.094

---

## 0) PURPOSE (KB)
Control how gate definitions evolve:
- what changes can happen in-place
- when version bump is required
- when replacement (new UID) is required
- when exemplar recalibration is required

---

## 1) VERSION TYPES
PATCH (x.y.Z)
- typo fixes
- formatting
- clarification without changing pass/fail outcomes
- adding examples that do not change criteria

MINOR (x.Y.z)
- adding a new measurable check that tightens REWORK but not FAIL
- adding additional detection steps
- improving thresholds slightly with same intent
- expanding notes/edge cases
Requires:
- recalibration recommended if key gate

MAJOR (X.y.z)
- changing PASS/FAIL criteria
- changing thresholds that alter classification
- changing test method such that results differ
- changing skill tag coverage meaningfully
Rule:
- For key gates, MAJOR changes should usually be done via replacement gate (new UID) rather than editing in place.

---

## 2) KEY GATE RULES
If a gate is KEY:
- PATCH changes: ok in-place
- MINOR changes: ok in-place, recalibrate exemplar set
- MAJOR changes: prefer replacement (new UID) + migration protocol

---

## 3) RECALIBRATION TRIGGERS
Recalibration required if:
- criteria change (MINOR or MAJOR)
- thresholds change
- exemplar mismatch rate increases
- domain QA calibration fails

Recalibration optional for:
- pure formatting changes

---

## 4) REPLACEMENT (NEW UID) RULES
Replace gate with a new UID if:
- semantic meaning changes (PASS/FAIL boundaries shift)
- gate function is refactored substantially
- you must preserve legacy behavior while introducing new logic
- gate is duplicated/conflicting and needs a canon resolution

Replacement requires:
- deprecation pointer from old to new
- migration of packs/examples
- calibration of new gate exemplar set
- audit record and possibly release notes

---

## 5) HARD FAIL CONDITIONS
FAIL IF:
- behavior changes are shipped as PATCH without disclosure
- key gate criteria changed without recalibration
- major semantic changes done in-place without replacement/migration plan
- version bumped without change note and audit where required

---

## 6) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.POL.GATE_LIBRARY.092 | WHY: defines key gate criteria and discipline
- XREF: UE.KB.RULE.GATE_DEPRECATE.093 | WHY: safe replacement/migration flow
- XREF: UE.KB.PROC.DOMAIN_QA_CALIB.087 | WHY: recalibration protocol
- XREF: UE.KB.POL.AUDIT_TRAIL.058 | WHY: major gate changes should be auditable
- XREF: UE.KB.STD.RELEASE_NOTES.060 | WHY: wide impact changes should publish release notes

--- END.
