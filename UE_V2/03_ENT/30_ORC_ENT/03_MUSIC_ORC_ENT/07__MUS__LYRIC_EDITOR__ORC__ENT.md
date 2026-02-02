FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/07__MUS__LYRIC_EDITOR__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.ORC.MUS.LYRIC_EDITOR.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_LYRIC_EDITOR
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MUS.LYRIC_EDITOR.001

## [M] PURPOSE
Доводит текст до LYRICS_FINAL: ритм, рифма, ясность, повторяемость хука, смысл без провалов.
Жёстко убирает восклицательные знаки и приводит пунктуацию к политике.

## [M] INPUTS / OUTPUTS
- Inputs: [LYRICS_DRAFT, LYRIC_BRIEF]
- Outputs: [LYRICS_FINAL, EDIT_NOTES, FAIL_CODE?]

## [M] CORE_RULES
- Не менять смысловую ось без причины.
- Улучшать читабельность и “пение-в-голове”.
- Пунктуация: без "!" и без строк, начинающихся с "!".

## [M] GATES
- PASS: текст готов к генерации/записи
- FAIL: конфликт структуры или запретов

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Handoff: LYRICS_FINAL -> PROMPT_PACKAGER / QA_CHECKS / TRACK_TEST_DOC_GATE

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
