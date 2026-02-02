FILE: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/04__GVN__CHANGE_CONTROL__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 00_GOVERNANCE_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: GVN_ORC_ENT
UID: UE.V2.ENT.ORC.GVN.CHANGE_CONTROL.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: GVN_CHANGE_CONTROL
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.GVN.CHANGE_CONTROL.001
- STATUS: ACTIVE
- OWNER: ORC_ENT
- VERSION: 1.0.0
- CREATED: 2026-02-02
- UPDATED: 2026-02-02

## [M] PURPOSE
Описывает “конверт изменений” и правила контроля изменений для governance-операций.
Решает: что допустимо, какие логи/гейты обязательны, какие артефакты должны выйти.

## [M] CAPABILITIES (what it can produce)
- Produces: [CHANGE_ENVELOPE, REQUIRED_LOGS, REQUIRED_GATES, FAIL_CODE?]
- Edits: [] (MODE REPO)
- Never:
  - не разрешает изменения в репо в режиме no-edit
  - не пропускает изменения без логирования требований

## [M] INPUTS / OUTPUTS
- Inputs:
  - GOVN_TASK_TOKEN
  - WORK_SET_KEYS
  - EXEC_MODE
- Outputs:
  - CHANGE_ENVELOPE: тип операции + обязательные условия
  - REQUIRED_LOGS: [RUN_LOG, DECISION_LOG?]
  - REQUIRED_GATES: список проверок, которые должны пройти
  - FAIL_CODE?: UE.FAIL.UNSAFE_CHANGE

## [M] INTERFACES (RAW only)
- Entry points (RAW):
- Dependencies (RAW):

## [M] KB SCOPE
- KB Inputs: [политика изменения, правила деприкации/версий (если задействованы)]
- KB Outputs: [envelope токены, требования к логам]
- KB Boundaries: [не принимать решения по “монтажу”, только правила/ограничения]
- KB RAW refs: []

## [M] GATES (pass/fail)
- PASS if:
  - конверт изменений определён и совместим с режимом
  - известны обязательные логи и проверки
- FAIL if:
  - запрос требует правки репозитория
  - нет способов доказать/заложить гейты под требуемое изменение

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, QA, CTL]
- Handoff rules:
  - Передаёт envelope в RISK_SAFETY и DECISION_APPROVAL

## [M] CHANGELOG (minimal)
- 2026-02-02: v1.0.0 init
