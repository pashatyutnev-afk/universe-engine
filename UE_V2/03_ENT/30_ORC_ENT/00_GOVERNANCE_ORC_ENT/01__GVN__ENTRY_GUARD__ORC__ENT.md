FILE: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/01__GVN__ENTRY_GUARD__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 00_GOVERNANCE_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: GVN_ORC_ENT
UID: UE.V2.ENT.ORC.GVN.ENTRY_GUARD.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: GVN_ENTRY_GUARD
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.GVN.ENTRY_GUARD.001
- STATUS: ACTIVE
- OWNER: ORC_ENT
- VERSION: 1.0.0
- CREATED: 2026-02-02
- UPDATED: 2026-02-02

## [M] PURPOSE
Входной “шлагбаум” Governance-раннера.
Нормализует входной TASK_TEXT в управляемый токен и валидирует базовые требования (режим, наличие ключей, границы задачи).

## [M] CAPABILITIES (what it can produce)
- Produces: [GOVN_TASK_TOKEN, CHANGE_INTENT, FAIL_CODE?]
- Edits: [] (MODE REPO)
- Never:
  - не изменяет файлы/репо
  - не использует PATH как обход при наличии KEY-навигации
  - не добавляет RAW-ссылки в выходы

## [M] INPUTS / OUTPUTS
- Inputs:
  - TASK_TEXT: исходный запрос (что нужно сделать)
  - MODE_HINT?: FAST|RELEASE_READY|MASTERPIECE (опционально)
  - TARGET_KEYS?: список ключей/реалмов (если известны)
- Outputs:
  - GOVN_TASK_TOKEN: intent + scope + constraints + targets
  - CHANGE_INTENT: create|update|deprecate|route|check
  - FAIL_CODE?: UE.FAIL.INPUT_ABSENT | UE.FAIL.RULE_VIOLATION

## [M] INTERFACES (RAW only)
- Entry points (RAW):
- Dependencies (RAW):

## [M] KB SCOPE
- KB Inputs: [законы RAW-only, no-edit режим, схемы индексов/ключей]
- KB Outputs: [только токены прогона и краткие выводы, без записи в KB]
- KB Boundaries: [не угадывать отсутствующие входы; не расширять scope без подтверждения]
- KB RAW refs: []

## [M] GATES (pass/fail)
- PASS if:
  - TASK_TEXT присутствует
  - intent и scope определены однозначно
  - нет прямых нарушений режима (no-edit)
- FAIL if:
  - TASK_TEXT отсутствует
  - запрос требует действий, запрещённых в MODE REPO (изменения/правки)
  - scope не определён и не может быть выведен из входа

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, CTL, VAL, QA]
- Handoff rules:
  - Передаёт GOVN_TASK_TOKEN в RULE_ENFORCER/DEPENDENCY_RESOLVER
  - При FAIL — возвращает FAIL_CODE и минимальное требование на вход

## [M] CHANGELOG (minimal)
- 2026-02-02: v1.0.0 init
