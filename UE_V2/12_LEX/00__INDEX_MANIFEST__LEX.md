FILE: UE_V2/12_LEX/00__INDEX_MANIFEST__LEX.md
SCOPE: UE_V2 / 12_LEX
DOC_TYPE: INDEX_MANIFEST
DOMAIN: LEX
UID: UE.V2.LEX.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма 12_LEX.
Хранит RAW и машинные паспорта LEX-доков: коды/сокращения/контрактные обозначения.
Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Любая навигация по 12_LEX выполняется через KEY → RAW.
- PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/12_LEX
- FOLDER_NAME: 12_LEX
- INDEX_SCOPE_TAGS: [LEX, SYS]

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
  UID: UE.V2.LEX.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 12_LEX
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/12_LEX/00__INDEX_MANIFEST__LEX.md
  PATH: UE_V2/12_LEX/00__INDEX_MANIFEST__LEX.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.LEX.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for 12_LEX
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/12_LEX/00__INDEX_MANIFEST__LEX.md
  PATH: UE_V2/12_LEX/00__INDEX_MANIFEST__LEX.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.LEX.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Realm step-run navigator
  DESC: KEY-only contract; resolves targets via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/12_LEX/00__PIPELINE_CONTRACT__LEX.md
  PATH: UE_V2/12_LEX/00__PIPELINE_CONTRACT__LEX.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (lexicon code sets)

- KEY: LEX.CODES.LAW
  UID:
  KIND: LEX
  ROLE: Law codes dictionary
  DESC: Codes/tokens used for laws and law references
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/12_LEX/01__CODES_LAW.md
  PATH: UE_V2/12_LEX/01__CODES_LAW.md
  MARKERS: [LEX, LAW]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LEX.CODES.MET
  UID:
  KIND: LEX
  ROLE: Meta codes dictionary
  DESC: Codes/tokens used for meta/system descriptors
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/12_LEX/02__CODES_MET.md
  PATH: UE_V2/12_LEX/02__CODES_MET.md
  MARKERS: [LEX, META]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LEX.CODES.PIPE
  UID:
  KIND: LEX
  ROLE: Pipeline codes dictionary
  DESC: Codes/tokens used in PIPE/STEP-RUN contracts and routing
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/12_LEX/03__CODES_PIPE.md
  PATH: UE_V2/12_LEX/03__CODES_PIPE.md
  MARKERS: [LEX, PIPE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LEX.CODES.VIS
  UID:
  KIND: LEX
  ROLE: Visual codes dictionary
  DESC: Codes/tokens used for VIS domain and style notation
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/12_LEX/04__CODES_VIS.md
  PATH: UE_V2/12_LEX/04__CODES_VIS.md
  MARKERS: [LEX, VIS]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LEX.ABBR_RULES
  UID:
  KIND: STD
  ROLE: Abbreviation rules
  DESC: Abbreviation discipline and allowed shortening rules
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/12_LEX/05__ABBR_RULES.md
  PATH: UE_V2/12_LEX/05__ABBR_RULES.md
  MARKERS: [LEX, STD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31
