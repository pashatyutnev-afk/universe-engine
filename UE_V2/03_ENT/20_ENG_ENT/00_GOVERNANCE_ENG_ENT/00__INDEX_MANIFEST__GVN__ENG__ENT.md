FILE: UE_V2/03_ENT/20_ENG_ENT/00_GOVERNANCE_ENG_ENT/00__INDEX_MANIFEST__GVN__ENG__ENT.md
SCOPE: UE_V2 / 03_ENT / 20_ENG_ENT / 00_GOVERNANCE_ENG_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: GVN_ENG
UID: UE.V2.ENT.ENG.GVN.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма GOVERNANCE_ENG_ENT (GVN).
Хранит RAW и машинные паспорта GVN-движков. Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Любая навигация по реалму: KEY -> resolve RAW here -> open.
- PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).
- NO GUESSING: для движков RAW заполняем только после фиксации кнопкой Raw (иначе GAP).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/20_ENG_ENT/00_GOVERNANCE_ENG_ENT
- FOLDER_NAME: 00_GOVERNANCE_ENG_ENT
- INDEX_SCOPE_TAGS: [ENT, ENG, GVN]

## [M] KEYSPACE
KEY_FORMAT: GVN.
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
  UID: UE.V2.ENT.ENG.GVN.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for GOVERNANCE_ENG_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/00_GOVERNANCE_ENG_ENT/00__INDEX_MANIFEST__GVN__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/00_GOVERNANCE_ENG_ENT/00__INDEX_MANIFEST__GVN__ENG__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (minimum for realm)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.ENG.GVN.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for GVN engines
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/00_GOVERNANCE_ENG_ENT/00__INDEX_MANIFEST__GVN__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/00_GOVERNANCE_ENG_ENT/00__INDEX_MANIFEST__GVN__ENG__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.ENG.GVN.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Realm step-run navigator
  DESC: KEY-only contract; resolves targets via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/00_GOVERNANCE_ENG_ENT/00__PIPELINE_CONTRACT__GVN__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/00_GOVERNANCE_ENG_ENT/00__PIPELINE_CONTRACT__GVN__ENG__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (GVN engines)
