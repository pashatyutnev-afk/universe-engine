FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/12__COR__GATEKEEPER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: COR_ORC_ENT
UID: UE.V2.ENT.ORC.COR.GATEKEEPER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: COR_GATEKEEPER
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.COR.GATEKEEPER.001

## [M] PURPOSE
Финальный арбитр PASS/FAIL.
Проверяет, что артефакты готовы, правила соблюдены, и что можно выдать OUTPUT_PACK.

## [M] INPUTS / OUTPUTS
- Inputs: [SENTINEL_REPORTS, FOCUS_REPORT, PIPE_OUTPUTS]
- Outputs: [FINAL_STATUS, FAIL_CODE?, REQUIRED_FIXES?]

## [M] CORE_RULES
- PASS только если: нет rule violations, есть минимальные outputs, структура ответа корректна.
- FAIL возвращает короткий список REQUIRED_FIXES.

## [M] INTERFACES (RAW only)
- Entry points (RAW):
- Dependencies (RAW):

## [M] KB SCOPE
- KB Inputs: [gates policy]
- KB Outputs: [FINAL_STATUS]
- KB Boundaries: [без новых правил]

## [M] GATES
- PASS: FINAL_STATUS=PASS
- FAIL: FINAL_STATUS=FAIL + FIXES

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA, CTL]
- Handoff: status -> LOGGER / RELEASE_PACKAGER

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
