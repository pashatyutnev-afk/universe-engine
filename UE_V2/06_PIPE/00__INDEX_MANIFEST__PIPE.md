FILE: UE_V2/06_PIPE/00__INDEX_MANIFEST__PIPE.md
SCOPE: UE_V2 / 06_PIPE
DOC_TYPE: INDEX_MANIFEST
DOMAIN: PIPE
UID: UE.V2.PIPE.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма 06_PIPE.
Хранит RAW и машинные паспорта пайплайнов и контрольных цепочек (CTL/VAL/QA/REL).
Никаких “историй” и длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Любая навигация по 06_PIPE выполняется через KEY → RAW.
- PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/06_PIPE
- FOLDER_NAME: 06_PIPE
- INDEX_SCOPE_TAGS: [PIPE, SYS, ROUTER]

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
  UID: UE.V2.PIPE.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 06_PIPE
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/06_PIPE/00__INDEX_MANIFEST__PIPE.md
  PATH: UE_V2/06_PIPE/00__INDEX_MANIFEST__PIPE.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.PIPE.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for PIPE realm
  DESC: Raw addresses + short meaning for 06_PIPE
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/06_PIPE/00__INDEX_MANIFEST__PIPE.md
  PATH: UE_V2/06_PIPE/00__INDEX_MANIFEST__PIPE.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.PIPE.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: PIPE realm step-run navigator
  DESC: KEY-only contract; resolves targets via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/06_PIPE/00__PIPELINE_CONTRACT__PIPE.md
  PATH: UE_V2/06_PIPE/00__PIPELINE_CONTRACT__PIPE.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (pipelines and control chain)

