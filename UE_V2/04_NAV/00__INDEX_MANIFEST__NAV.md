FILE: UE_V2/04_NAV/00__INDEX_MANIFEST__NAV.md
SCOPE: UE_V2 / 04_NAV
DOC_TYPE: INDEX_MANIFEST
DOMAIN: NAV
UID: UE.V2.NAV.INDEX_MANIFEST.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-02-05
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма 04_NAV.
Хранит RAW и машинные паспорта NAV-доков и IDX-панелей (routing indexes).
Никаких “историй” и длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Любая навигация по 04_NAV выполняется через KEY → RAW.
- PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).
- Если имя файла/RAW меняется — обновлять ТОЛЬКО тут (и в разрешённых корневых таблицах).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/04_NAV
- FOLDER_NAME: 04_NAV
- INDEX_SCOPE_TAGS: [NAV, SYS]

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
  UID: UE.V2.NAV.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 04_NAV
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/04_NAV/00__INDEX_MANIFEST__NAV.md
  PATH: UE_V2/04_NAV/00__INDEX_MANIFEST__NAV.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-02-05

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.NAV.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for NAV realm
  DESC: Raw addresses + short meaning for 04_NAV
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/04_NAV/00__INDEX_MANIFEST__NAV.md
  PATH: UE_V2/04_NAV/00__INDEX_MANIFEST__NAV.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-02-05

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.NAV.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: NAV realm step-run navigator
  DESC: KEY-only contract; resolves targets via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/04_NAV/00__PIPELINE_CONTRACT_NAV.md
  PATH: UE_V2/04_NAV/00__PIPELINE_CONTRACT_NAV.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-02-05

### [O] CONTENT (IDX panels)
# RULE: Each IDX_* file is a navigation panel used by ROUTE_TOKEN / runtime.
# Keep descriptions 1–2 lines max.

- KEY: NAV.IDX.BOOT
  UID:
  KIND: FILE
  ROLE: Boot navigation panel
  DESC: Pointers/entrypoints for BOOT layer access
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/04_NAV/01__IDX_BOOT.md
  PATH: UE_V2/04_NAV/01__IDX_BOOT.md
  MARKERS: [IDX, NAV, BOOT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: NAV.IDX.ENT
  UID:
  KIND: FILE
  ROLE: Entities navigation panel
  DESC: Pointers/entrypoints for ENT layer access
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/04_NAV/02__IDX_ENT.md
  PATH: UE_V2/04_NAV/02__IDX_ENT.md
  MARKERS: [IDX, NAV, ENT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: NAV.IDX.PIPE
  UID:
  KIND: FILE
  ROLE: Pipelines navigation panel
  DESC: Pointers/entrypoints for PIPE layer access
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/04_NAV/03__IDX_PIPE.md
  PATH: UE_V2/04_NAV/03__IDX_PIPE.md
  MARKERS: [IDX, NAV, PIPE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: NAV.IDX.KB
  UID:
  KIND: FILE
  ROLE: Knowledge base navigation panel
  DESC: Pointers/entrypoints for KB layer access
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/04_NAV/04__IDX_KB.md
  PATH: UE_V2/04_NAV/04__IDX_KB.md
  MARKERS: [IDX, NAV, KB]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: NAV.IDX.AUD
  UID:
  KIND: FILE
  ROLE: Audio domain navigation panel
  DESC: Pointers/entrypoints for DOM_AUD routes and checks
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/04_NAV/05__IDX_AUD.md
  PATH: UE_V2/04_NAV/05__IDX_AUD.md
  MARKERS: [IDX, NAV, AUD, DOM]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: NAV.IDX.VIS
  UID:
  KIND: FILE
  ROLE: Visual domain navigation panel
  DESC: Pointers/entrypoints for DOM_VIS routes and checks
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/04_NAV/06__IDX_VIS.md
  PATH: UE_V2/04_NAV/06__IDX_VIS.md
  MARKERS: [IDX, NAV, VIS, DOM]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: NAV.IDX.LEX
  UID:
  KIND: FILE
  ROLE: Lexicon navigation panel
  DESC: Pointers/entrypoints for LEX layer usage
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/04_NAV/07__IDX_LEX.md
  PATH: UE_V2/04_NAV/07__IDX_LEX.md
  MARKERS: [IDX, NAV, LEX]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: NAV.IDX.REG
  UID:
  KIND: FILE
  ROLE: Registry navigation panel
  DESC: Pointers/entrypoints for REG access (rules/registries)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/04_NAV/08__IDX_REG.md
  PATH: UE_V2/04_NAV/08__IDX_REG.md
  MARKERS: [IDX, NAV, REG]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: NAV.IDX.XREF
  UID:
  KIND: FILE
  ROLE: Cross-references navigation panel
  DESC: Pointers/entrypoints for XREF access and resolution
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/04_NAV/09__IDX_XREF.md
  PATH: UE_V2/04_NAV/09__IDX_XREF.md
  MARKERS: [IDX, NAV, XREF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: NAV.IDX.OPERATIONS
  UID:
  KIND: FILE
  ROLE: Operations navigation panel
  DESC: Operational entrypoints (maintenance, audits, repair ops)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/04_NAV/10__IDX_OPERATIONS.md
  PATH: UE_V2/04_NAV/10__IDX_OPERATIONS.md
  MARKERS: [IDX, NAV, OPS]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: NAV.IDX.LOG
  UID:
  KIND: FILE
  ROLE: Logging navigation panel
  DESC: Pointers/entrypoints for LOG layer access
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/04_NAV/11__IDX_LOG.md
  PATH: UE_V2/04_NAV/11__IDX_LOG.md
  MARKERS: [IDX, NAV, LOG]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: NAV.IDX.MUSIC
  UID:
  KIND: FILE
  ROLE: Music navigation panel
  DESC: Music-specific entrypoints (used by domains/pipelines)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/04_NAV/12__IDX_MUSIC.md
  PATH: UE_V2/04_NAV/12__IDX_MUSIC.md
  MARKERS: [IDX, NAV, MUSIC]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] GLOBAL DICTIONARY (shortnames)
- KEY: NAV.GLOBAL_SHORTNAME_DICTIONARY
  UID: UE.V2.NAV.SHORTNAME_DICTIONARY.001
  KIND: FILE
  ROLE: Global shortname dictionary
  DESC: Canon mapping for shortened tokens → full names/meanings; used to avoid guessing at runtime
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/04_NAV/99__UE_V2__GLOBAL_SHORTNAME_DICTIONARY.md
  PATH: UE_V2/04_NAV/99__UE_V2__GLOBAL_SHORTNAME_DICTIONARY.md
  MARKERS: [NAV, DICT, SHORTNAMES, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-02-05
