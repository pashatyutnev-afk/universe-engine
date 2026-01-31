FILE: UE_V2/03_ENT/00_REG_ENT/00__INDEX_MANIFEST__REG__ENT.md
SCOPE: UE_V2 / 03_ENT / 00_REG_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: REG
UID: UE.V2.REG.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-30
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — это “таблица адресов” и кратких смыслов для папки/реалма REG_ENT.
Хранит RAW и машинные паспорта элементов. Никаких “историй” и длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- Коротко: 1–2 строки смысла. Без лирики.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/00_REG_ENT
- FOLDER_NAME: 00_REG_ENT
- INDEX_SCOPE_TAGS: [ENT, REG]

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
  UID: UE.V2.REG.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for REG_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/00_REG_ENT/00__INDEX_MANIFEST__REG__ENT.md
  PATH: UE_V2/03_ENT/00_REG_ENT/00__INDEX_MANIFEST__REG__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (минимум для реалма)
- KEY: REG.INDEX_MANIFEST
  UID: UE.V2.REG.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for REG_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/00_REG_ENT/00__INDEX_MANIFEST__REG__ENT.md
  PATH: UE_V2/03_ENT/00_REG_ENT/00__INDEX_MANIFEST__REG__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: REG.PIPELINE_CONTRACT
  UID: UE.V2.REG.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Navigator for realm actions
  DESC: Uses KEYS, resolves RAW via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/00_REG_ENT/00__PIPELINE_CONTRACT__REG__ENT.md
  PATH: UE_V2/03_ENT/00_REG_ENT/00__PIPELINE_CONTRACT__REG__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: REG.ENTITY_IDS
  UID: UE.V2.REG.ENTITY_IDS.001
  KIND: REG
  ROLE: Canon entity families and naming codes
  DESC: Entity codes/families to keep routing deterministic
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/00_REG_ENT/01__REG__ENTITY_IDS__ENT.md
  PATH: UE_V2/03_ENT/00_REG_ENT/01__REG__ENTITY_IDS__ENT.md
  MARKERS: [REG, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: REG.PATH_MAP
  UID: UE.V2.REG.PATH_MAP.001
  KIND: REG
  ROLE: Semantic map for UE_V2 roots and folders
  DESC: Root layers meaning + folder naming semantics
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/00_REG_ENT/02__REG__PATH_MAP__ENT.md
  PATH: UE_V2/03_ENT/00_REG_ENT/02__REG__PATH_MAP__ENT.md
  MARKERS: [REG, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: REG.UID_REGISTRY
  UID: UE.V2.REG.UID_REGISTRY.001
  KIND: REG
  ROLE: UID collision prevention registry
  DESC: Append-only UID registry for canon and reserves
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/00_REG_ENT/06__REG__UID__REG__ENT.md
  PATH: UE_V2/03_ENT/00_REG_ENT/06__REG__UID__REG__ENT.md
  MARKERS: [REG, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT
- KEY: REG.ENTITY_CATALOG
  UID: UE.V2.REG.ENTITY_CATALOG.001
  KIND: REG
  ROLE: Canon catalog of required entities
  DESC: Required entities list for UE_V2 domains/runtime
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/00_REG_ENT/03__REG__ENTITY_CATALOG__ENT.md
  PATH: UE_V2/03_ENT/00_REG_ENT/03__REG__ENTITY_CATALOG__ENT.md
  MARKERS: [REG]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: REG.ENTITY_TYPES
  UID: UE.V2.REG.ENTITY_TYPES.001
  KIND: REG
  ROLE: Entity type schema
  DESC: Entity types and required fields/sections
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/00_REG_ENT/04__REG__ENTITY_TYPES__ENT.md
  PATH: UE_V2/03_ENT/00_REG_ENT/04__REG__ENTITY_TYPES__ENT.md
  MARKERS: [REG]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: REG.ENTITY_MIN_SET
  UID: UE.V2.REG.ENTITY_MIN_SET.001
  KIND: REG
  ROLE: Minimal load sets by runtime/domain
  DESC: Defines minimal entity sets for execution
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/00_REG_ENT/05__REG__ENTITY_MIN_SET__ENT.md
  PATH: UE_V2/03_ENT/00_REG_ENT/05__REG__ENTITY_MIN_SET__ENT.md
  MARKERS: [REG]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: REG.ENTITY_REGISTRY
  UID: UE.V2.REG.ENTITY_REGISTRY.001
  KIND: REG
  ROLE: Canon entity registry
  DESC: Registry of entities fixed as canon
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/00_REG_ENT/07__REG__ENTITY_REG__ENT.md
  PATH: UE_V2/03_ENT/00_REG_ENT/07__REG__ENTITY_REG__ENT.md
  MARKERS: [REG]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: REG.ARTIFACT_REGISTRY
  UID: UE.V2.REG.ARTIFACT_REGISTRY.001
  KIND: REG
  ROLE: Canon artifact registry
  DESC: Registry of produced artifacts/outputs
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/00_REG_ENT/08__REG__ARTIFACT_REG__ENT.md
  PATH: UE_V2/03_ENT/00_REG_ENT/08__REG__ARTIFACT_REG__ENT.md
  MARKERS: [REG]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: REG.CHANGELOG
  UID: UE.V2.REG.CHANGELOG.001
  KIND: LOG
  ROLE: Change history for REG_ENT
  DESC: Append-only log of changes in REG domain
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/00_REG_ENT/90__REG__CHANGELOG__ENT.md
  PATH: UE_V2/03_ENT/00_REG_ENT/90__REG__CHANGELOG__ENT.md
  MARKERS: [LOG]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: REG.DEPRECATION
  UID: UE.V2.REG.DEPRECATION.001
  KIND: LAW
  ROLE: Deprecation policy and redirects
  DESC: Deprecation notes and redirection rules
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/00_REG_ENT/91__REG__DEPRECATION__ENT.md
  PATH: UE_V2/03_ENT/00_REG_ENT/91__REG__DEPRECATION__ENT.md
  MARKERS: [POLICY, LOG]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31
