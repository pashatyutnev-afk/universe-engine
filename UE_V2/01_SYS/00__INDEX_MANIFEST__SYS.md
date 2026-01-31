FILE: UE_V2/01_SYS/00__INDEX_MANIFEST__SYS.md
SCOPE: UE_V2 / 01_SYS
DOC_TYPE: INDEX_MANIFEST
DOMAIN: SYS
UID: UE.V2.SYS.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма 01_SYS.
Хранит RAW и машинные паспорта SYS-подреалмов. Никаких “историй” и длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Любая навигация по 01_SYS выполняется через KEY → RAW.
- PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/01_SYS
- FOLDER_NAME: 01_SYS
- INDEX_SCOPE_TAGS: [SYS, NAV]

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
  UID: UE.V2.SYS.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 01_SYS
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/00__INDEX_MANIFEST__SYS.md
  PATH: UE_V2/01_SYS/00__INDEX_MANIFEST__SYS.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.SYS.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for 01_SYS
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/00__INDEX_MANIFEST__SYS.md
  PATH: UE_V2/01_SYS/00__INDEX_MANIFEST__SYS.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.SYS.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Realm step-run navigator
  DESC: KEY-only contract; resolves targets via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/00__PIPELINE_CONTRACT__SYS.md
  PATH: UE_V2/01_SYS/00__PIPELINE_CONTRACT__SYS.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (SYS subrealms)
# RULE: SYS-level index stores only subrealm INDEX_MANIFEST entrypoints.
# PIPELINE_CONTRACT for subrealms must be resolved inside each subrealm index (no duplicates here).

- KEY: SYS.TPL_SYS.INDEX_MANIFEST
  UID: UE.V2.SYS.IDX.TPL_SYS.001
  KIND: FILE
  ROLE: Subrealm index for 01_TPL_SYS
  DESC: Address table for SYS templates (TPL_SYS)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/01_TPL_SYS/00__INDEX_MANIFEST__TPL__SYS.md
  PATH: UE_V2/01_SYS/01_TPL_SYS/00__INDEX_MANIFEST__TPL__SYS.md
  MARKERS: [INDEX, SYS, TPL]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SYS.SYS_LAW.INDEX_MANIFEST
  UID: UE.V2.SYS.IDX.SYS_LAW.001
  KIND: FILE
  ROLE: Subrealm index for 02_SYS_LAW
  DESC: Address table for system laws (SYS_LAW)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/01_SYS/02_SYS_LAW/00__INDEX_MANIFEST__SYS__LAW.md
  PATH: UE_V2/01_SYS/02_SYS_LAW/00__INDEX_MANIFEST__SYS__LAW.md
  MARKERS: [INDEX, SYS, LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31
