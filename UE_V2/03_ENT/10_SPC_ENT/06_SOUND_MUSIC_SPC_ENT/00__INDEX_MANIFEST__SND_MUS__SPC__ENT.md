FILE: UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/00__INDEX_MANIFEST__SND_MUS__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 06_SOUND_MUSIC_SPC_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: SND_MUS_SPC
UID: UE.V2.ENT.SPC.SND_MUS.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма SOUND_MUSIC_SPC_ENT.
Хранит RAW и машинные паспорта sound/music-специалистов (SND_MUS). Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- Коротко: 1–2 строки смысла. Без лирики.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT
- FOLDER_NAME: 06_SOUND_MUSIC_SPC_ENT
- INDEX_SCOPE_TAGS: [ENT, SPC, SND, MUSIC]

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

## [M] ENTRIES

### [M] SELF
- KEY: SELF
  UID: UE.V2.ENT.SPC.SND_MUS.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for SOUND_MUSIC_SPC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/00__INDEX_MANIFEST__SND_MUS__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/00__INDEX_MANIFEST__SND_MUS__SPC__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.SPC.SND_MUS.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for SOUND_MUSIC_SPC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/00__INDEX_MANIFEST__SND_MUS__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/00__INDEX_MANIFEST__SND_MUS__SPC__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.SPC.SND_MUS.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Realm step-run navigator
  DESC: KEY-only contract; resolves targets via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/00__PIPELINE_CONTRACT__SND_MUS__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/00__PIPELINE_CONTRACT__SND_MUS__SPC__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (sound/music specialists)

