FILE: UE_V2/03_ENT/20_ENG_ENT/13_POETCORPUS_ENG_ENT/00__INDEX_MANIFEST__PCR__ENG__ENT.md
SCOPE: UE_V2 / 03_ENT / 20_ENG_ENT / 13_POETCORPUS_ENG_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: PCR_ENG
UID: UE.V2.ENT.ENG.PCR.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма POETCORPUS_ENG_ENT (PCR).
Хранит RAW и машинные паспорта PCR-движков. Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Любая навигация по реалму: KEY -> resolve RAW here -> open.
- PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).
- NO GUESSING: для движков RAW заполняем только после фиксации кнопкой Raw (иначе GAP).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/20_ENG_ENT/13_POETCORPUS_ENG_ENT
- FOLDER_NAME: 13_POETCORPUS_ENG_ENT
- INDEX_SCOPE_TAGS: [ENT, ENG, PCR]

## [M] KEYSPACE
KEY_FORMAT: PCR.
RESOLUTION_RULE: KEY -> RAW берётся только из ENTRIES ниже

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
  UID: UE.V2.ENT.ENG.PCR.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for POETCORPUS_ENG_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/13_POETCORPUS_ENG_ENT/00__INDEX_MANIFEST__PCR__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/13_POETCORPUS_ENG_ENT/00__INDEX_MANIFEST__PCR__ENG__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (minimum for realm)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.ENG.PCR.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for PCR engines
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/13_POETCORPUS_ENG_ENT/00__INDEX_MANIFEST__PCR__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/13_POETCORPUS_ENG_ENT/00__INDEX_MANIFEST__PCR__ENG__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.ENG.PCR.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Realm step-run navigator
  DESC: KEY-only contract; resolves targets via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/13_POETCORPUS_ENG_ENT/00__PIPELINE_CONTRACT__PCR__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/13_POETCORPUS_ENG_ENT/00__PIPELINE_CONTRACT__PCR__ENG__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (PCR engines)
# RULE: RAW for engines must be copied from each file “Raw” button (no guessing).
# Until RAW is fixed -> keep RAW empty and MARKERS include GAP.

- KEY: PCR.PD_FILTER
  UID:
  KIND: ENTITY
  ROLE: Poetic density filter engine
  DESC: Filters corpus by poetic density / signal; emits FILTERED_CORPUS_TOKEN
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/13_POETCORPUS_ENG_ENT/01__PCR__PD_FILTER__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/13_POETCORPUS_ENG_ENT/01__PCR__PD_FILTER__ENG__ENT.md
  MARKERS: [ENG, PCR, FILTER]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-02-01

- KEY: PCR.POEM_FIT_SCORING
  UID:
  KIND: ENTITY
  ROLE: Poem fit scoring engine
  DESC: Scores candidates vs target mood/style/brief; emits POEM_FIT_SCORECARD
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/13_POETCORPUS_ENG_ENT/02__PCR__POEM_FIT_SCORING__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/13_POETCORPUS_ENG_ENT/02__PCR__POEM_FIT_SCORING__ENG__ENT.md
  MARKERS: [ENG, PCR, SCORE]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-02-01

- KEY: PCR.JUICE_EXTRACTOR
  UID:
  KIND: ENTITY
  ROLE: Juice extractor engine
  DESC: Extracts “poet juice” (hooks/lines/images); emits JUICE_PACK_TOKEN
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/13_POETCORPUS_ENG_ENT/03__PCR__JUICE_EXTRACTOR__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/13_POETCORPUS_ENG_ENT/03__PCR__JUICE_EXTRACTOR__ENG__ENT.md
  MARKERS: [ENG, PCR, EXTRACT]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-02-01

- KEY: PCR.MOSAIC_COMPOSER
  UID:
  KIND: ENTITY
  ROLE: Mosaic composer engine
  DESC: Composes mosaic from extracted fragments; emits MOSAIC_TEXT_PACK
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/13_POETCORPUS_ENG_ENT/04__PCR__MOSAIC_COMPOSER__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/13_POETCORPUS_ENG_ENT/04__PCR__MOSAIC_COMPOSER__ENG__ENT.md
  MARKERS: [ENG, PCR, COMPOSE]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-02-01

- KEY: PCR.EXCERPT_COLLISION
  UID:
  KIND: ENTITY
  ROLE: Excerpt collision engine
  DESC: Detects near-duplicates and collisions in excerpts; emits COLLISION_REPORT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/13_POETCORPUS_ENG_ENT/05__PCR__EXCERPT_COLLISION__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/13_POETCORPUS_ENG_ENT/05__PCR__EXCERPT_COLLISION__ENG__ENT.md
  MARKERS: [ENG, PCR, COLLISION]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-02-01

---

## [M] LOAD_HINTS
MIN_SET_KEYS:
- INDEX_MANIFEST
- PIPELINE_CONTRACT

OPTIONAL_KEYS:
- PCR.PD_FILTER
- PCR.POEM_FIT_SCORING
- PCR.JUICE_EXTRACTOR
- PCR.MOSAIC_COMPOSER
- PCR.EXCERPT_COLLISION

## [M] GUARDS
STOP_IF:
- RAW missing for any MIN_SET_KEYS
GAP_IF:
- requested KEY not present in ENTRIES
- any engine RAW not fixed yet (expected during build)