- KEY: PIPE.DEFAULT
  UID:
  KIND: PIPE
  ROLE: Default pipeline router
  DESC: Default handoff router to domain pipelines
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/06_PIPE/01__PIPE_DEFAULT.md
  PATH: UE_V2/06_PIPE/01__PIPE_DEFAULT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPE.GAP
  UID:
  KIND: PIPE
  ROLE: Gap handling pipeline
  DESC: GAP workflow and required artifacts to close gaps
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/06_PIPE/02__PIPE_GAP.md
  PATH: UE_V2/06_PIPE/02__PIPE_GAP.md
  MARKERS: [PIPE, GAP]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPE.AUD
  UID:
  KIND: PIPE
  ROLE: Audio domain pipeline
  DESC: Domain pipeline for AUD tasks
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/06_PIPE/03__PIPE_AUD.md
  PATH: UE_V2/06_PIPE/03__PIPE_AUD.md
  MARKERS: [PIPE, DOM, AUD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPE.VIS
  UID:
  KIND: PIPE
  ROLE: Visual domain pipeline
  DESC: Domain pipeline for VIS tasks
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/06_PIPE/04__PIPE_VIS.md
  PATH: UE_V2/06_PIPE/04__PIPE_VIS.md
  MARKERS: [PIPE, DOM, VIS]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPE.LOR
  UID:
  KIND: PIPE
  ROLE: Lore domain pipeline
  DESC: Domain pipeline for LOR tasks
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/06_PIPE/05__PIPE_LOR.md
  PATH: UE_V2/06_PIPE/05__PIPE_LOR.md
  MARKERS: [PIPE, DOM, LOR]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: CTL.READINESS
  UID:
  KIND: PIPE
  ROLE: Controller readiness gate
  DESC: Readiness checks before validation and QA
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/06_PIPE/06__CTL_READINESS.md
  PATH: UE_V2/06_PIPE/06__CTL_READINESS.md
  MARKERS: [CTL, GATE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: CTL.NOISE
  UID:
  KIND: PIPE
  ROLE: Controller noise gate
  DESC: Anti-noise checks and minimality enforcement
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/06_PIPE/07__CTL_NOISE.md
  PATH: UE_V2/06_PIPE/07__CTL_NOISE.md
  MARKERS: [CTL, GATE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: VAL.DOC
  UID:
  KIND: PIPE
  ROLE: Document validation
  DESC: Validates doc structure, headers, markers, traceability
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/06_PIPE/08__VAL_DOC.md
  PATH: UE_V2/06_PIPE/08__VAL_DOC.md
  MARKERS: [VAL, DOC]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: VAL.AUD
  UID:
  KIND: PIPE
  ROLE: Audio validation
  DESC: Validates audio domain artifacts and gates
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/06_PIPE/09__VAL_AUD.md
  PATH: UE_V2/06_PIPE/09__VAL_AUD.md
  MARKERS: [VAL, AUD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: VAL.VIS
  UID:
  KIND: PIPE
  ROLE: Visual validation
  DESC: Validates visual domain artifacts and gates
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/06_PIPE/10__VAL_VIS.md
  PATH: UE_V2/06_PIPE/10__VAL_VIS.md
  MARKERS: [VAL, VIS]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: QA.ACCEPT
  UID:
  KIND: PIPE
  ROLE: QA acceptance gate
  DESC: Final acceptance decision and sign-off prerequisites
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/06_PIPE/11__QA_ACCEPT.md
  PATH: UE_V2/06_PIPE/11__QA_ACCEPT.md
  MARKERS: [QA, GATE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: QA.PACK
  UID:
  KIND: PIPE
  ROLE: QA packaging check
  DESC: Ensures output pack completeness and pointers
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/06_PIPE/12__QA_PACK.md
  PATH: UE_V2/06_PIPE/12__QA_PACK.md
  MARKERS: [QA, OUTPUT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: REL.SIGNOFF
  UID:
  KIND: PIPE
  ROLE: Release signoff
  DESC: Release finalization and publication signoff
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/06_PIPE/13__SIGNOFF.md
  PATH: UE_V2/06_PIPE/13__SIGNOFF.md
  MARKERS: [REL, SIGNOFF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPE.REL
  UID:
  KIND: PIPE
  ROLE: Release pipeline
  DESC: Release pipeline orchestration
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/06_PIPE/14__PIPE_REL.md
  PATH: UE_V2/06_PIPE/14__PIPE_REL.md
  MARKERS: [PIPE, REL]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPE.STEP_RUN
  UID:
  KIND: PIPE
  ROLE: Step-run meta pipeline
  DESC: Step-run execution discipline pipeline
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/06_PIPE/15__PIPE_STEP_RUN.md
  PATH: UE_V2/06_PIPE/15__PIPE_STEP_RUN.md
  MARKERS: [PIPE, STEP_RUN]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPE.FOCUS_LOOP
  UID:
  KIND: PIPE
  ROLE: Focus loop pipeline
  DESC: Focus loop discipline and iteration control
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/06_PIPE/16__PIPE_FOCUS_LOOP.md
  PATH: UE_V2/06_PIPE/16__PIPE_FOCUS_LOOP.md
  MARKERS: [PIPE, FOCUS]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: VAL.CHAIN_COMPLETENESS
  UID:
  KIND: PIPE
  ROLE: Validation chain completeness
  DESC: Ensures CTL->VAL->QA chain completeness across artifacts
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/06_PIPE/17__VAL_CHAIN_COMPLETENESS.md
  PATH: UE_V2/06_PIPE/17__VAL_CHAIN_COMPLETENESS.md
  MARKERS: [VAL, CHAIN]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: CTL.COVERAGE_GATE
  UID:
  KIND: PIPE
  ROLE: Coverage gate
  DESC: Coverage requirements gate for tasks and artifacts
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/06_PIPE/18__CTL_COVERAGE_GATE.md
  PATH: UE_V2/06_PIPE/18__CTL_COVERAGE_GATE.md
  MARKERS: [CTL, COVERAGE, GATE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPE.MUSIC.TRACK
  UID:
  KIND: PIPE
  ROLE: Music track pipeline
  DESC: Pipeline for producing a music track artifact
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/06_PIPE/20__PIPE_MUSIC_TRACK.md
  PATH: UE_V2/06_PIPE/20__PIPE_MUSIC_TRACK.md
  MARKERS: [PIPE, MUSIC]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPE.MUSIC.LYRICS
  UID:
  KIND: PIPE
  ROLE: Music lyrics pipeline
  DESC: Pipeline for producing lyrics artifact
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/06_PIPE/21__PIPE_MUSIC_LYRICS.md
  PATH: UE_V2/06_PIPE/21__PIPE_MUSIC_LYRICS.md
  MARKERS: [PIPE, MUSIC, TEXT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPE.MUSIC.IDENTITY
  UID:
  KIND: PIPE
  ROLE: Music identity pipeline
  DESC: Pipeline for artist/project identity artifacts
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/06_PIPE/22__PIPE_MUSIC_IDENTITY.md
  PATH: UE_V2/06_PIPE/22__PIPE_MUSIC_IDENTITY.md
  MARKERS: [PIPE, MUSIC, IDENTITY]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31
