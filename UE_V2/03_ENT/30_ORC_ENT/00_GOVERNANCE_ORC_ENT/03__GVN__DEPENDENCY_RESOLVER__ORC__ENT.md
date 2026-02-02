FILE: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/03__GVN__DEPENDENCY_RESOLVER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 00_GOVERNANCE_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: GVN_ORC_ENT
UID: UE.V2.ENT.ORC.GVN.DEPENDENCY_RESOLVER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: GVN_DEPENDENCY_RESOLVER
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.GVN.DEPENDENCY_RESOLVER.001
- STATUS: ACTIVE
- OWNER: ORC_ENT
- VERSION: 1.0.0
- CREATED: 2026-02-02
- UPDATED: 2026-02-02

## [M] PURPOSE
Считает зависимости для governance-прогона.
Формирует минимальный WORK_SET_KEYS и порядок шагов/открытий без лишнего.

## [M] CAPABILITIES (what it can produce)
- Produces: [WORK_SET_KEYS, LOAD_ORDER, FAIL_CODE?]
- Edits: [] (MODE REPO)
- Never:
  - не добавляет новые сущности/ключи “из головы”
  - не открывает лишние файлы без причины

## [M] INPUTS / OUTPUTS
- Inputs:
  - GOVN_TASK_TOKEN
  - RULE_CHECK_REPORT (PASS)
  - AVAILABLE_KEYS (из INDEX_MANIFEST, через раннер)
- Outputs:
  - WORK_SET_KEYS: минимальный набор ключей на прогон
  - LOAD_ORDER: порядок резолва/открытий (keys-only)
  - FAIL_CODE?: UE.FAIL.MISSING_KEY

## [M] INTERFACES (RAW only)
- Entry points (RAW):
- Dependencies (RAW):

## [M] KB SCOPE
- KB Inputs: [KEY-схемы реалма, REQUIRED_KEYS, доменные зависимости]
- KB Outputs: [work-set токены]
- KB Boundaries: [не принимать монтажных решений; не выходить за scope]
- KB RAW refs: []

## [M] GATES (pass/fail)
- PASS if:
  - все нужные ключи существуют
  - набор минимален и достаточен под intent
- FAIL if:
  - нужного ключа нет (UE.FAIL.MISSING_KEY)
  - scope не определён и требует уточнения входа

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, CTL, QA]
- Handoff rules:
  - Передаёт WORK_SET_KEYS в CHANGE_CONTROL / RISK_SAFETY / DECISION_APPROVAL по маршруту

## [M] CHANGELOG (minimal)
- 2026-02-02: v1.0.0 init
