FILE: UE_V2/14_LOG/00__INDEX_MANIFEST__LOG.md
SCOPE: UE_V2 / 14_LOG
DOC_TYPE: INDEX_MANIFEST
DOMAIN: LOG
UID: UE.V2.LOG.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма 14_LOG.
Хранит RAW и машинные паспорта LOG-доков. Без “историй” и длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Любая навигация по 14_LOG выполняется через KEY → RAW.
- PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/14_LOG
- FOLDER_NAME: 14_LOG
- INDEX_SCOPE_TAGS: [LOG, SYS, TRACE]

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
  UID: UE.V2.LOG.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 14_LOG
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/14_LOG/00__INDEX_MANIFEST__LOG.md
  PATH: UE_V2/14_LOG/00__INDEX_MANIFEST__LOG.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.LOG.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for 14_LOG
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/14_LOG/00__INDEX_MANIFEST__LOG.md
  PATH: UE_V2/14_LOG/00__INDEX_MANIFEST__LOG.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.LOG.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Realm step-run navigator
  DESC: KEY-only contract; resolves targets via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/14_LOG/00__PIPELINE_CONTRACT__LOG.md
  PATH: UE_V2/14_LOG/00__PIPELINE_CONTRACT__LOG.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (log set)

- KEY: LOG.RUN_LOG
  UID: UE.V2.LOG.RUN_LOG.001
  KIND: LOG
  ROLE: Execution run log (append-only)
  DESC: One run = one record; stores step outputs pointers and status
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/14_LOG/01__RUN_LOG.md
  PATH: UE_V2/14_LOG/01__RUN_LOG.md
  MARKERS: [LOG, MUST_LOAD, TRACE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LOG.CHANGE_LOG
  UID: UE.V2.LOG.CHANGE_LOG.001
  KIND: LOG
  ROLE: Change log (append-only)
  DESC: Records changes to canon/system with minimal entries and pointers
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/14_LOG/02__CHANGE_LOG.md
  PATH: UE_V2/14_LOG/02__CHANGE_LOG.md
  MARKERS: [LOG]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LOG.TOKEN_ARCHIVE
  UID: UE.V2.LOG.TOKEN_ARCHIVE.001
  KIND: LOG
  ROLE: Token archive (append-only)
  DESC: Stores ROUTE_TOKEN/START_OUTPUT/decision artifacts pointers per run
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/14_LOG/03__TOKEN_ARCHIVE.md
  PATH: UE_V2/14_LOG/03__TOKEN_ARCHIVE.md
  MARKERS: [LOG, MUST_LOAD, TOKEN]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LOG.DECISION_LOG
  UID: UE.V2.LOG.DECISION_LOG.001
  KIND: LOG
  ROLE: Decision log (append-only)
  DESC: Stores approvals/rejections/gates outcomes + rationale pointers
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/14_LOG/04__DECISION_LOG.md
  PATH: UE_V2/14_LOG/04__DECISION_LOG.md
  MARKERS: [LOG, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LOG.START_POINT_LOG
  UID: UE.V2.LOG.START_POINT_LOG.001
  KIND: LOG
  ROLE: Start point log (append-only)
  DESC: Records entrypoints (START) invocations + initial inputs snapshot pointers
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/14_LOG/05__START_POINT_LOG.md
  PATH: UE_V2/14_LOG/05__START_POINT_LOG.md
  MARKERS: [LOG, ENTRYPOINT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31
