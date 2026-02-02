FILE: UE_V2/03_ENT/50_VAL_ENT/90_SHARED_LIB_VAL_ENT/02__LIB__FAIL_CODE_MAP__VAL__ENT.md
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT / 90_SHARED_LIB_VAL_ENT
DOC_TYPE: VAL_ENTITY
DOMAIN: LIB_VAL_ENT
UID: UE.V2.ENT.VAL.LIB.FAIL_CODE_MAP.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: VAL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: LIB_FAIL_CODE_MAP_VAL
- ENTITY_CLASS: VAL
- UID: UE.V2.ENT.VAL.LIB.FAIL_CODE_MAP.001

## [M] PURPOSE
Единая карта FAIL_CODE для валидаторов: когда ставить какой код, чтобы отчёты были сопоставимы.

## [M] SCOPE
- TARGET_DOMAIN: MULTI
- APPLIES_TO: [ALL_VAL_REPORTS, ALL_VALIDATORS]
- NON_GOALS: [детализация по всем доменам до бесконечности]

## [M] CANON FAIL CODES
- UE.FAIL.INPUT_ABSENT
  - Use when: обязательный вход/артефакт отсутствует.
- UE.FAIL.GATE_FAIL
  - Use when: проверка/гейт не пройден при наличии входа.
- UE.FAIL.RULE_VIOLATION
  - Use when: нарушено жёсткое правило/политика (например RAW вне индекса, direct copy).
- UE.FAIL.MISSING_KEY
  - Use when: контракт/план не может разрешить KEY.
- UE.FAIL.ROUTE_UNRESOLVED
  - Use when: невозможно выбрать реалм/маршрут без входа.
- UE.FAIL.APPROVAL_REQUIRED
  - Use when: нужен внешний decision/approval token (если политика допускает).

## [M] SEVERITY BINDING
- BLOCK: обычно UE.FAIL.RULE_VIOLATION или UE.FAIL.GATE_FAIL
- HIGH: UE.FAIL.GATE_FAIL или UE.FAIL.APPROVAL_REQUIRED
- MED: FAIL_CODE опционален, но допускается UE.FAIL.GATE_FAIL если политика требует
- LOW: FAIL_CODE не обязателен

## [M] DECISION_MATRIX
- IF violation indicates policy break -> UE.FAIL.RULE_VIOLATION
- IF missing required input -> UE.FAIL.INPUT_ABSENT
- IF evidence present but gate failed -> UE.FAIL.GATE_FAIL
- IF cannot resolve key/route -> UE.FAIL.MISSING_KEY / UE.FAIL.ROUTE_UNRESOLVED
- ELSE -> no fail code required

## [M] KB SCOPE
- KB Inputs: [violations, validator context]
- KB Outputs: [normalized fail codes]
- KB Boundaries: [не эскалировать severity без evidence]
- KB RAW refs: []

## [M] GATES
- PASS if: fail codes chosen match definitions
- FAIL if: fail code contradicts evidence (например RULE_VIOLATION без rule break)
