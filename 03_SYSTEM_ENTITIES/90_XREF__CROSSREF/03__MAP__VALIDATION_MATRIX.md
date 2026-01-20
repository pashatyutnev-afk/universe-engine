# XREF MAP — VALIDATION MATRIX (CANON)

FILE: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/03__MAP__VALIDATION_MATRIX.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 90_XREF__CROSSREF
DOC_TYPE: MAP
MAP_TYPE: VALIDATION_MATRIX
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.XREF.MAP.VALIDATION_MATRIX.001
OWNER: SYSTEM
ROLE: Defines required CTL/VAL/QA gates by artifact type and acceptance criteria.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: CREATE
- SUMMARY: "Created validation matrix schema to make gates explicit per artifact class."
- REASON: "Stop gate ambiguity and prevent shipping unvalidated artifacts."
- IMPACT: "Any output can be checked against mandatory gates deterministically."
- CHANGE_ID: UE.CHG.2026-01-20.XREF.MAP.VALMATRIX.001

---

## 0) PURPOSE (LAW)
Матрица говорит: для каждого класса артефакта какие CTL/VAL/QA обязательны и как выглядит PASS.

---

## 1) FIELD DICTIONARY
- ARTIFACT_TYPE
- REQUIRED_CTL (comma ids or names)
- REQUIRED_VAL (comma ids or names)
- REQUIRED_QA (comma ids or names)
- REQUIRED_DOC_CONTROL: YES | NO
- PASS_CRITERIA: short
- NOTES

---

## 2) MATRIX TABLE (FILL)
| ARTIFACT_TYPE | REQUIRED_CTL | REQUIRED_VAL | REQUIRED_QA | REQUIRED_DOC_CONTROL | PASS_CRITERIA | NOTES |
|---|---|---|---|---|---|---|
| RUNBOOK | READINESS_CHECK_CTL | TBD | TBD | YES | "All headers+laws satisfied; boot markers defined" |  |
| MAP | READINESS_CHECK_CTL | TBD | TBD | YES | "Schema complete; no duplicate rows; version bumped" |  |
| SPEC | READINESS_CHECK_CTL | TBD | TBD | YES | "Required sections present; interfaces RAW-only" |  |
| PACKAGE | READINESS_CHECK_CTL | TBD | TBD | YES | "Self-contained; SoT/pointers clear; migration steps if rename" |  |

--- END.
