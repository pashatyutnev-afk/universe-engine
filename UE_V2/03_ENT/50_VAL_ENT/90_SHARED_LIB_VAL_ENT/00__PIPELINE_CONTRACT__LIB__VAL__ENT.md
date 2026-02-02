FILE: UE_V2/03_ENT/50_VAL_ENT/90_SHARED_LIB_VAL_ENT/00__PIPELINE_CONTRACT__LIB__VAL__ENT.md
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT / 90_SHARED_LIB_VAL_ENT
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: LIB_VAL_ENT
UID: UE.V2.ENT.PIPE.LIB_VAL_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: VAL_ENT
NAV_RULE: Contract has no RAW

---

## [M] PURPOSE
PIPELINE_CONTRACT — роутер общей библиотеки VAL.
Возвращает ключи общих правил (taxonomy/fail codes/evidence rules) для встраивания в любой валидаторный прогон.
RAW не хранит: всё через KEY и INDEX_MANIFEST.

## [M] HARD_RULES
- RAW запрещён внутри CONTRACT.
- Все ссылки: только KEYS.
- MODE REPO: никаких правок репозитория.
- Выход: VAL_LIB_PLAN (KEYS) + APPLY_NOTES.

## [M] REQUIRED_KEYS
- INDEX_MANIFEST
- PIPELINE_CONTRACT
- VAL.LIB.VIOLATION_TAXONOMY
- VAL.LIB.FAIL_CODE_MAP
- VAL.LIB.EVIDENCE_RULES

## [M] DEFAULT_PLAN (keys)
- ALWAYS:
  - VAL.LIB.VIOLATION_TAXONOMY
  - VAL.LIB.FAIL_CODE_MAP
  - VAL.LIB.EVIDENCE_RULES

## [M] APPLY_NOTES
- Использовать taxonomy как источник violation-id шаблонов.
- Использовать fail-code map для единообразных FAIL_CODE.
- Использовать evidence rules, чтобы PASS никогда не ставился без явного evidence.

## [M] STEP-RUN
- STEP: S0
  GOAL: Return shared VAL library keys
  INPUTS: [TASK_TEXT?, ARTIFACT_HINTS?]
  TARGETS: [INDEX_MANIFEST]
  ACTIONS:
    - Output VAL_LIB_PLAN = DEFAULT_PLAN
  OUTPUTS: [VAL_LIB_PLAN, APPLY_NOTES]
  CHECKS: [REQUIRED_KEYS_PRESENT]
  FAIL: UE.FAIL.MISSING_KEY
  NEXT: "го"

## [M] FAIL_CODES
- UE.FAIL.MISSING_KEY
- UE.FAIL.GATE_FAIL
- UE.FAIL.RULE_VIOLATION
