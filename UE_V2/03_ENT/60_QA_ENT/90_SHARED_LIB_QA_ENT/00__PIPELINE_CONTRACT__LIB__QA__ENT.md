FILE: UE_V2/03_ENT/60_QA_ENT/90_SHARED_LIB_QA_ENT/00__PIPELINE_CONTRACT__LIB__QA__ENT.md
SCOPE: UE_V2 / 03_ENT / 60_QA_ENT / 90_SHARED_LIB_QA_ENT
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: LIB_QA_ENT
UID: UE.V2.ENT.PIPE.LIB_QA_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: QA_ENT
NAV_RULE: Contract has no RAW

---

## [M] PURPOSE
PIPELINE_CONTRACT — роутер общей библиотеки QA.
Возвращает ключи общих правил (severity/fail codes/evidence requirements) для любого QA прогона.
RAW не хранит: всё через KEY и INDEX_MANIFEST.

## [M] HARD_RULES
- RAW запрещён внутри CONTRACT.
- Все ссылки: только KEYS.
- MODE REPO: никаких правок репозитория.
- Выход: QA_LIB_PLAN (KEYS) + APPLY_NOTES.

## [M] REQUIRED_KEYS
- INDEX_MANIFEST
- PIPELINE_CONTRACT
- QA.LIB.SEVERITY_SCALE
- QA.LIB.FAIL_CODE_MAP
- QA.LIB.EVIDENCE_REQUIREMENTS

## [M] DEFAULT_PLAN (keys)
- ALWAYS:
  - QA.LIB.SEVERITY_SCALE
  - QA.LIB.FAIL_CODE_MAP
  - QA.LIB.EVIDENCE_REQUIREMENTS

## [M] APPLY_NOTES
- Severity scale — для единообразных QA_DECISION и issue severity.
- Fail code map — для единых FAIL_CODE.
- Evidence requirements — чтобы PASS/FAIL не ставились без входов, и чтобы ASK использовался корректно.

## [M] STEP-RUN
- STEP: S0
  GOAL: Return shared QA library keys
  INPUTS: [TASK_TEXT?, ARTIFACT_HINTS?]
  TARGETS: [INDEX_MANIFEST]
  ACTIONS:
    - Output QA_LIB_PLAN = DEFAULT_PLAN
  OUTPUTS: [QA_LIB_PLAN, APPLY_NOTES]
  CHECKS: [REQUIRED_KEYS_PRESENT]
  FAIL: UE.FAIL.MISSING_KEY
  NEXT: "го"

## [M] FAIL_CODES
- UE.FAIL.MISSING_KEY
- UE.FAIL.GATE_FAIL
- UE.FAIL.RULE_VIOLATION
