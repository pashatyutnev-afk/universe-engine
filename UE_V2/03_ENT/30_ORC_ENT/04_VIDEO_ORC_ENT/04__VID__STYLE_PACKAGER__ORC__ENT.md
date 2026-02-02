FILE: UE_V2/03_ENT/30_ORC_ENT/04_VIDEO_ORC_ENT/04__VID__STYLE_PACKAGER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 04_VIDEO_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: VID_ORC_ENT
UID: UE.V2.ENT.ORC.VID.STYLE_PACKAGER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: VID_STYLE_PACKAGER
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.VID.STYLE_PACKAGER.001

## [M] PURPOSE
Собирает STYLE_PACK: принципы визуала, ограничения, слоты стилей для переключений, риски.
Не задаёт конкретные палитры и монтажные решения.

## [M] INPUTS / OUTPUTS
- Inputs: [VID_BRIEF, SHOT_PLAN]
- Outputs: [STYLE_PACK, FAIL_CODE?]

## [M] STYLE_PACK (schema)
- PRINCIPLES
- CONSTRAINTS
- STYLE_SLOTS: [{slot_name, style_principles, do, dont}]
- COLOR_CONTRAST_PRINCIPLES
- MOTION_PRINCIPLES
- RISKS

## [M] GATES
- PASS: слоты определены и совместимы с subject lock
- FAIL: конфликт стилей без уточнения

## [M] KB SCOPE
- KB Inputs: [brief + shot plan]
- KB Outputs: [style pack]
- KB Boundaries: [principles only]

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Handoff: STYLE_PACK -> PROMPT_FACTORY / QA_CHECKS

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
