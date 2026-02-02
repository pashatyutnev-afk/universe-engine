FILE: UE_V2/03_ENT/30_ORC_ENT/02_CREATIVE_ORC_ENT/02__CRV__STYLE_SYSTEM_BUILDER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 02_CREATIVE_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: CRV_ORC_ENT
UID: UE.V2.ENT.ORC.CRV.STYLE_SYSTEM_BUILDER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: CRV_STYLE_SYSTEM_BUILDER
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.CRV.STYLE_SYSTEM_BUILDER.001

## [M] PURPOSE
Строит STYLE_TOKEN: набор принципов и ограничений, плюс “слоты вариаций”.
Не назначает конкретные палитры/монтаж, только принципы и риски.

## [M] INPUTS / OUTPUTS
- Inputs: [CREATIVE_BRIEF, IDENTITY_TOKEN]
- Outputs: [STYLE_TOKEN, FAIL_CODE?]

## [M] TOKEN_SCHEMA (STYLE_TOKEN)
- PRINCIPLES: [style principles]
- CONSTRAINTS: [hard constraints]
- CONTRAST_COLOR_PRINCIPLES: [principles]
- MOTION_RULES: [principles]
- STRUCTURE_RULES: [rules]
- VARIATION_SLOTS: [{slot, options[]}]
- RISKS: [risks]

## [M] INTERFACES (RAW only)
- Entry points (RAW):
- Dependencies (RAW):

## [M] KB SCOPE
- KB Inputs: [style principles, domain constraints from brief]
- KB Outputs: [STYLE_TOKEN]
- KB Boundaries: [без конкретных монтажных решений]

## [M] GATES
- PASS: style принципы и ограничения согласованы
- FAIL: конфликт требований (например, “минимализм” и “максимум деталей” без уточнения)

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Handoff: STYLE_TOKEN -> TREND_SYNTHESIZER / CONCEPT_TO_ARTIFACT_BRIDGE

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
