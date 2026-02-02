FILE: UE_V2/03_ENT/60_QA_ENT/90_SHARED_LIB_QA_ENT/02__LIB__QA_FAIL_CODE_MAP__QA__ENT.md
SCOPE: UE_V2 / 03_ENT / 60_QA_ENT / 90_SHARED_LIB_QA_ENT
DOC_TYPE: QA_ENTITY
DOMAIN: LIB_QA_ENT
UID: UE.V2.ENT.QA.LIB.FAIL_CODE_MAP.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: QA_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: QA_FAIL_CODE_MAP_LIB
- ENTITY_CLASS: QA
- UID: UE.V2.ENT.QA.LIB.FAIL_CODE_MAP.001

## [M] PURPOSE
Единая карта FAIL_CODE для QA: когда ставить какой код, чтобы отчёты были сопоставимы.

## [M] CANON FAIL CODES
- UE.FAIL.INPUT_ABSENT
  - Use when: обязательный вход/артефакт отсутствует (ASK/FAIL по политике реалма).
- UE.FAIL.GATE_FAIL
  - Use when: проверка/гейт не пройден при наличии входа.
- UE.FAIL.RULE_VIOLATION
  - Use when: нарушено жёсткое правило/политика.
- UE.FAIL.MISSING_KEY
  - Use when: контракт/план не может разрешить KEY.
- UE.FAIL.ROUTE_UNRESOLVED
  - Use when: невозможно выбрать маршрут без входа.

## [M] DECISION MATRIX
- IF missing required input -> UE.FAIL.INPUT_ABSENT
- IF evidence present but gate failed -> UE.FAIL.GATE_FAIL
- IF policy broken -> UE.FAIL.RULE_VIOLATION
- IF cannot resolve key -> UE.FAIL.MISSING_KEY
- IF cannot decide route -> UE.FAIL.ROUTE_UNRESOLVED

## [M] GATES
- PASS if: fail codes match evidence and decision
- FAIL if: rule violation used without a real rule break
