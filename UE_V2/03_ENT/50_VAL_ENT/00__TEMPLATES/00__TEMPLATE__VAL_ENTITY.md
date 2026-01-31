# VAL ENTITY — TEMPLATE

FILE: 03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/00__TEMPLATES/00__TEMPLATE__VAL_ENTITY.md
SCOPE: Universe Engine (Games volume) / Validators (VAL) / Template
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
ENTITY_GROUP: VALIDATORS (VAL)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.GAMES.TPL.VAL.ENTITY.001
OWNER: SYSTEM
ROLE: Canonical template for a VAL validator entity (contract + checks + report format).

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MINOR
- SUMMARY: "Expanded minimal stub into DOC CONTROL compliant template with mandatory contract + checks + report schema."
- REASON: "Avoid empty validator files and mixed schemas."
- IMPACT: "VAL entities become consistently usable by ORC/CTL/QA chains."
- CHANGE_ID: UE.CHG.2026-01-20.VAL.TPL.ENTITY.001

---

## 0) HEADER (REQUIRED)
UID:
FAMILY:
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
OWNER: SYSTEM
ROLE: "<one-line: what this validator checks>"

## 1) PURPOSE (REQUIRED)
- что именно валидируем
- где применяется (какие пайплайны/артефакты)
- что считается FAIL (в терминах S0–S3)

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- artifacts: []
- governing_refs: []

PRODUCES:
- validation_report: [VAL_REPORT]
- violations_list: [VIOLATION]
- fix_actions: []

DEPENDS_ON:
- []

OUTPUT_TARGET:
- OUT | PRJ | LOG

## 3) CHECK RULES (MANDATORY)
### 3.1 Preconditions
- какие минимальные входы нужны, чтобы проверка была валидной

### 3.2 Checks (ordered)
- CHECK_01:
  - WHAT: "<что проверяем>"
  - FAIL_IF: "<условие>"
  - SEVERITY: S0|S1|S2|S3
  - FIX_ACTION: "<что сделать>"
- CHECK_02:
  - ...

### 3.3 PASS/FAIL policy
- PASS если нет нарушений S0 (и нет S1, если пайплайн запрещает продолжение при S1)
- FAIL если есть хотя бы одно S0
- S1/S2/S3 обязаны попасть в отчёт как VIOLATION записи

## 4) REPORT FORMAT (MANDATORY)
VAL_REPORT:
- RESULT: PASS | FAIL
- TARGET_UID: <UID цели или NONE>
- VIOLATIONS: (list of VIOLATION)

VIOLATION schema reference:
- use template `00__TEMPLATE__VAL_VIOLATION.md`

## 5) INTERFACES (RAW ONLY)
- VAL Rules:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/01__RULES__VAL.md
- VAL Violation Template:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/00__TEMPLATES/00__TEMPLATE__VAL_VIOLATION.md
- UID Rules:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md
- DOC CONTROL Standard:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
