FILE: UE_V2/09_DOM_LOR/00__INDEX_MANIFEST__DOM__LOR.md
SCOPE: UE_V2 / 09_DOM_LOR
DOC_TYPE: INDEX_MANIFEST
DOMAIN: DOM_LOR
UID: UE.V2.DOM.LOR.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма 09_DOM_LOR.
Хранит RAW и машинные паспорта LOR домена: триггеры, языковую адаптацию, арки, канон-лок, fail/pack/xref.
Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Любая навигация по 09_DOM_LOR выполняется через KEY → RAW.
- PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/09_DOM_LOR
- FOLDER_NAME: 09_DOM_LOR
- INDEX_SCOPE_TAGS: [DOM, LOR]

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
  UID: UE.V2.DOM.LOR.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 09_DOM_LOR
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/09_DOM_LOR/00__INDEX_MANIFEST__DOM__LOR.md
  PATH: UE_V2/09_DOM_LOR/00__INDEX_MANIFEST__DOM__LOR.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.DOM.LOR.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for 09_DOM_LOR
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/09_DOM_LOR/00__INDEX_MANIFEST__DOM__LOR.md
  PATH: UE_V2/09_DOM_LOR/00__INDEX_MANIFEST__DOM__LOR.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.DOM.LOR.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Domain step-run navigator
  DESC: KEY-only contract; resolves targets via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/09_DOM_LOR/00__PIPELINE_CONTRACT__DOM__LOR.md
  PATH: UE_V2/09_DOM_LOR/00__PIPELINE_CONTRACT__DOM__LOR.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (LOR domain set)

- KEY: LOR.TRIGGER
  UID:
  KIND: PIPE
  ROLE: LOR trigger / entry rules
  DESC: How LOR tasks start; required inputs and first opens
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/09_DOM_LOR/01__LOR_TRIGGER.md
  PATH: UE_V2/09_DOM_LOR/01__LOR_TRIGGER.md
  MARKERS: [DOM, LOR, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LOR.RI_TO_LANG
  UID:
  KIND: STD
  ROLE: Readability boundary to language mapping
  DESC: Mapping rules from RI/readability to language/wording constraints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/09_DOM_LOR/02__RI_TO_LANG.md
  PATH: UE_V2/09_DOM_LOR/02__RI_TO_LANG.md
  MARKERS: [DOM, LOR, STD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LOR.ARC.S16
  UID:
  KIND: FILE
  ROLE: Arc definition S16
  DESC: Arc reference file used by LOR domain (season/arc S16)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/09_DOM_LOR/03__ARC_S16.md
  PATH: UE_V2/09_DOM_LOR/03__ARC_S16.md
  MARKERS: [DOM, LOR, ARC]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LOR.CANON_LOCK
  UID:
  KIND: LAW
  ROLE: Canon lock policy for LOR
  DESC: Rules for canon locking, approvals, and no-conflict enforcement
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/09_DOM_LOR/04__CANON_LOCK.md
  PATH: UE_V2/09_DOM_LOR/04__CANON_LOCK.md
  MARKERS: [DOM, LOR, LAW, CANON]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LOR.FAIL
  UID:
  KIND: FILE
  ROLE: LOR fail codes / failure handling
  DESC: LOR-specific failure patterns and recovery actions
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/09_DOM_LOR/05__FAIL_LOR.md
  PATH: UE_V2/09_DOM_LOR/05__FAIL_LOR.md
  MARKERS: [DOM, LOR, FAIL]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LOR.PACK
  UID:
  KIND: STD
  ROLE: LOR output packaging
  DESC: Packaging requirements for LOR artifacts and pointers
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/09_DOM_LOR/06__PACK_LOR.md
  PATH: UE_V2/09_DOM_LOR/06__PACK_LOR.md
  MARKERS: [DOM, LOR, OUTPUT, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: LOR.XREF
  UID:
  KIND: XREF
  ROLE: LOR cross-reference rules
  DESC: XREF rules and required linkouts for LOR artifacts
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/09_DOM_LOR/07__XREF_LOR.md
  PATH: UE_V2/09_DOM_LOR/07__XREF_LOR.md
  MARKERS: [DOM, LOR, XREF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31
