FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/06__MUS__LYRIC_DRAFTER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.ORC.MUS.LYRIC_DRAFTER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_LYRIC_DRAFTER
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MUS.LYRIC_DRAFTER.001

## [M] PURPOSE
Пишет LYRICS_DRAFT по LYRIC_BRIEF: куплеты/припев/бридж по структуре, с сохранением тона и хука.
Не использует восклицательные знаки.

## [M] INPUTS / OUTPUTS
- Inputs: [LYRIC_BRIEF]
- Outputs: [LYRICS_DRAFT, FAIL_CODE?]

## [M] CORE_RULES
- Соблюдать структуру и длину строк.
- Избегать запретных слов и прямых цитат.
- Хук должен быть узнаваемым, но не навязчивым.

## [M] GATES
- PASS: draft соответствует brief
- FAIL: невозможно соблюсти ограничения без уточнения

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Handoff: LYRICS_DRAFT -> LYRIC_EDITOR / LYRICS_FOCUS_LOOP

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
