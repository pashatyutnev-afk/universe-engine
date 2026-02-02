FILE: UE_V2/03_ENT/30_ORC_ENT/08_META_ORC_ENT/02__MET__TEMPLATE_APPLIER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 08_META_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MET_ORC_ENT
UID: UE.V2.ENT.ORC.MET.TEMPLATE_APPLIER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MET_TEMPLATE_APPLIER
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MET.TEMPLATE_APPLIER.001

## [M] PURPOSE
Применяет канонические шаблоны: секции, порядок, обязательные блоки (KB SCOPE, GATES, SPC PEER ROLES).
В MODE REPO не редактирует файлы — выдаёт TEMPLATE_APPLY_NOTES и “готовую структуру”.

## [M] INPUTS / OUTPUTS
- Inputs: [DRAFT_OUTPUT?, SELF_CHECK_REPORT]
- Outputs: [TEMPLATE_APPLY_NOTES, STRUCTURE_PATCH?, FAIL_CODE?]

## [M] CORE_RULES
- INTERFACES: только RAW-ссылки (не PATH).
- SPC PEER ROLES всегда отдельным блоком.
- VISUAL: только ограничения/риски, без монтажных решений.
- Цвет: principles, не палитры.

## [M] KB SCOPE
- KB Inputs: [template rules]
- KB Outputs: [apply notes]
- KB Boundaries: [без изменения смысла, только форма]
- KB RAW refs: []

## [M] GATES
- PASS: структура соответствует требуемому шаблону
- FAIL: отсутствуют обязательные секции и их нельзя восстановить без входа

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA, CTL]
- Handoff: notes -> NORMALIZATION_UID / caller packager

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
