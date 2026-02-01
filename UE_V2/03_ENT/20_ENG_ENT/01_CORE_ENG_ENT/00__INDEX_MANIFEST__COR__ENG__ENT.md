FILE: UE_V2/03_ENT/20_ENG_ENT/01_CORE_ENG_ENT/00__INDEX_MANIFEST__COR__ENG__ENT.md
SCOPE: UE_V2 / 03_ENT / 20_ENG_ENT / 01_CORE_ENG_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: COR_ENG
UID: UE.V2.ENT.ENG.COR.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма CORE_ENG_ENT (COR).
Хранит RAW и машинные паспорта COR-движков. Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Любая навигация по реалму: KEY -> resolve RAW here -> open.
- PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).
- NO GUESSING: для движков RAW заполняем только после фиксации кнопкой Raw (иначе GAP).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/20_ENG_ENT/01_CORE_ENG_ENT
- FOLDER_NAME: 01_CORE_ENG_ENT
- INDEX_SCOPE_TAGS: [ENT, ENG, COR]

## [M] KEYSPACE
KEY_FORMAT: COR.
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
  UID: UE.V2.ENT.ENG.COR.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for CORE_ENG_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/01_CORE_ENG_ENT/00__INDEX_MANIFEST__COR__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/01_CORE_ENG_ENT/00__INDEX_MANIFEST__COR__ENG__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (minimum for realm)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.ENG.COR.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for COR engines
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/01_CORE_ENG_ENT/00__INDEX_MANIFEST__COR__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/01_CORE_ENG_ENT/00__INDEX_MANIFEST__COR__ENG__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.ENG.COR.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Realm step-run navigator
  DESC: KEY-only contract; resolves targets via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/01_CORE_ENG_ENT/00__PIPELINE_CONTRACT__COR__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/01_CORE_ENG_ENT/00__PIPELINE_CONTRACT__COR__ENG__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (COR engines)
- KEY: COR.CORE_IDENTITY
  UID:
  KIND: ENTITY
  ROLE: Core identity engine
  DESC: Core identity invariants; emits CORE_IDENTITY_TOKEN
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/01_CORE_ENG_ENT/01__COR__CORE_IDENTITY__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/01_CORE_ENG_ENT/01__COR__CORE_IDENTITY__ENG__ENT.md
  MARKERS: [ENG, COR, ID]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: COR.CORE_STATE
  UID:
  KIND: ENTITY
  ROLE: Core state engine
  DESC: State model and transitions; emits CORE_STATE_TOKEN
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/01_CORE_ENG_ENT/02__COR__CORE_STATE__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/01_CORE_ENG_ENT/02__COR__CORE_STATE__ENG__ENT.md
  MARKERS: [ENG, COR, STATE]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: COR.CORE_LIFECYCLE
  UID:
  KIND: ENTITY
  ROLE: Core lifecycle engine
  DESC: Lifecycle phases and checkpoints; emits CORE_LIFECYCLE_MAP
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/01_CORE_ENG_ENT/03__COR__CORE_LIFECYCLE__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/01_CORE_ENG_ENT/03__COR__CORE_LIFECYCLE__ENG__ENT.md
  MARKERS: [ENG, COR, LIFE]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

---

## [M] LOAD_HINTS
MIN_SET_KEYS:
- INDEX_MANIFEST
- PIPELINE_CONTRACT

OPTIONAL_KEYS:
- COR.CORE_IDENTITY
- COR.CORE_STATE
- COR.CORE_LIFECYCLE

## [M] GUARDS
STOP_IF:
- RAW missing for any MIN_SET_KEYS
GAP_IF:
- requested KEY not present in ENTRIES
- any engine RAW not fixed yet (expected during build)
