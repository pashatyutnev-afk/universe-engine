FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/08__MUS__PROMPT_PACKAGER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.ORC.MUS.PROMPT_PACKAGER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_PROMPT_PACKAGER
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MUS.PROMPT_PACKAGER.001

## [M] PURPOSE
Собирает PROMPT_PACK для генератора музыки: описание стиля, структура, вокал, BPM, настроение, текст, запреты, варианты.
Учитывает SOURCE_POLICY_TOKEN и пунктуационную политику.

## [M] INPUTS / OUTPUTS
- Inputs: [MUS_BRIEF, STYLE_ROUTE_TOKEN, LYRICS_FINAL, SOURCE_POLICY_TOKEN?]
- Outputs: [PROMPT_PACK, FAIL_CODE?]

## [M] PROMPT_PACK (sections)
- MAIN_PROMPT
- NEGATIVE_PROMPT (banned)
- LYRICS (final)
- VARIANTS (optional)
- NOTES (constraints lock)

## [M] GATES
- PASS: pack полный, запреты учтены
- FAIL: отсутствует стиль или текст, если они обязательны

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Handoff: PROMPT_PACK -> TRACK_BUILD_STEP / QA_CHECKS

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
