FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/00__PIPELINE_CONTRACT__MUS__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.PIPE.MUS_ORC_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: Contract has no RAW

---

## [M] PURPOSE
MUSIC PIPELINE_CONTRACT — раннер музыкальной оркестрации: brief -> genre/style -> group/album/track plan -> lyrics build loops -> QA -> release pack.
Работает через KEY и резолвит адреса в INDEX_MANIFEST. RAW внутри контракта запрещён.

## [M] HARD_RULES
- RAW запрещён внутри CONTRACT.
- Все ссылки и маршруты: KEY -> INDEX_MANIFEST -> open.
- MODE REPO: никаких правок репозитория.
- STEP-RUN: один шаг = одна пачка действий, затем NEXT_PROMPT.
- Любой шаг завершать NEXT_PROMPT: "го" или FAIL_CODE.
- Для текстов песен: не использовать восклицательные знаки, заменять на точку/тире/многоточие.

## [M] REQUIRED_KEYS (must exist in INDEX_MANIFEST)
- INDEX_MANIFEST
- PIPELINE_CONTRACT
- MUS.PUBLIC_DOMAIN_SOURCE_PICKER
- MUS.GENRE_STYLE_ROUTER
- MUS.GROUP_TO_ALBUM
- MUS.ALBUM_TO_TRACK
- MUS.LYRIC_BRIEF_FACTORY
- MUS.LYRIC_DRAFTER
- MUS.LYRIC_EDITOR
- MUS.PROMPT_PACKAGER
- MUS.TRACK_BUILD_STEP
- MUS.HOOK_FOCUS_LOOP
- MUS.MIX_FOCUS_LOOP
- MUS.LYRICS_FOCUS_LOOP
- MUS.QA_CHECKS
- MUS.TRACK_TEST_DOC_GATE
- MUS.METADATA_FACTORY
- MUS.IDENTITY_BUILD
- MUS.MERGE_SYNTHESIS
- MUS.RELEASE_ASSEMBLER
- MUS.RELEASE_PACK
- MUS.PORTFOLIO_PLANNER
- LEGACY.POET_PACK_ORC_ENT

## [M] CONTRACT_HEADER
- REALM_ID: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT
- DOMAIN: MUS_ORC_ENT
- ARTIFACT_TYPES: [MUS_BRIEF, STYLE_TOKEN, ALBUM_TOKEN, TRACK_PLAN, LYRIC_BRIEF, LYRICS_DRAFT, LYRICS_FINAL, PROMPT_PACK, QA_REPORT, TEST_DOC_TOKEN, METADATA_PACK, RELEASE_ASSET_TOKEN, OUTPUT_PACK]
- DEFAULT_MODE: RELEASE_READY

## [M] STEP-RUN (canonical)
- STEP: S
  GOAL:
  INPUTS: []
  TARGETS: []
  ACTIONS:
    -
  OUTPUTS: []
  CHECKS: []
  FAIL:
  NEXT: "го"

## [M] STEPS (music flow)
- STEP: S0
  GOAL: Normalize task into MUS_BRIEF and constraints lock
  INPUTS: [TASK_TEXT, MODE_HINT?]
  TARGETS: []
  ACTIONS:
    - Extract: target (single track / EP / album / playlist), mood, language, duration, vocal type, forbidden topics
    - Lock constraints into MUS_CONSTRAINTS_LOCK
  OUTPUTS: [MUS_BRIEF, MUS_CONSTRAINTS_LOCK, EXEC_MODE]
  CHECKS: [TASK_PRESENT]
  FAIL: UE.FAIL.INPUT_ABSENT
  NEXT: "го"

