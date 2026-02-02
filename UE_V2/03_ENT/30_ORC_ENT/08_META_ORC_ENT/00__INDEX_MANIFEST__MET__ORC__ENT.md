FILE: UE_V2/03_ENT/30_ORC_ENT/08_META_ORC_ENT/00__INDEX_MANIFEST__MET__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 08_META_ORC_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: MET_ORC_ENT
UID: UE.V2.ENT.IDX.MET_ORC_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — адресная таблица реалма 08_META_ORC_ENT.
Хранит KEYS, короткий смысл, RAW и PATH (как справка). Без длинных историй.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- Коротко: 1–2 строки смысла. Без лирики.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/30_ORC_ENT/08_META_ORC_ENT
- FOLDER_NAME: 08_META_ORC_ENT
- INDEX_SCOPE_TAGS: [ENT, ORC, META]

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
  UID: UE.V2.ENT.IDX.MET_ORC_ENT.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 08_META_ORC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/08_META_ORC_ENT/00__INDEX_MANIFEST__MET__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/08_META_ORC_ENT/00__INDEX_MANIFEST__MET__ORC__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.IDX.MET_ORC_ENT.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for 08_META_ORC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/08_META_ORC_ENT/00__INDEX_MANIFEST__MET__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/08_META_ORC_ENT/00__INDEX_MANIFEST__MET__ORC__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.PIPE.MET_ORC_ENT.001
  KIND: PIPE
  ROLE: Navigator for realm actions
  DESC: Uses KEYS, resolves RAW via INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/08_META_ORC_ENT/00__PIPELINE_CONTRACT__MET__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/08_META_ORC_ENT/00__PIPELINE_CONTRACT__MET__ORC__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

### [O] META ORC ENT (modules)
- KEY: MET.SELF_CHECK
  UID:
  KIND: FILE
  ROLE: Self-check orchestrator
  DESC: Runs self-checks for coherence, missing inputs, and rule compliance
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/08_META_ORC_ENT/01__MET__SELF_CHECK__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/08_META_ORC_ENT/01__MET__SELF_CHECK__ORC__ENT.md
  MARKERS: [MET, QA, GUARD]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: MET.TEMPLATE_APPLIER
  UID:
  KIND: FILE
  ROLE: Template applier
  DESC: Applies canon templates and section ordering to outputs
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/08_META_ORC_ENT/02__MET__TEMPLATE_APPLIER__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/08_META_ORC_ENT/02__MET__TEMPLATE_APPLIER__ORC__ENT.md
  MARKERS: [MET, TPL]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: MET.NORMALIZATION_UID
  UID:
  KIND: FILE
  ROLE: UID normalization
  DESC: Normalizes UID/CHANGE_ID and enforces UID_RULES
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/08_META_ORC_ENT/03__MET__NORMALIZATION_UID__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/08_META_ORC_ENT/03__MET__NORMALIZATION_UID__ORC__ENT.md
  MARKERS: [MET, UID, RULES]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: MET.DEPRECATION_POLICY
  UID:
  KIND: FILE
  ROLE: Deprecation policy
  DESC: Defines deprecation rules, migration notes, and deprecation gates
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/08_META_ORC_ENT/04__MET__DEPRECATION_POLICY__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/08_META_ORC_ENT/04__MET__DEPRECATION_POLICY__ORC__ENT.md
  MARKERS: [MET, DEPRECATION, POLICY]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02
