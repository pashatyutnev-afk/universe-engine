FILE: UE_V2/13_STR_PNT/00__INDEX_MANIFEST__STR__PNT.md
SCOPE: UE_V2 / 13_STR_PNT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: STR_PNT
UID: UE.V2.STR_PNT.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма 13_STR_PNT.
Хранит RAW и машинные паспорта стартовых точек (start points) для запуска типовых режимов работы.
Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Любая навигация по 13_STR_PNT выполняется через KEY → RAW.
- PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/13_STR_PNT
- FOLDER_NAME: 13_STR_PNT
- INDEX_SCOPE_TAGS: [ENTRYPOINT, STR_PNT, SYS]

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
  UID: UE.V2.STR_PNT.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 13_STR_PNT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/13_STR_PNT/00__INDEX_MANIFEST__STR__PNT.md
  PATH: UE_V2/13_STR_PNT/00__INDEX_MANIFEST__STR__PNT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.STR_PNT.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for 13_STR_PNT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/13_STR_PNT/00__INDEX_MANIFEST__STR__PNT.md
  PATH: UE_V2/13_STR_PNT/00__INDEX_MANIFEST__STR__PNT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.STR_PNT.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Realm step-run navigator
  DESC: KEY-only contract; resolves targets via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/13_STR_PNT/00__PIPELINE_CONTRACT__STR__PNT.md
  PATH: UE_V2/13_STR_PNT/00__PIPELINE_CONTRACT__STR__PNT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (start points)

- KEY: STR_PNT.NEW_TASK
  UID: UE.V2.STR_PNT.NEW_TASK.001
  KIND: FILE
  ROLE: Start point for new task
  DESC: Clean start: new TASK_TEXT -> ROUTE_TOKEN -> domain pipeline
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/13_STR_PNT/01__STR_PNT__NEW_TASK.md
  PATH: UE_V2/13_STR_PNT/01__STR_PNT__NEW_TASK.md
  MARKERS: [STR_PNT, ENTRYPOINT, TASK]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: STR_PNT.PATCH_FIX
  UID: UE.V2.STR_PNT.PATCH_FIX.001
  KIND: FILE
  ROLE: Start point for patch/fix
  DESC: Patch mode: apply PATCH protocol, validate, package, log
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/13_STR_PNT/02__STR_PNT__PATCH_FIX.md
  PATH: UE_V2/13_STR_PNT/02__STR_PNT__PATCH_FIX.md
  MARKERS: [STR_PNT, ENTRYPOINT, PATCH]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: STR_PNT.QA_FAIL
  UID: UE.V2.STR_PNT.QA_FAIL.001
  KIND: FILE
  ROLE: Start point for QA failure
  DESC: QA fail recovery: reproduce, isolate, fix, re-validate, re-pack
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/13_STR_PNT/03__STR_PNT__QA_FAIL.md
  PATH: UE_V2/13_STR_PNT/03__STR_PNT__QA_FAIL.md
  MARKERS: [STR_PNT, ENTRYPOINT, QA]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: STR_PNT.RELEASE_READY
  UID: UE.V2.STR_PNT.RELEASE_READY.001
  KIND: FILE
  ROLE: Start point for release-ready packaging
  DESC: Release-ready mode: final gates, packaging, signoff, log
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/13_STR_PNT/04__STR_PNT__RELEASE_READY.md
  PATH: UE_V2/13_STR_PNT/04__STR_PNT__RELEASE_READY.md
  MARKERS: [STR_PNT, ENTRYPOINT, REL]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31
