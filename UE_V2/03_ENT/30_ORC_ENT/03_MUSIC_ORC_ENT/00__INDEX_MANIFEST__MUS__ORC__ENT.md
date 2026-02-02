FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/00__INDEX_MANIFEST__MUS__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.IDX.MUS_ORC_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — адресная таблица реалма 03_MUSIC_ORC_ENT.
Хранит KEYS, короткий смысл, RAW и PATH (как справка). Без длинных историй.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- Коротко: 1–2 строки смысла. Без лирики.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT
- FOLDER_NAME: 03_MUSIC_ORC_ENT
- INDEX_SCOPE_TAGS: [ENT, ORC, MUSIC]

## [M] ENTRY_SCHEMA (v1)
- KEY: <UNIQUE_KEY>
  UID: <OPTIONAL_UID>
  KIND: FILE|FOLDER|ENTITY|PIPE|KB|REG|XREF|LOG|STD|LAW|TPL
  ROLE: <ONE_LINE_ROLE>
  DESC: <ONE_LINE_DESC>
  RAW: <RAW_URL_OR_EMPTY>
  PATH: <REPO_PATH_OR_EMPTY>
  MARKERS: [MUST_LOAD, ROUTER, NAV, ...]
  STATUS: ACTIVE|DRAFT|DEPRECATED
  OWNER: SYS|RUNTIME|USER|<TEAM>
  UPDATED: 0000-00-00

---

## [M] ENTRIES

### [M] SELF
- KEY: SELF
  UID: UE.V2.ENT.IDX.MUS_ORC_ENT.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 03_MUSIC_ORC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/00__INDEX_MANIFEST__MUS__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/00__INDEX_MANIFEST__MUS__ORC__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.IDX.MUS_ORC_ENT.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for 03_MUSIC_ORC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/00__INDEX_MANIFEST__MUS__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/00__INDEX_MANIFEST__MUS__ORC__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.PIPE.MUS_ORC_ENT.001
  KIND: PIPE
  ROLE: Navigator for realm actions
  DESC: Uses KEYS, resolves RAW via INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/00__PIPELINE_CONTRACT__MUS__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/00__PIPELINE_CONTRACT__MUS__ORC__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