- STEP: S1
  GOAL: Choose allowed reference sources and style route
  INPUTS: [MUS_BRIEF, MUS_CONSTRAINTS_LOCK]
  TARGETS: [MUS.PUBLIC_DOMAIN_SOURCE_PICKER, MUS.GENRE_STYLE_ROUTER]
  ACTIONS:
    - Produce SOURCE_POLICY_TOKEN (allowed references only)
    - Produce STYLE_ROUTE_TOKEN (genre, tempo band, energy, instrumentation rules)
  OUTPUTS: [SOURCE_POLICY_TOKEN, STYLE_ROUTE_TOKEN]
  CHECKS: [SOURCE_POLICY_OK, STYLE_ROUTE_OK]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

- STEP: S2
  GOAL: Build identity and plan album/track layout
  INPUTS: [MUS_BRIEF, STYLE_ROUTE_TOKEN]
  TARGETS: [MUS.IDENTITY_BUILD, MUS.GROUP_TO_ALBUM, MUS.ALBUM_TO_TRACK]
  ACTIONS:
    - Produce ARTIST_ID_TOKEN (naming, tone, credits conventions)
    - Produce ALBUM_TOKEN (concept, positioning, cover mood as principles)
    - Produce TRACK_PLAN (slots, titles placeholders, variations policy)
  OUTPUTS: [ARTIST_ID_TOKEN, ALBUM_TOKEN, TRACK_PLAN]
  CHECKS: [PLAN_OK]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

- STEP: S3
  GOAL: Build lyrics brief, draft, and edit to final
  INPUTS: [TRACK_PLAN, ALBUM_TOKEN, STYLE_ROUTE_TOKEN, MUS_CONSTRAINTS_LOCK]
  TARGETS: [MUS.LYRIC_BRIEF_FACTORY, MUS.LYRIC_DRAFTER, MUS.LYRIC_EDITOR]
  ACTIONS:
    - Produce LYRIC_BRIEF (POV, imagery, structure, banned list, rhyme policy)
    - Produce LYRICS_DRAFT
    - Produce LYRICS_FINAL (no exclamation, consistent meter, clear hook)
  OUTPUTS: [LYRIC_BRIEF, LYRICS_DRAFT, LYRICS_FINAL]
  CHECKS: [LYRICS_OK]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

- STEP: S4
  GOAL: Package prompts and run focus loops
  INPUTS: [STYLE_ROUTE_TOKEN, LYRICS_FINAL, MUS_BRIEF]
  TARGETS: [MUS.PROMPT_PACKAGER, MUS.HOOK_FOCUS_LOOP, MUS.MIX_FOCUS_LOOP, MUS.LYRICS_FOCUS_LOOP]
  ACTIONS:
    - Produce PROMPT_PACK (music gen prompts + constraints)
    - Optionally iterate hook/mix/lyrics within locked constraints
  OUTPUTS: [PROMPT_PACK, LOOP_NOTES?]
  CHECKS: [PROMPTS_OK]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

- STEP: S5
  GOAL: QA, test doc gate, metadata, release assembly and packaging
  INPUTS: [PROMPT_PACK, LYRICS_FINAL, TRACK_PLAN, ARTIST_ID_TOKEN]
  TARGETS: [MUS.QA_CHECKS, MUS.TRACK_TEST_DOC_GATE, MUS.METADATA_FACTORY, MUS.MERGE_SYNTHESIS, MUS.RELEASE_ASSEMBLER, MUS.RELEASE_PACK]
  ACTIONS:
    - QA checklist pass/fail
    - Produce TEST_DOC_TOKEN (evidence-ready)
    - Produce METADATA_PACK (titles, credits, tags)
    - Merge best variants if present
    - Assemble RELEASE_ASSET_TOKEN and final RELEASE_PACK_TOKEN
  OUTPUTS: [QA_REPORT, TEST_DOC_TOKEN, METADATA_PACK, RELEASE_PACK_TOKEN, OUTPUT_PACK]
  CHECKS: [FINAL_GATE]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

## [M] FAIL_CODES (local)
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.MISSING_KEY
- UE.FAIL.RULE_VIOLATION
- UE.FAIL.GATE_FAIL
- UE.FAIL.APPROVAL_REQUIRED

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
