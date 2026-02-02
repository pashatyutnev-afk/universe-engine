FILE: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/00__INDEX_MANIFEST__GVN__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 00_GOVERNANCE_ORC_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: GVN_ORC_ENT
UID: UE.V2.ENT.IDX.GVN_ORC_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — адресная таблица реалма 00_GOVERNANCE_ORC_ENT.
Хранит KEYS, короткий смысл, RAW (если есть) и PATH (как справка). Без длинных историй.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- Коротко: 1–2 строки смысла. Без лирики.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT
- FOLDER_NAME: 00_GOVERNANCE_ORC_ENT
- INDEX_SCOPE_TAGS: [ENT, ORC, GVN]

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
  UID: UE.V2.ENT.IDX.GVN_ORC_ENT.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 00_GOVERNANCE_ORC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/00__INDEX_MANIFEST__GVN__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/00__INDEX_MANIFEST__GVN__ORC__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.IDX.GVN_ORC_ENT.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for 00_GOVERNANCE_ORC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/00__INDEX_MANIFEST__GVN__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/00__INDEX_MANIFEST__GVN__ORC__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.PIPE.GVN_ORC_ENT.001
  KIND: PIPE
  ROLE: Navigator for realm actions
  DESC: Uses KEYS, resolves RAW via INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/00__PIPELINE_CONTRACT__GVN__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/00__PIPELINE_CONTRACT__GVN__ORC__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

### [O] GOVERNANCE ORC ENT (modules)
- KEY: GVN.ENTRY_GUARD
  UID:
  KIND: FILE
  ROLE: Entry gatekeeper for governance actions
  DESC: Validates inputs, mode, required keys before any governance run
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/01__GVN__ENTRY_GUARD__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/01__GVN__ENTRY_GUARD__ORC__ENT.md
  MARKERS: [GVN, GUARD, NAV]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: GVN.RULE_ENFORCER
  UID:
  KIND: FILE
  ROLE: Enforces governance hard rules
  DESC: Blocks non-compliant operations; emits fail-codes and required fixes
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/02__GVN__RULE_ENFORCER__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/02__GVN__RULE_ENFORCER__ORC__ENT.md
  MARKERS: [GVN, ENFORCER]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: GVN.DEPENDENCY_RESOLVER
  UID:
  KIND: FILE
  ROLE: Resolves dependencies for governance actions
  DESC: Computes required entities/docs/keys and minimal load order
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/03__GVN__DEPENDENCY_RESOLVER__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/03__GVN__DEPENDENCY_RESOLVER__ORC__ENT.md
  MARKERS: [GVN, RESOLVER]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: GVN.CHANGE_CONTROL
  UID:
  KIND: FILE
  ROLE: Change control router for governance
  DESC: Decides what can change, how to log, and what gates apply
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/04__GVN__CHANGE_CONTROL__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/04__GVN__CHANGE_CONTROL__ORC__ENT.md
  MARKERS: [GVN, CHANGE]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: GVN.RISK_SAFETY
  UID:
  KIND: FILE
  ROLE: Risk and safety evaluator
  DESC: Detects risky actions; requires safeguards or blocks execution
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/05__GVN__RISK_SAFETY__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/05__GVN__RISK_SAFETY__ORC__ENT.md
  MARKERS: [GVN, RISK]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: GVN.DECISION_APPROVAL
  UID:
  KIND: FILE
  ROLE: Decision approval and escalation
  DESC: Determines when approval is required and how to record decision entry
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/06__GVN__DECISION_APPROVAL__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/06__GVN__DECISION_APPROVAL__ORC__ENT.md
  MARKERS: [GVN, DECISION]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: GVN.AUDIT_LOG_BRIDGE
  UID:
  KIND: FILE
  ROLE: Audit log bridge
  DESC: Writes/links run logs and audit records for governance actions
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/07__GVN__AUDIT_LOG_BRIDGE__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/07__GVN__AUDIT_LOG_BRIDGE__ORC__ENT.md
  MARKERS: [GVN, LOG]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: GVN.COMPLIANCE_REPORTER
  UID:
  KIND: FILE
  ROLE: Compliance status reporter
  DESC: Produces compliance summary for run and highlights violations
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/08__GVN__COMPLIANCE_REPORTER__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/08__GVN__COMPLIANCE_REPORTER__ORC__ENT.md
  MARKERS: [GVN, REPORT]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02