### [O] MUSIC ORC ENT (modules)
- KEY: MUS.PUBLIC_DOMAIN_SOURCE_PICKER
  UID:
  KIND: FILE
  ROLE: Public domain source picker
  DESC: Selects legal/allowed reference sources for music briefs and metadata
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/01__MUS__PUBLIC_DOMAIN_SOURCE_PICKER__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/01__MUS__PUBLIC_DOMAIN_SOURCE_PICKER__ORC__ENT.md
  MARKERS: [MUS, SOURCE, KB]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: MUS.GENRE_STYLE_ROUTER
  UID:
  KIND: FILE
  ROLE: Genre/style router
  DESC: Routes by genre, mood, tempo and assigns style constraints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/02__MUS__GENRE_STYLE_ROUTER__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/02__MUS__GENRE_STYLE_ROUTER__ORC__ENT.md
  MARKERS: [MUS, ROUTER]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: MUS.GROUP_TO_ALBUM
  UID:
  KIND: FILE
  ROLE: Group-to-album mapper
  DESC: Maps artist/group identity into album concept and positioning
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/03__MUS__GROUP_TO_ALBUM__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/03__MUS__GROUP_TO_ALBUM__ORC__ENT.md
  MARKERS: [MUS, ALBUM]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: MUS.ALBUM_TO_TRACK
  UID:
  KIND: FILE
  ROLE: Album-to-track planner
  DESC: Breaks album concept into track plan, variants and slot rules
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/04__MUS__ALBUM_TO_TRACK__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/04__MUS__ALBUM_TO_TRACK__ORC__ENT.md
  MARKERS: [MUS, TRACK, PLAN]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: MUS.LYRIC_BRIEF_FACTORY
  UID:
  KIND: FILE
  ROLE: Lyric brief factory
  DESC: Produces structured lyric brief: theme, POV, imagery, banned items, constraints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/05__MUS__LYRIC_BRIEF_FACTORY__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/05__MUS__LYRIC_BRIEF_FACTORY__ORC__ENT.md
  MARKERS: [MUS, LYRICS, BRIEF]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: MUS.LYRIC_DRAFTER
  UID:
  KIND: FILE
  ROLE: Lyric drafter
  DESC: Drafts lyrics from brief; builds verses/chorus/bridge with structure rules
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/06__MUS__LYRIC_DRAFTER__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/06__MUS__LYRIC_DRAFTER__ORC__ENT.md
  MARKERS: [MUS, LYRICS, DRAFT]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: MUS.LYRIC_EDITOR
  UID:
  KIND: FILE
  ROLE: Lyric editor
  DESC: Tightens lyrics: meter, rhyme, repetition, clarity; enforces no-exclamation rule
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/07__MUS__LYRIC_EDITOR__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/07__MUS__LYRIC_EDITOR__ORC__ENT.md
  MARKERS: [MUS, LYRICS, EDIT]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: MUS.PROMPT_PACKAGER
  UID:
  KIND: FILE
  ROLE: Prompt packager
  DESC: Packages prompts for generation tools (music/video) using final brief + constraints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/08__MUS__PROMPT_PACKAGER__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/08__MUS__PROMPT_PACKAGER__ORC__ENT.md
  MARKERS: [MUS, PROMPT, OUTPUT]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: MUS.TRACK_BUILD_STEP
  UID:
  KIND: FILE
  ROLE: Track build step runner
  DESC: Controls iterative generation steps for track build (draft→revise→final)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/09__MUS__TRACK_BUILD_STEP__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/09__MUS__TRACK_BUILD_STEP__ORC__ENT.md
  MARKERS: [MUS, STEP, RUN]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: MUS.HOOK_FOCUS_LOOP
  UID:
  KIND: FILE
  ROLE: Hook focus loop
  DESC: Iterates hook to maximize catchiness; keeps constraints stable
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/10__MUS__HOOK_FOCUS_LOOP__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/10__MUS__HOOK_FOCUS_LOOP__ORC__ENT.md
  MARKERS: [MUS, HOOK, LOOP]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: MUS.MIX_FOCUS_LOOP
  UID:
  KIND: FILE
  ROLE: Mix focus loop
  DESC: Iterates mix targets (balance, energy, loudness) and stabilizes result
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/11__MUS__MIX_FOCUS_LOOP__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/11__MUS__MIX_FOCUS_LOOP__ORC__ENT.md
  MARKERS: [MUS, MIX, LOOP]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: MUS.LYRICS_FOCUS_LOOP
  UID:
  KIND: FILE
  ROLE: Lyrics focus loop
  DESC: Iterates lyrics for meaning, flow, imagery; checks banned items and clarity
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/12__MUS__LYRICS_FOCUS_LOOP__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/12__MUS__LYRICS_FOCUS_LOOP__ORC__ENT.md
  MARKERS: [MUS, LYRICS, LOOP]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: MUS.QA_CHECKS
  UID:
  KIND: FILE
  ROLE: QA checks for music artifacts
  DESC: Runs checklist: structure, lyric rules, metadata completeness, packaging
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/13__MUS__QA_CHECKS__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/13__MUS__QA_CHECKS__ORC__ENT.md
  MARKERS: [MUS, QA, GATE]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: MUS.TRACK_TEST_DOC_GATE
  UID:
  KIND: FILE
  ROLE: Track test doc gate
  DESC: Produces/validates test doc before release; blocks missing evidence
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/14__MUS__TRACK_TEST_DOC_GATE__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/14__MUS__TRACK_TEST_DOC_GATE__ORC__ENT.md
  MARKERS: [MUS, TEST, GATE]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: MUS.METADATA_FACTORY
  UID:
  KIND: FILE
  ROLE: Metadata factory
  DESC: Builds metadata: title, artist, album, release notes, tags, credits
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/15__MUS__METADATA_FACTORY__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/15__MUS__METADATA_FACTORY__ORC__ENT.md
  MARKERS: [MUS, META]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: MUS.IDENTITY_BUILD
  UID:
  KIND: FILE
  ROLE: Identity build for music releases
  DESC: Builds artist identity tokens and mapping for album/track packaging
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/16__MUS__IDENTITY_BUILD__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/16__MUS__IDENTITY_BUILD__ORC__ENT.md
  MARKERS: [MUS, ID]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: MUS.MERGE_SYNTHESIS
  UID:
  KIND: FILE
  ROLE: Merge synthesis
  DESC: Merges best parts from variants into final track/lyrics/metadata pack
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/17__MUS__MERGE_SYNTHESIS__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/17__MUS__MERGE_SYNTHESIS__ORC__ENT.md
  MARKERS: [MUS, MERGE]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: MUS.RELEASE_ASSEMBLER
  UID:
  KIND: FILE
  ROLE: Release assembler
  DESC: Assembles release artifact: audio targets, lyrics, metadata, credits
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/18__MUS__RELEASE_ASSEMBLER__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/18__MUS__RELEASE_ASSEMBLER__ORC__ENT.md
  MARKERS: [MUS, RELEASE]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: MUS.RELEASE_PACK
  UID:
  KIND: FILE
  ROLE: Release pack
  DESC: Final packaging into OUTPUT_PACK, upload notes and distribution checklist
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/19__MUS__RELEASE_PACK__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/19__MUS__RELEASE_PACK__ORC__ENT.md
  MARKERS: [MUS, OUTPUT, PACK]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: MUS.PORTFOLIO_PLANNER
  UID:
  KIND: FILE
  ROLE: Portfolio planner
  DESC: Plans release portfolio: series, cadence, themes, and diversification
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/20__MUS__PORTFOLIO_PLANNER__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/20__MUS__PORTFOLIO_PLANNER__ORC__ENT.md
  MARKERS: [MUS, PLAN]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

### [O] LEGACY (back-compat)
- KEY: LEGACY.POET_PACK_ORC_ENT
  UID:
  KIND: FILE
  ROLE: Legacy poet pack
  DESC: Back-compat pack for old lyric/poet flow
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/90__LEGACY__POET_PACK__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/90__LEGACY__POET_PACK__ORC__ENT.md
  MARKERS: [LEGACY]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02
