FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/13__MUS__QA_CHECKS__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.ORC.MUS.QA_CHECKS.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_QA_CHECKS
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MUS.QA_CHECKS.001

## [M] PURPOSE
Проводит QA чеклист: соответствие стиля, текстовые правила, отсутствие запрещённого, готовность к релизу, консистентность метаданных.
Даёт QA_REPORT с PASS/FAIL и списком фиксов.

## [M] INPUTS / OUTPUTS
- Inputs: [MUS_BRIEF, STYLE_ROUTE_TOKEN, LYRICS_FINAL, PROMPT_PACK, METADATA_PACK?]
- Outputs: [QA_REPORT, FAIL_CODE?]

## [M] QA_CHECKLIST (minimum)
- No RAW outside index manifests
- No repo edits in MODE REPO
- Lyrics: no exclamation, banned list respected
- Prompt pack completeness
- Naming consistency (artist/album/track)
- Ready for test doc gate

## [M] GATES
- PASS: нарушений нет
- FAIL: есть нарушения и они перечислены как REQUIRED_FIXES

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [CTL]
- Handoff: QA_REPORT -> TRACK_TEST_DOC_GATE / RELEASE_PACK

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
