FILE: UE_V2/03_ENT/60_QA_ENT/00_GOVERNANCE_QA_ENT/00__INDEX_MANIFEST__GVN__QA__ENT.md
SCOPE: UE_V2 / 03_ENT / 60_QA_ENT / 00_GOVERNANCE_QA_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: GVN_QA_ENT
UID: UE.V2.ENT.IDX.GVN_QA_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: QA_ENT
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — адресная таблица governance-реалма QA.
Хранит RAW и короткие смыслы для QA governance: gates, QA flow, issue lifecycle.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- Коротко: 1–2 строки смысла. Без лирики.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/60_QA_ENT/00_GOVERNANCE_QA_ENT
- FOLDER_NAME: 00_GOVERNANCE_QA_ENT
- INDEX_SCOPE_TAGS: [ENT, QA, GVN]

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
  UID: UE.V2.ENT.IDX.GVN_QA_ENT.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for QA governance realm
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/00_GOVERNANCE_QA_ENT/00__INDEX_MANIFEST__GVN__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/00_GOVERNANCE_QA_ENT/00__INDEX_MANIFEST__GVN__QA__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

### [M] REQUIRED
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.IDX.GVN_QA_ENT.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: RAW addresses + short meaning for QA governance
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/00_GOVERNANCE_QA_ENT/00__INDEX_MANIFEST__GVN__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/00_GOVERNANCE_QA_ENT/00__INDEX_MANIFEST__GVN__QA__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.PIPE.GVN_QA_ENT.001
  KIND: PIPE
  ROLE: Router for QA governance actions
  DESC: Uses KEYS, resolves RAW via INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/00_GOVERNANCE_QA_ENT/00__PIPELINE_CONTRACT__GVN__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/00_GOVERNANCE_QA_ENT/00__PIPELINE_CONTRACT__GVN__QA__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

### [O] CONTENT
- KEY: QA.GVN.NATURALNESS_GATE
  UID: UE.V2.ENT.QA.GVN.NATURALNESS_GATE.001
  KIND: ENTITY
  ROLE: Minimal naturalness gate
  DESC: Detects robotic/unnatural output and returns required fixes
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/00_GOVERNANCE_QA_ENT/01__GVN__NATURALNESS_GATE__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/00_GOVERNANCE_QA_ENT/01__GVN__NATURALNESS_GATE__QA__ENT.md
  MARKERS: [QA, GVN, GATE, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

- KEY: QA.GVN.CREATE_FLOW
  UID: UE.V2.ENT.QA.GVN.CREATE_FLOW.001
  KIND: ENTITY
  ROLE: Canon QA flow builder
  DESC: Standard run sequence: inputs, checks, report, issues, handoff
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/00_GOVERNANCE_QA_ENT/02__GVN__CREATE_FLOW__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/00_GOVERNANCE_QA_ENT/02__GVN__CREATE_FLOW__QA__ENT.md
  MARKERS: [QA, GVN, ROUTER]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02

- KEY: QA.GVN.ISSUE_LIFECYCLE
  UID: UE.V2.ENT.QA.GVN.ISSUE_LIFECYCLE.001
  KIND: ENTITY
  ROLE: Canon issue lifecycle rules
  DESC: Defines statuses, severity, and closure requirements for QA issues
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/60_QA_ENT/00_GOVERNANCE_QA_ENT/03__GVN__ISSUE_LIFECYCLE__QA__ENT.md
  PATH: UE_V2/03_ENT/60_QA_ENT/00_GOVERNANCE_QA_ENT/03__GVN__ISSUE_LIFECYCLE__QA__ENT.md
  MARKERS: [QA, GVN, LOG, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: QA_ENT
  UPDATED: 2026-02-02