- KEY: SPC.SND_MUS.MUSIC_SUPERVISOR
  UID:
  KIND: ENTITY
  ROLE: Music supervisor
  DESC: Owns music direction across project; selects musical strategy and final approvals
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/01__SND_MUS__MUSIC_SUPERVISOR__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/01__SND_MUS__MUSIC_SUPERVISOR__SPC__ENT.md
  MARKERS: [SPC, SND, MUSIC, SPECIALIST, DIR]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.SND_MUS.MUSIC_PRODUCER
  UID:
  KIND: ENTITY
  ROLE: Music producer
  DESC: Produces track-level production plan; coordinates composition/arrangement/vocals; drives deliverables
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/02__SND_MUS__MUSIC_PRODUCER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/02__SND_MUS__MUSIC_PRODUCER__SPC__ENT.md
  MARKERS: [SPC, SND, MUSIC, SPECIALIST, PROD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.SND_MUS.COMPOSER
  UID:
  KIND: ENTITY
  ROLE: Composer
  DESC: Composes music materials and themes; outputs composition drafts aligned to brief
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/03__SND_MUS__COMPOSER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/03__SND_MUS__COMPOSER__SPC__ENT.md
  MARKERS: [SPC, SND, MUSIC, SPECIALIST, COMP]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.SND_MUS.SONGWRITER
  UID:
  KIND: ENTITY
  ROLE: Songwriter
  DESC: Writes song structure, hooks, toplines; outputs song drafts and variations
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/04__SND_MUS__SONGWRITER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/04__SND_MUS__SONGWRITER__SPC__ENT.md
  MARKERS: [SPC, SND, MUSIC, SPECIALIST, SONG]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.SND_MUS.LYRICIST
  UID:
  KIND: ENTITY
  ROLE: Lyricist
  DESC: Writes lyrics aligned to tone and meaning; outputs lyric drafts and revisions
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/05__SND_MUS__LYRICIST__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/05__SND_MUS__LYRICIST__SPC__ENT.md
  MARKERS: [SPC, SND, MUSIC, SPECIALIST, TEXT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.SND_MUS.ARRANGER
  UID:
  KIND: ENTITY
  ROLE: Arranger
  DESC: Designs arrangement and instrumentation; outputs arrangement plan and stems spec
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/06__SND_MUS__ARRANGER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/06__SND_MUS__ARRANGER__SPC__ENT.md
  MARKERS: [SPC, SND, MUSIC, SPECIALIST, ARR]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.SND_MUS.VOCAL_DIRECTOR
  UID:
  KIND: ENTITY
  ROLE: Vocal director
  DESC: Directs vocal performance and delivery; outputs vocal notes and takes selection criteria
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/07__SND_MUS__VOCAL_DIRECTOR__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/07__SND_MUS__VOCAL_DIRECTOR__SPC__ENT.md
  MARKERS: [SPC, SND, MUSIC, SPECIALIST, VOC]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.SND_MUS.SOUND_DESIGNER
  UID:
  KIND: ENTITY
  ROLE: Sound designer
  DESC: Designs sound layer and FX; outputs sound design spec and asset list
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/08__SND_MUS__SOUND_DESIGNER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/08__SND_MUS__SOUND_DESIGNER__SPC__ENT.md
  MARKERS: [SPC, SND, MUSIC, SPECIALIST, SFX]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.SND_MUS.MIX_ENGINEER
  UID:
  KIND: ENTITY
  ROLE: Mix engineer
  DESC: Produces mix strategy and revisions; outputs MIX_TOKEN and mix notes
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/09__SND_MUS__MIX_ENGINEER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/09__SND_MUS__MIX_ENGINEER__SPC__ENT.md
  MARKERS: [SPC, SND, MUSIC, SPECIALIST, MIX]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.SND_MUS.MASTERING_ENGINEER
  UID:
  KIND: ENTITY
  ROLE: Mastering engineer
  DESC: Produces mastering targets and revisions; outputs MASTER_TOKEN and acceptance notes
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/10__SND_MUS__MASTERING_ENGINEER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/10__SND_MUS__MASTERING_ENGINEER__SPC__ENT.md
  MARKERS: [SPC, SND, MUSIC, SPECIALIST, MASTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.SND_MUS.AUDIO_QA
  UID:
  KIND: ENTITY
  ROLE: Audio QA
  DESC: Runs QA checks and acceptance criteria; outputs QA_PASS/FAIL with issues list
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/11__SND_MUS__AUDIO_QA__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/11__SND_MUS__AUDIO_QA__SPC__ENT.md
  MARKERS: [SPC, SND, MUSIC, SPECIALIST, QA]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.SND_MUS.PROMPT_ARCHITECT
  UID:
  KIND: ENTITY
  ROLE: Prompt architect (music)
  DESC: Designs prompt strategy for music generation; outputs prompt packs and constraints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/12__SND_MUS__PROMPT_ARCHITECT__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/12__SND_MUS__PROMPT_ARCHITECT__SPC__ENT.md
  MARKERS: [SPC, SND, MUSIC, SPECIALIST, PROMPT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.SND_MUS.UGC_DIRECTOR
  UID:
  KIND: ENTITY
  ROLE: UGC director
  DESC: Designs UGC-ready constraints and cutdowns; outputs UGC pack and variations policy
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/13__SND_MUS__UGC_DIRECTOR__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/13__SND_MUS__UGC_DIRECTOR__SPC__ENT.md
  MARKERS: [SPC, SND, MUSIC, SPECIALIST, UGC]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.SND_MUS.EARWORM_DIRECTOR
  UID:
  KIND: ENTITY
  ROLE: Earworm director
  DESC: Optimizes hooks and repeatability; outputs hook strategy and tests checklist
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/14__SND_MUS__EARWORM_DIRECTOR__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/14__SND_MUS__EARWORM_DIRECTOR__SPC__ENT.md
  MARKERS: [SPC, SND, MUSIC, SPECIALIST, HOOK]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.SND_MUS.GENRE_FUSION_ARCHITECT
  UID:
  KIND: ENTITY
  ROLE: Genre fusion architect
  DESC: Designs hybrid genre blends and rules; outputs fusion map + constraints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/15__SND_MUS__GENRE_FUSION_ARCHITECT__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/15__SND_MUS__GENRE_FUSION_ARCHITECT__SPC__ENT.md
  MARKERS: [SPC, SND, MUSIC, SPECIALIST, GENRE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.SND_MUS.TREND_ENGINEER
  UID:
  KIND: ENTITY
  ROLE: Trend engineer
  DESC: Tracks trends and converts into constraints; outputs trend snapshot and adaptation suggestions
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/16__SND_MUS__TREND_ENGINEER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/16__SND_MUS__TREND_ENGINEER__SPC__ENT.md
  MARKERS: [SPC, SND, MUSIC, SPECIALIST, TREND]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.SND_MUS.POET_JUICE_EDITOR
  UID:
  KIND: ENTITY
  ROLE: Poet-juice editor
  DESC: Optimizes lyric punch and density; outputs edit notes and alternative lines pack
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/17__SND_MUS__POET_JUICE_EDITOR__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/17__SND_MUS__POET_JUICE_EDITOR__SPC__ENT.md
  MARKERS: [SPC, SND, MUSIC, SPECIALIST, TEXT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.SND_MUS.MOSAIC_EDITOR
  UID:
  KIND: ENTITY
  ROLE: Mosaic editor
  DESC: Designs montage/mosaic editing approach for music cuts; outputs mosaic structure and transitions
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/18__SND_MUS__MOSAIC_EDITOR__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/18__SND_MUS__MOSAIC_EDITOR__SPC__ENT.md
  MARKERS: [SPC, SND, MUSIC, SPECIALIST, EDIT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.SND_MUS.ALBUM_SHOWRUNNER
  UID:
  KIND: ENTITY
  ROLE: Album showrunner
  DESC: Owns album-level cohesion; defines arc, pacing, and release-ready order; outputs album run sheet
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/19__SND_MUS__ALBUM_SHOWRUNNER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/19__SND_MUS__ALBUM_SHOWRUNNER__SPC__ENT.md
  MARKERS: [SPC, SND, MUSIC, SPECIALIST, ALBUM]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.SND_MUS.GROUP_CREATIVE_DIRECTOR
  UID:
  KIND: ENTITY
  ROLE: Group creative director
  DESC: Owns group identity across releases; outputs identity constraints and coherence checks
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/20__SND_MUS__GROUP_CREATIVE_DIRECTOR__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/06_SOUND_MUSIC_SPC_ENT/20__SND_MUS__GROUP_CREATIVE_DIRECTOR__SPC__ENT.md
  MARKERS: [SPC, SND, MUSIC, SPECIALIST, ID]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31
