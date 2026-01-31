FILE: UE_V2/03_ENT/01_TPL_ENT/60__TPL__QA__ENT.md
SCOPE: UE_V2 / 03_ENT / 01_TPL_ENT
DOC_TYPE: TEMPLATE
TEMPLATE_FOR: ENTITY_PASSPORT (QA)
DOMAIN: ENT
UID: UE.V2.ENT.TPL.QA.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: Template has no RAW

---

## [M] PURPOSE
Шаблон паспорта QA.
QA выполняет проверку качества по сценарию и выдаёт QA_REPORT (scored + gates).

## [M] HARD_RULES
- QA_REPORT обязателен и краткий.
- Никаких RAW. Только KEYS ONLY.
- Метрики/скоринг должны быть объяснимы одной строкой.
- Итог строго PASS/REWORK/FAIL.

## [M] QA_REPORT_SCHEMA
- TARGET
- SCORE: 0..100
- FINDINGS: [0..N]
- GATES: PASS|REWORK|FAIL
- NEXT: "го" | FAIL_CODE

## [M] BODY_TEMPLATE

### ENTITY_HEADER
ENTITY_TYPE: QA
ENTITY_NAME: <REPLACE_ME>
ENTITY_KEY: <KEY_FOR_INDEX_MANIFEST>
DOMAIN_TAGS: [<LIST>]
OWNER_TEAM: <SYS|TEAM>
LIFECYCLE: ACTIVE|DRAFT|DEPRECATED

### PURPOSE
<1-2 lines>

### QA_SCOPE
- TARGET_TYPES: [<ARTIFACT/ENTITY TYPES>]
- QUALITY_AXES: [Readability, Minimality, Traceability, CanonIntegrity, ...]
- DEFAULT_THRESHOLD: <number>                  # e.g. 75

### QA_PROCEDURE
- STEP_01: <one line>
- STEP_02: <one line>
- STEP_03: <one line>

### OUTPUTS
- ARTIFACTS: [QA_REPORT, PATCH_NOTES?]

### QA_REPORT (format)
- TARGET: <REPLACE_ME>
  SCORE: <0..100>
  FINDINGS:
    - <one line>
  GATES: PASS|REWORK|FAIL
  NEXT: "го" | <FAIL_CODE>

### DEPENDENCIES (KEYS ONLY)
- LAW_KEYS: [LAW_01, LAW_02, LAW_03, LAW_04, LAW_05, LAW_06, LAW_14, LAW_20]
- STD/REG_KEYS: [<KEYS_ONLY>]

### GATES
PASS_IF:
- score >= threshold and no FAIL findings
REWORK_IF:
- score below threshold or missing trace
FAIL_IF:
- violates hard laws (RAW/no artifact/canon conflict)

### CHANGELOG (append-only)
- DATE: 0000-00-00
  CHANGE_ID: <REPLACE_ME>
  TYPE: CREATE|UPDATE|DEPRECATE
  NOTES: <one line>
