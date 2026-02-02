FILE: UE_V2/03_ENT/30_ORC_ENT/02_CREATIVE_ORC_ENT/01__CRV__IDENTITY_FACTORY__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 02_CREATIVE_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: CRV_ORC_ENT
UID: UE.V2.ENT.ORC.CRV.IDENTITY_FACTORY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: CRV_IDENTITY_FACTORY
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.CRV.IDENTITY_FACTORY.001

## [M] PURPOSE
Собирает IDENTITY_TOKEN: имя/лейбл/тон/голос/позиционирование, и минимальные правила консистентности.
Работает как “фабрика рамки”, не как генератор конечных артефактов.

## [M] INPUTS / OUTPUTS
- Inputs: [CREATIVE_BRIEF, CREATIVE_CONSTRAINTS_LOCK]
- Outputs: [IDENTITY_TOKEN, FAIL_CODE?]

## [M] TOKEN_SCHEMA (IDENTITY_TOKEN)
- NAME: string
- TAGLINE: string
- VOICE: [keywords]
- BANNED: [keywords]
- DO: [principles]
- DONT: [principles]
- AUDIENCE: string
- LOCALE: string
- BRAND_RULES: [rules]

## [M] INTERFACES (RAW only)
- Entry points (RAW):
- Dependencies (RAW):

## [M] KB SCOPE
- KB Inputs: [бренд-ограничения, project naming constraints]
- KB Outputs: [IDENTITY_TOKEN]
- KB Boundaries: [без придумывания фактов о пользователе/компании]

## [M] GATES
- PASS: token заполнен и непротиворечив
- FAIL: нет данных для имени/тона или конфликт запретов

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, QA]
- Handoff: IDENTITY_TOKEN -> STYLE_SYSTEM_BUILDER / TREND_SYNTHESIZER

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
