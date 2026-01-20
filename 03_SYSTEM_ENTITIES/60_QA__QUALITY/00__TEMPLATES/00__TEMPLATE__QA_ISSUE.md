# QA ISSUE — TEMPLATE

FILE: 03_SYSTEM_ENTITIES/60_QA__QUALITY/00__TEMPLATES/00__TEMPLATE__QA_ISSUE.md
SCOPE: Universe Engine (Games volume) / Quality (QA) / Issue record template
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
ENTITY_GROUP: QUALITY (QA)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.GAMES.TPL.QA.ISSUE.001
OWNER: SYSTEM
ROLE: Canonical issue record format for QA reports (S0–S3).

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MINOR
- SUMMARY: "DOC CONTROL alignment + normalized fields."
- REASON: "Make QA issues consistent and auditable."
- IMPACT: "QA reports become comparable across checks."
- CHANGE_ID: UE.CHG.2026-01-20.QA.TPL.ISSUE.001

---

## ISSUE (RECORD SCHEMA)
CODE: <short stable code>
SEVERITY: S0|S1|S2|S3
MESSAGE: "<what is wrong>"
FIX_SUGGESTION: "<how to improve>"
