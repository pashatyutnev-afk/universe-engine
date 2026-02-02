FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/12__MUS__LYRICS_FOCUS_LOOP__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.ORC.MUS.LYRICS_FOCUS_LOOP.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_LYRICS_FOCUS_LOOP
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MUS.LYRICS_FOCUS_LOOP.001

## [M] PURPOSE
Цикл смысловой и ритмической доводки: ясность образов, логика куплетов, сила припева, повторяемость, естественность фраз.
Сохраняет запреты и политику пунктуации.

## [M] INPUTS / OUTPUTS
- Inputs: [LYRIC_BRIEF, LYRICS_FINAL]
- Outputs: [LYRICS_LOOP_NOTES, REWRITE_SUGGESTIONS, FAIL_CODE?]

## [M] GATES
- PASS: улучшения без срыва структуры и запретов
- FAIL: нехватка входа или конфликт требований

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Handoff: suggestions -> LYRIC_EDITOR / LYRIC_DRAFTER

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
