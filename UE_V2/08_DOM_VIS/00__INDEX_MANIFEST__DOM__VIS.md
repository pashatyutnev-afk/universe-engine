FILE: UE_V2/08_DOM_VIS/00__INDEX_MANIFEST__DOM__VIS.md
SCOPE: UE_V2 / 08_DOM_VIS
DOC_TYPE: INDEX_MANIFEST
DOMAIN: DOM_VIS
UID: UE.V2.DOM.VIS.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма 08_DOM_VIS.
Хранит RAW и машинные паспорта VIS домена: индекс визуала, формат промптов, правила шотов/глитчей,
sync-модули, fail и packaging. Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Любая навигация по 08_DOM_VIS выполняется через KEY → RAW.
- PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/08_DOM_VIS
- FOLDER_NAME: 08_DOM_VIS
- INDEX_SCOPE_TAGS: [DOM, VIS]

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
  UID: UE.V2.DOM.VIS.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 08_DOM_VIS
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/08_DOM_VIS/00__INDEX_MANIFEST__DOM__VIS.md
  PATH: UE_V2/08_DOM_VIS/00__INDEX_MANIFEST__DOM__VIS.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.DOM.VIS.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for 08_DOM_VIS
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/08_DOM_VIS/00__INDEX_MANIFEST__DOM__VIS.md
  PATH: UE_V2/08_DOM_VIS/00__INDEX_MANIFEST__DOM__VIS.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.DOM.VIS.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Domain step-run navigator
  DESC: KEY-only contract; resolves targets via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/08_DOM_VIS/00__PIPELINE_CONTRACT__DOM__VIS.md
  PATH: UE_V2/08_DOM_VIS/00__PIPELINE_CONTRACT__DOM__VIS.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (VIS domain set)

- KEY: VIS.INDEX
  UID:
  KIND: FILE
  ROLE: Visual domain index (fast lookup)
  DESC: Quick map of VIS primitives, modules, and allowed compositions
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/08_DOM_VIS/00__VIS_INDEX.md
  PATH: UE_V2/08_DOM_VIS/00__VIS_INDEX.md
  MARKERS: [DOM, VIS, INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: VIS.LAW15_MAP
  UID:
  KIND: LAW
  ROLE: Law15 mapping
  DESC: Mapping for Law15 constraints into VIS decisions
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/08_DOM_VIS/01__LAW15_MAP.md
  PATH: UE_V2/08_DOM_VIS/01__LAW15_MAP.md
  MARKERS: [DOM, VIS, LAW, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: VIS.PROMPT_FMT
  UID:
  KIND: STD
  ROLE: Prompt format (VIS)
  DESC: Canon prompt sections/order for VIS artifacts and renders
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/08_DOM_VIS/02__PROMPT_FMT.md
  PATH: UE_V2/08_DOM_VIS/02__PROMPT_FMT.md
  MARKERS: [DOM, VIS, STD, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: VIS.GLITCH_RULES
  UID:
  KIND: STD
  ROLE: Glitch rules
  DESC: What glitch is allowed, how to constrain it, how to score violations
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/08_DOM_VIS/03__GLITCH_RULES.md
  PATH: UE_V2/08_DOM_VIS/03__GLITCH_RULES.md
  MARKERS: [DOM, VIS, STD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: VIS.SHOT_RULES
  UID:
  KIND: STD
  ROLE: Shot rules
  DESC: Shot grammar (camera, lens, motion) and constraints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/08_DOM_VIS/04__SHOT_RULES.md
  PATH: UE_V2/08_DOM_VIS/04__SHOT_RULES.md
  MARKERS: [DOM, VIS, STD, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: VIS.SYNC.CF
  UID:
  KIND: FILE
  ROLE: Sync module (CF)
  DESC: Sync rules for CinemaFlow (or CF pipeline integration)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/08_DOM_VIS/05__SYNC_CF.md
  PATH: UE_V2/08_DOM_VIS/05__SYNC_CF.md
  MARKERS: [DOM, VIS, SYNC]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: VIS.SYNC.LRA
  UID:
  KIND: FILE
  ROLE: Sync module (LRA)
  DESC: Sync rules for LRA pipeline integration
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/08_DOM_VIS/06__SYNC_LRA.md
  PATH: UE_V2/08_DOM_VIS/06__SYNC_LRA.md
  MARKERS: [DOM, VIS, SYNC]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: VIS.SYNC.AIR
  UID:
  KIND: FILE
  ROLE: Sync module (AIR)
  DESC: Sync rules for AIR pipeline integration
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/08_DOM_VIS/07__SYNC_AIR.md
  PATH: UE_V2/08_DOM_VIS/07__SYNC_AIR.md
  MARKERS: [DOM, VIS, SYNC]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: VIS.FAIL
  UID:
  KIND: FILE
  ROLE: VIS failure handling
  DESC: VIS-specific fail patterns and recovery actions
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/08_DOM_VIS/08__FAIL_VIS.md
  PATH: UE_V2/08_DOM_VIS/08__FAIL_VIS.md
  MARKERS: [DOM, VIS, FAIL]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: VIS.PACK
  UID:
  KIND: STD
  ROLE: VIS packaging standard
  DESC: Packaging requirements for VIS outputs (files, pointers, checks, next-open keys)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/08_DOM_VIS/09__PACK_VIS.md
  PATH: UE_V2/08_DOM_VIS/09__PACK_VIS.md
  MARKERS: [DOM, VIS, OUTPUT, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31
