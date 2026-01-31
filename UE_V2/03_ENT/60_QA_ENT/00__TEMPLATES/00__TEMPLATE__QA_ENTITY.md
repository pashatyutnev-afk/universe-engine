# QA ENTITY — TEMPLATE

FILE: 03_SYSTEM_ENTITIES/60_QA__QUALITY/00__TEMPLATES/00__TEMPLATE__QA_ENTITY.md
SCOPE: Universe Engine (Games volume) / Quality (QA) / Template
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
ENTITY_GROUP: QUALITY (QA)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.GAMES.TPL.QA.ENTITY.001
OWNER: SYSTEM
ROLE: Canonical template for a QA entity (contract + checks + report schema).

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MINOR
- SUMMARY: "DOC CONTROL alignment + normalized mandatory sections + RAW-only interfaces."
- REASON: "Prevent stub QA entities and inconsistent report formats."
- IMPACT: "QA entities become consistently usable as ORC gates."
- CHANGE_ID: UE.CHG.2026-01-20.QA.TPL.ENTITY.001

---

## 0) HEADER (REQUIRED)
UID:
FAMILY:
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
OWNER: SYSTEM
ROLE: "<one-line: what quality dimension this QA entity evaluates>"

## 1) PURPOSE (REQUIRED)
- что именно оцениваем
- где применяется (какие outputs / какие ORC gates)
- что считается FAIL (в терминах S0–S3)

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- artifact_result: []
- quality_frame: []

PRODUCES:
- qa_report: [QA_REPORT]
- issues_list: [ISSUE]
- fix_suggestions: []

DEPENDS_ON:
- []

OUTPUT_TARGET:
- OUT | PRJ | LOG

## 3) QUALITY CHECKS (MANDATORY)
### REQUIRED CHECKS (ordered)
- CHECK_01:
  - WHAT: "<what is evaluated>"
  - FAIL_IF: "<condition>"
  - SEVERITY: S0|S1|S2|S3
  - FIX_SUGGESTION: "<how to improve>"
- CHECK_02:
  - ...

### OPTIONAL CHECKS
- CHECK_X: ...

## 4) REPORT FORMAT (MANDATORY)
QA_REPORT:
- RESULT: PASS | FAIL
- TARGET_UID: <UID цели или NONE>
- SCORE: <0..100> (optional)
- ISSUES: (list of ISSUE)
- RED_FLAGS: (optional list)

ISSUE schema reference:
- use template `00__TEMPLATE__QA_ISSUE.md`

## 5) INTERFACES (RAW ONLY)
- QA Rules:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/01__RULES__QA.md
- QA Issue Template:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/00__TEMPLATES/00__TEMPLATE__QA_ISSUE.md
- UID Rules:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md
- DOC CONTROL Standard:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
