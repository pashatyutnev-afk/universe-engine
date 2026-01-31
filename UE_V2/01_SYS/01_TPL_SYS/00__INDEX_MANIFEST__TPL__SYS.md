FILE: UE_V2/01_SYS/01_TPL_SYS/00__INDEX_MANIFEST__TPL__SYS.md
SCOPE: UE_V2 / 01_SYS / 01_TPL_SYS
DOC_TYPE: INDEX_MANIFEST
DOMAIN: TPL_SYS
UID: UE.V2.SYS.IDX.TPL_SYS.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — это “таблица адресов” и кратких смыслов для папки/реалма 01_TPL_SYS.
Хранит RAW и машинные паспорта элементов. Никаких “историй” и длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- Коротко: 1–2 строки смысла. Без лирики.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/01_SYS/01_TPL_SYS
- FOLDER_NAME: 01_TPL_SYS
- INDEX_SCOPE_TAGS: [SYS, TPL]

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
  UID: UE.V2.SYS.IDX.TPL_SYS.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 01_TPL_SYS
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/01_TPL_SYS/00__INDEX_MANIFEST__TPL__SYS.md
  PATH: UE_V2/01_SYS/01_TPL_SYS/00__INDEX_MANIFEST__TPL__SYS.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.SYS.IDX.TPL_SYS.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for 01_TPL_SYS
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/01_TPL_SYS/00__INDEX_MANIFEST__TPL__SYS.md
  PATH: UE_V2/01_SYS/01_TPL_SYS/00__INDEX_MANIFEST__TPL__SYS.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.SYS.PIPE.TPL_SYS.001
  KIND: PIPE
  ROLE: Navigator for realm actions
  DESC: Uses KEYS, resolves RAW via INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/01_TPL_SYS/00__PIPELINE_CONTRACT__TPL__SYS.md
  PATH: UE_V2/01_SYS/01_TPL_SYS/00__PIPELINE_CONTRACT__TPL__SYS.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT
- KEY: TPL.INDEX_MANIFEST
  UID: UE.V2.SYS.TPL.INDEX_MANIFEST.001
  KIND: TPL
  ROLE: Template for INDEX_MANIFEST docs
  DESC: Canon template for realm address table
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/01_TPL_SYS/01__TPL__INDEX_MANIFEST__SYS.md
  PATH: UE_V2/01_SYS/01_TPL_SYS/01__TPL__INDEX_MANIFEST__SYS.md
  MARKERS: [TPL, SYS]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: TPL.PIPELINE_CONTRACT
  UID: UE.V2.SYS.TPL.PIPELINE_CONTRACT.001
  KIND: TPL
  ROLE: Template for PIPELINE_CONTRACT docs
  DESC: Canon template for step-run contract
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/01_TPL_SYS/02__TPL__PIPELINE_CONTRACT__SYS.md
  PATH: UE_V2/01_SYS/01_TPL_SYS/02__TPL__PIPELINE_CONTRACT__SYS.md
  MARKERS: [TPL, SYS]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: TPL.ENTITY_PASSPORT
  UID: UE.V2.SYS.TPL.ENTITY_PASSPORT.001
  KIND: TPL
  ROLE: Template for ENTITY_PASSPORT docs
  DESC: Canon entity passport header/sections
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/01_TPL_SYS/03__TPL__ENTITY_PASSPORT__SYS.md
  PATH: UE_V2/01_SYS/01_TPL_SYS/03__TPL__ENTITY_PASSPORT__SYS.md
  MARKERS: [TPL, SYS]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: TPL.DECISION_LOG_ENTRY
  UID: UE.V2.SYS.TPL.DECISION_LOG_ENTRY.001
  KIND: TPL
  ROLE: Template for DECISION_LOG_ENTRY docs
  DESC: Canon decision log entry format
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/01_TPL_SYS/04__TPL__DECISION_LOG_ENTRY__SYS.md
  PATH: UE_V2/01_SYS/01_TPL_SYS/04__TPL__DECISION_LOG_ENTRY__SYS.md
  MARKERS: [TPL, SYS, LOG]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: TPL.FILE_HEADER
  UID: UE.V2.SYS.TPL.FILE_HEADER.001
  KIND: TPL
  ROLE: Template for file headers
  DESC: Canon header fields and ordering
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/01_TPL_SYS/05__TPL__FILE_HEADER__SYS.md
  PATH: UE_V2/01_SYS/01_TPL_SYS/05__TPL__FILE_HEADER__SYS.md
  MARKERS: [TPL, SYS]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: TPL.OUTPUT_PACK
  UID: UE.V2.SYS.TPL.OUTPUT_PACK.001
  KIND: TPL
  ROLE: Template for OUTPUT_PACK docs
  DESC: Canon output packaging format
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/01_TPL_SYS/06__TPL__OUTPUT_PACK__SYS.md
  PATH: UE_V2/01_SYS/01_TPL_SYS/06__TPL__OUTPUT_PACK__SYS.md
  MARKERS: [TPL, SYS, OUTPUT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: TPL.RUN_LOG_ENTRY
  UID: UE.V2.SYS.TPL.RUN_LOG_ENTRY.001
  KIND: TPL
  ROLE: Template for RUN_LOG_ENTRY docs
  DESC: Canon run log entry format
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/01_TPL_SYS/07__TPL__RUN_LOG_ENTRY__SYS.md
  PATH: UE_V2/01_SYS/01_TPL_SYS/07__TPL__RUN_LOG_ENTRY__SYS.md
  MARKERS: [TPL, SYS, LOG]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31
