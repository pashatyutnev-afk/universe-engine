FILE: UE_V2/03_ENT/20_ENG_ENT/07_PRODUCTIONFORMAT_ENG_ENT/00__INDEX_MANIFEST__PFT__ENG__ENT.md
SCOPE: UE_V2 / 03_ENT / 20_ENG_ENT / 07_PRODUCTIONFORMAT_ENG_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: PFT_ENG
UID: UE.V2.ENT.ENG.PFT.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма PRODUCTIONFORMAT_ENG_ENT (PFT).
Хранит RAW и машинные паспорта PFT-движков. Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Любая навигация по реалму: KEY -> resolve RAW here -> open.
- PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).
- NO GUESSING: для движков RAW заполняем только после фиксации кнопкой Raw (иначе GAP).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/20_ENG_ENT/07_PRODUCTIONFORMAT_ENG_ENT
- FOLDER_NAME: 07_PRODUCTIONFORMAT_ENG_ENT
- INDEX_SCOPE_TAGS: [ENT, ENG, PFT]

## [M] KEYSPACE
KEY_FORMAT: PFT.
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
  UID: UE.V2.ENT.ENG.PFT.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for PRODUCTIONFORMAT_ENG_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/07_PRODUCTIONFORMAT_ENG_ENT/00__INDEX_MANIFEST__PFT__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/07_PRODUCTIONFORMAT_ENG_ENT/00__INDEX_MANIFEST__PFT__ENG__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (minimum for realm)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.ENG.PFT.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for PFT engines
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/07_PRODUCTIONFORMAT_ENG_ENT/00__INDEX_MANIFEST__PFT__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/07_PRODUCTIONFORMAT_ENG_ENT/00__INDEX_MANIFEST__PFT__ENG__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.ENG.PFT.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Realm step-run navigator
  DESC: KEY-only contract; resolves targets via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/07_PRODUCTIONFORMAT_ENG_ENT/00__PIPELINE_CONTRACT__PFT__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/07_PRODUCTIONFORMAT_ENG_ENT/00__PIPELINE_CONTRACT__PFT__ENG__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (PFT engines)
# RULE: RAW for engines must be copied from each file “Raw” button (no guessing).
# Until RAW is fixed -> keep RAW empty and MARKERS include GAP.

 - KEY: PFT.GENRE
  UID:
  KIND: ENTITY
  ROLE: Genre selection engine
  DESC: Selects base genre constraints for production format; emits GENRE_SELECTION_TOKEN
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/07_PRODUCTIONFORMAT_ENG_ENT/01__PFT__GENRE__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/07_PRODUCTIONFORMAT_ENG_ENT/01__PFT__GENRE__ENG__ENT.md
  MARKERS: [ENG, PFT, GENRE]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-02-01

- KEY: PFT.GENRE_BLENDING
  UID:
  KIND: ENTITY
  ROLE: Genre blending engine
  DESC: Blends genres with constraints and risk flags; emits GENRE_BLEND_PACK
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/07_PRODUCTIONFORMAT_ENG_ENT/02__PFT__GENRE_BLENDING__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/07_PRODUCTIONFORMAT_ENG_ENT/02__PFT__GENRE_BLENDING__ENG__ENT.md
  MARKERS: [ENG, PFT, BLEND]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-02-01

- KEY: PFT.FORMAT_ADAPTATION
  UID:
  KIND: ENTITY
  ROLE: Format adaptation engine
  DESC: Adapts content to target format rules; emits FORMAT_ADAPTATION_PLAN
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/07_PRODUCTIONFORMAT_ENG_ENT/03__PFT__FORMAT_ADAPTATION__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/07_PRODUCTIONFORMAT_ENG_ENT/03__PFT__FORMAT_ADAPTATION__ENG__ENT.md
  MARKERS: [ENG, PFT, ADAPT]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-02-01

- KEY: PFT.BOOK_FORMAT
  UID:
  KIND: ENTITY
  ROLE: Book format engine
  DESC: Defines book structure constraints; emits BOOK_FORMAT_BLUEPRINT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/07_PRODUCTIONFORMAT_ENG_ENT/04__PFT__BOOK_FORMAT__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/07_PRODUCTIONFORMAT_ENG_ENT/04__PFT__BOOK_FORMAT__ENG__ENT.md
  MARKERS: [ENG, PFT, BOOK]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-02-01

- KEY: PFT.SERIES_EPISODE
  UID:
  KIND: ENTITY
  ROLE: Series/episode engine
  DESC: Defines episodic structure and pacing; emits SERIES_EPISODE_BLUEPRINT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/07_PRODUCTIONFORMAT_ENG_ENT/05__PFT__SERIES_EPISODE__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/07_PRODUCTIONFORMAT_ENG_ENT/05__PFT__SERIES_EPISODE__ENG__ENT.md
  MARKERS: [ENG, PFT, SERIES]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-02-01

- KEY: PFT.SHORT_CONTENT
  UID:
  KIND: ENTITY
  ROLE: Short content engine
  DESC: Defines short-form constraints and hook pacing; emits SHORT_CONTENT_BLUEPRINT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/07_PRODUCTIONFORMAT_ENG_ENT/06__PFT__SHORT_CONTENT__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/07_PRODUCTIONFORMAT_ENG_ENT/06__PFT__SHORT_CONTENT__ENG__ENT.md
  MARKERS: [ENG, PFT, SHORT]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-02-01

- KEY: PFT.YOUTUBE_LONGFORM
  UID:
  KIND: ENTITY
  ROLE: YouTube longform engine
  DESC: Defines longform YouTube structure and retention beats; emits YT_LONGFORM_BLUEPRINT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/07_PRODUCTIONFORMAT_ENG_ENT/07__PFT__YOUTUBE_LONGFORM__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/07_PRODUCTIONFORMAT_ENG_ENT/07__PFT__YOUTUBE_LONGFORM__ENG__ENT.md
  MARKERS: [ENG, PFT, YT, LONGFORM]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-02-01

- KEY: PFT.GAME_NARRATIVE
  UID:
  KIND: ENTITY
  ROLE: Game narrative engine
  DESC: Defines interactive narrative format rules; emits GAME_NARRATIVE_BLUEPRINT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/07_PRODUCTIONFORMAT_ENG_ENT/08__PFT__GAME_NARRATIVE__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/07_PRODUCTIONFORMAT_ENG_ENT/08__PFT__GAME_NARRATIVE__ENG__ENT.md
  MARKERS: [ENG, PFT, GAME]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-02-01

---

## [M] LOAD_HINTS
MIN_SET_KEYS:
- INDEX_MANIFEST
- PIPELINE_CONTRACT

OPTIONAL_KEYS:
- PFT.GENRE
- PFT.GENRE_BLENDING
- PFT.FORMAT_ADAPTATION
- PFT.BOOK_FORMAT
- PFT.SERIES_EPISODE
- PFT.SHORT_CONTENT
- PFT.YOUTUBE_LONGFORM
- PFT.GAME_NARRATIVE

## [M] GUARDS
STOP_IF:
- RAW missing for any MIN_SET_KEYS
GAP_IF:
- requested KEY not present in ENTRIES
- any engine RAW is empty
