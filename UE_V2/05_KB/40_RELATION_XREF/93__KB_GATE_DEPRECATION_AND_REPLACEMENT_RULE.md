# KB — GATE DEPRECATION & REPLACEMENT RULE (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/93__KB_GATE_DEPRECATION_AND_REPLACEMENT_RULE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: RULE
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.RULE.GATE_DEPRECATE.093
OWNER: SYSTEM
ROLE: Defines deterministic deprecation and replacement flow for gates so packs/examples/certification do not break: pointer-first migration, replacement binding, exemplar recalibration, and audit/release discipline.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created gate deprecation & replacement rule with safe migration for packs and examples."
- REASON: "Gates are referenced by many artifacts; uncontrolled changes break QA calibration and cause regressions."
- IMPACT: "Stable migrations, consistent QA, and safer evolution of gate library."
- CHANGE_ID: UE.CHG.2026-01-14.KB.RULE.093

---

## 0) PURPOSE (KB)
Deprecate/replace gates safely:
- prevent broken references in packs/examples
- preserve calibration meaning
- ensure auditability and controlled behavior changes

---

## 1) ABSOLUTE RULES
R1 — Never delete a gate that is referenced
- Deprecate instead, with a replacement UID.

R2 — Replacement must be explicit
- Deprecated gate must declare REPLACED_BY (UID-only).

R3 — Update dependents
- Packs and examples referencing the old gate must be migrated.

R4 — Recalibrate exemplars
- Key gates must have exemplar sets; replacements require recalibration.

---

## 2) DEPRECATION FLOW (DETERMINISTIC)
Step 1: Identify reason
- duplicate, conflict, incorrect criteria, improved method

Step 2: Create replacement gate (new UID)
- define criteria and test method
- ensure measurability and tags

Step 3: Mark old gate as DEPRECATED
- add pointer/notice:
  - REPLACED_BY: <new gate UID>

Step 4: Migrate dependents
- update competence packs:
  - replace old gate UID references with new
- update examples:
  - replace related gate UID
  - re-evaluate label and explanation
- update exemplar sets:
  - create/update exemplar set for new gate
  - retire or migrate old set

Step 5: Validate
- run calibration protocol
- run pack QA gates
- run trace review if evaluation logic changed

Step 6: Audit & release notes
- audit record is mandatory for key gate changes
- release notes required if wide impact

---

## 3) SAFE MIGRATION RULES
- Use pointer-first: keep old gate available as deprecated pointer until dependents migrated.
- Do not mark new gate ACTIVE_READY until exemplar calibration passes.
- If gate semantics changed significantly:
  - treat as new gate, not a patch to old one.

---

## 4) HARD FAIL CONDITIONS
FAIL IF:
- old gate removed while referenced
- old gate deprecated without replacement UID
- packs/examples not migrated
- exemplar calibration missing for key gate replacements
- audit trail skipped for key gate changes

---

## 5) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.POL.GATE_LIBRARY.092 | WHY: gate library policy defines key gate discipline
- XREF: UE.KB.STD.GATE_DEF.088 | WHY: replacement gate must follow gate definition standard
- XREF: UE.KB.RULE.GATE_EXAMPLE_BIND.090 | WHY: key gates require exemplar sets
- XREF: UE.KB.PROC.DOMAIN_QA_CALIB.087 | WHY: recalibration after replacement
- XREF: UE.KB.POL.AUDIT_TRAIL.058 | WHY: deprecation/replacement must be audited
- XREF: UE.KB.STD.RELEASE_NOTES.060 | WHY: wide impact requires release notes

--- END.
