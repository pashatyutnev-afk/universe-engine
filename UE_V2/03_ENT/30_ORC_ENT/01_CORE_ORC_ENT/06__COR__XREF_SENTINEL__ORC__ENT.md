FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/06__COR__XREF_SENTINEL__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: COR_ORC_ENT
UID: UE.V2.ENT.ORC.COR.XREF_SENTINEL.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: COR_XREF_SENTINEL
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.COR.XREF_SENTINEL.001

## [M] PURPOSE
Контролирует кросс-реалм ссылки: только через разрешённые KEY и границы scope.
Не даёт “утечь” в чужие зоны без подтверждения.

## [M] INPUTS / OUTPUTS
- Inputs: [ROUTE_TOKEN]
- Outputs: [XREF_CHECK_REPORT, FAIL_CODE?]

## [M] CORE_RULES
- Любое расширение target realms требует явного основания в TASK_TOKEN.
- XREF только как KEYS, без прямых RAW/URL в сущностях.

## [M] INTERFACES (RAW only)
- Entry points (RAW):
- Dependencies (RAW):

## [M] KB SCOPE
- KB Inputs: [xref boundaries]
- KB Outputs: [XREF_CHECK_REPORT]
- KB Boundaries: [без расширения scope]

## [M] GATES
- PASS: ссылки в допустимых границах
- FAIL: попытка выхода за границы

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [CTL, QA]
- Handoff: report -> PIPE_SELECTOR / FAIL_HANDLER

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
