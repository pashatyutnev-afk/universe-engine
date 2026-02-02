FILE: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/02__GVN__RULE_ENFORCER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 00_GOVERNANCE_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: GVN_ORC_ENT
UID: UE.V2.ENT.ORC.GVN.RULE_ENFORCER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: GVN_RULE_ENFORCER
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.GVN.RULE_ENFORCER.001
- STATUS: ACTIVE
- OWNER: ORC_ENT
- VERSION: 1.0.0
- CREATED: 2026-02-02
- UPDATED: 2026-02-02

## [M] PURPOSE
Применяет “жёсткие правила” Governance к запросу и маршруту выполнения.
Блокирует некорректные операции и возвращает FAIL_CODE + короткий список исправлений.

## [M] CAPABILITIES (what it can produce)
- Produces: [RULE_CHECK_REPORT, FAIL_CODE?]
- Edits: [] (MODE REPO)
- Never:
  - не допускает RAW внутри контрактов/выходов
  - не допускает обход через PATH вместо KEY-навигации
  - не допускает “угадывание” отсутствующих данных

## [M] INPUTS / OUTPUTS
- Inputs:
  - GOVN_TASK_TOKEN
  - EXEC_MODE
- Outputs:
  - RULE_CHECK_REPORT: список проверок + статус
  - FAIL_CODE?: UE.FAIL.RULE_VIOLATION | UE.FAIL.UNSAFE_CHANGE

## [M] INTERFACES (RAW only)
- Entry points (RAW):
- Dependencies (RAW):

## [M] KB SCOPE
- KB Inputs: [HARD_RULES реалма, ограничения MODE REPO, схемы индекс/KEY]
- KB Outputs: [отчёт проверок, fail-коды]
- KB Boundaries: [не расширять требования; не вводить новые правила без источника]
- KB RAW refs: []

## [M] GATES (pass/fail)
- PASS if:
  - запрос совместим с MODE REPO
  - маршрут построен через KEY->INDEX_MANIFEST->open
- FAIL if:
  - требуется редактирование репо
  - в запросе есть явные RAW/URL требования “в обход”
  - попытка ссылаться на отсутствующие ключи без подтверждения

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, CTL, QA]
- Handoff rules:
  - PASS -> Dependency Resolver
  - FAIL -> вернуть FAIL_CODE + минимальные исправления входа

## [M] CHANGELOG (minimal)
- 2026-02-02: v1.0.0 init