- KEY: GVN.AUDIT_LOG
  UID:
  KIND: ENTITY
  ROLE: Audit-log engine
  DESC: Audit events, trace summaries, compliance snapshots; emits AUDIT_LOG_ENTRY
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/00_GOVERNANCE_ENG_ENT/01__GVN__AUDIT_LOG__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/00_GOVERNANCE_ENG_ENT/01__GVN__AUDIT_LOG__ENG__ENT.md
  MARKERS: [ENG, GVN, AUDIT, LOG]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: GVN.CANON_AUTHORITY
  UID:
  KIND: ENTITY
  ROLE: Canon authority engine
  DESC: Canon authority checks; emits CANON_VERDICT (approve/reject/gap)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/00_GOVERNANCE_ENG_ENT/02__GVN__CANON_AUTHORITY__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/00_GOVERNANCE_ENG_ENT/02__GVN__CANON_AUTHORITY__ENG__ENT.md
  MARKERS: [ENG, GVN, CANON]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: GVN.RULE_HIERARCHY
  UID:
  KIND: ENTITY
  ROLE: Rule hierarchy engine
  DESC: Priority/override rules; resolves conflicts; emits RULE_HIERARCHY_MAP
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/00_GOVERNANCE_ENG_ENT/03__GVN__RULE_HIERARCHY__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/00_GOVERNANCE_ENG_ENT/03__GVN__RULE_HIERARCHY__ENG__ENT.md
  MARKERS: [ENG, GVN, RULES]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: GVN.CHANGE_CONTROL
  UID:
  KIND: ENTITY
  ROLE: Change control engine
  DESC: Change proposal, scope and impact; emits CHANGE_CONTROL_RECORD
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/00_GOVERNANCE_ENG_ENT/04__GVN__CHANGE_CONTROL__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/00_GOVERNANCE_ENG_ENT/04__GVN__CHANGE_CONTROL__ENG__ENT.md
  MARKERS: [ENG, GVN, CHANGE]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: GVN.CONSISTENCY
  UID:
  KIND: ENTITY
  ROLE: Consistency engine
  DESC: Consistency checks across docs/entities; emits CONSISTENCY_REPORT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/00_GOVERNANCE_ENG_ENT/05__GVN__CONSISTENCY__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/00_GOVERNANCE_ENG_ENT/05__GVN__CONSISTENCY__ENG__ENT.md
  MARKERS: [ENG, GVN, CONSISTENCY]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: GVN.DEPENDENCY_REGISTRY
  UID:
  KIND: ENTITY
  ROLE: Dependency registry engine
  DESC: Dependencies graph and SoT pointers; emits DEP_GRAPH_TOKEN
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/00_GOVERNANCE_ENG_ENT/06__GVN__DEPENDENCY_REGISTRY__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/00_GOVERNANCE_ENG_ENT/06__GVN__DEPENDENCY_REGISTRY__ENG__ENT.md
  MARKERS: [ENG, GVN, DEP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: GVN.DECISION_APPROVAL
  UID:
  KIND: ENTITY
  ROLE: Decision approval engine
  DESC: Approval gates and decision record; emits DECISION_RECORD
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/00_GOVERNANCE_ENG_ENT/07__GVN__DECISION_APPROVAL__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/00_GOVERNANCE_ENG_ENT/07__GVN__DECISION_APPROVAL__ENG__ENT.md
  MARKERS: [ENG, GVN, DECISION]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: GVN.SCOPE_IMPACT
  UID:
  KIND: ENTITY
  ROLE: Scope impact engine
  DESC: Scope/impact analysis; emits SCOPE_IMPACT_REPORT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/00_GOVERNANCE_ENG_ENT/08__GVN__SCOPE_IMPACT__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/00_GOVERNANCE_ENG_ENT/08__GVN__SCOPE_IMPACT__ENG__ENT.md
  MARKERS: [ENG, GVN, SCOPE]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: GVN.RISK_SAFETY
  UID:
  KIND: ENTITY
  ROLE: Risk & safety engine
  DESC: Risk analysis and safety gates; emits RISK_SAFETY_PLAN
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/00_GOVERNANCE_ENG_ENT/09__GVN__RISK_SAFETY__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/00_GOVERNANCE_ENG_ENT/09__GVN__RISK_SAFETY__ENG__ENT.md
  MARKERS: [ENG, GVN, RISK]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: GVN.VERSIONING_MEMORY
  UID:
  KIND: ENTITY
  ROLE: Versioning memory engine
  DESC: Version/memory discipline and state; emits VERSION_MEMORY_TOKEN
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/00_GOVERNANCE_ENG_ENT/10__GVN__VERSIONING_MEMORY__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/00_GOVERNANCE_ENG_ENT/10__GVN__VERSIONING_MEMORY__ENG__ENT.md
  MARKERS: [ENG, GVN, VER]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

---

## [M] LOAD_HINTS
MIN_SET_KEYS:
- INDEX_MANIFEST
- PIPELINE_CONTRACT

OPTIONAL_KEYS:
- GVN.AUDIT_LOG
- GVN.CANON_AUTHORITY
- GVN.RULE_HIERARCHY
- GVN.CHANGE_CONTROL
- GVN.CONSISTENCY
- GVN.DEPENDENCY_REGISTRY
- GVN.DECISION_APPROVAL
- GVN.SCOPE_IMPACT
- GVN.RISK_SAFETY
- GVN.VERSIONING_MEMORY

## [M] GUARDS
STOP_IF:
- RAW missing for any MIN_SET_KEYS
GAP_IF:
- requested KEY not present in ENTRIES
- any engine RAW is empty
