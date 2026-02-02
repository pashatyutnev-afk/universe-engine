FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/20__MUS__PORTFOLIO_PLANNER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.ORC.MUS.PORTFOLIO_PLANNER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_PORTFOLIO_PLANNER
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MUS.PORTFOLIO_PLANNER.001

## [M] PURPOSE
Планирует портфель релизов: серии, темп выпуска, распределение жанров/настроений, правила “чтобы не было каши”.
Не назначает даты как факт, если не задано.

## [M] INPUTS / OUTPUTS
- Inputs: [ARTIST_ID_TOKEN, PAST_RELEASES_HINT?]
- Outputs: [PORTFOLIO_PLAN_TOKEN, FAIL_CODE?]

## [M] GATES
- PASS: план структурный и реалистичный
- FAIL: нет входов (что за проект, какие цели)

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [CTL]
- Handoff: plan -> GROUP_TO_ALBUM / ALBUM_TO_TRACK

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
