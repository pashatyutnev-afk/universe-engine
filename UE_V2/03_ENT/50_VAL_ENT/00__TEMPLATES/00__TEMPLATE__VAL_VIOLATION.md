# VAL VIOLATION — TEMPLATE

FILE: 03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/00__TEMPLATES/00__TEMPLATE__VAL_VIOLATION.md
SCOPE: Universe Engine (Games volume) / Validators (VAL) / Violation record template
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
ENTITY_GROUP: VALIDATORS (VAL)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.GAMES.TPL.VAL.VIOLATION.001
OWNER: SYSTEM
ROLE: Canonical violation record format for VAL reports (S0–S3).

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MINOR
- SUMMARY: "DOC CONTROL alignment + normalized fields."
- REASON: "Make violations machine-readable and consistent across validators."
- IMPACT: "VAL reports become comparable and auditable."
- CHANGE_ID: UE.CHG.2026-01-20.VAL.TPL.VIOLATION.001

---

## VIOLATION (RECORD SCHEMA)
CODE: <short stable code>
SEVERITY: S0|S1|S2|S3
MESSAGE: "<what is violated>"
FIX_ACTION: "<required change>"
AUTO_FIX_SUGGESTION: "<optional suggestion, not a domain decision>"
