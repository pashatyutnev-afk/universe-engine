FILE: UE_V2/03_ENT/30_ORC_ENT/05_DOCS_ORC_ENT/02__DOC__BUILDER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 05_DOCS_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: DOC_ORC_ENT
UID: UE.V2.ENT.ORC.DOC.BUILDER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: DOC_BUILDER
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.DOC.BUILDER.001

## [M] PURPOSE
Строит DOC_DRAFT по DOC_BRIEF: канонический хедер, нужные секции, ясные формулировки, без лишней лирики.

## [M] INPUTS / OUTPUTS
- Inputs: [DOC_BRIEF, DOC_CONSTRAINTS_LOCK]
- Outputs: [DOC_DRAFT, FAIL_CODE?]

## [M] CORE_RULES
- Обязательный файл-хедер в каноничном порядке.
- INTERFACES: ссылки только RAW (если есть), PATH не использовать как ссылку.
- KB SCOPE обязателен (может быть добавлен следующим шагом, но секция должна существовать).
- VISUAL: только ограничения/риски, без монтажных решений.
- Цвет: principles, не палитры.

## [M] KB SCOPE
- KB Inputs: [brief, template hints]
- KB Outputs: [doc draft]
- KB Boundaries: [не добавлять фактов без источника]
- KB RAW refs: []

## [M] GATES
- PASS: draft содержит все REQUIRED_SECTIONS
- FAIL: отсутствуют обязательные секции

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Handoff: DOC_DRAFT -> KB_SCOPE_BUILDER

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
