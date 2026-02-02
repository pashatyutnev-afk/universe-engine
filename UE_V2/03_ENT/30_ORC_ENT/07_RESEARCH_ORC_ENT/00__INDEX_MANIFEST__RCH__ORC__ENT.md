FILE: UE_V2/03_ENT/30_ORC_ENT/07_RESEARCH_ORC_ENT/00__INDEX_MANIFEST__RCH__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 07_RESEARCH_ORC_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: RCH_ORC_ENT
UID: UE.V2.ENT.IDX.RCH_ORC_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — адресная таблица реалма 07_RESEARCH_ORC_ENT.
Хранит KEYS, короткий смысл, RAW и PATH (как справка). Без длинных историй.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- Коротко: 1–2 строки смысла. Без лирики.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/30_ORC_ENT/07_RESEARCH_ORC_ENT
- FOLDER_NAME: 07_RESEARCH_ORC_ENT
- INDEX_SCOPE_TAGS: [ENT, ORC, RESEARCH]

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
  UID: UE.V2.ENT.IDX.RCH_ORC_ENT.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 07_RESEARCH_ORC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/07_RESEARCH_ORC_ENT/00__INDEX_MANIFEST__RCH__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/07_RESEARCH_ORC_ENT/00__INDEX_MANIFEST__RCH__ORC__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.IDX.RCH_ORC_ENT.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for 07_RESEARCH_ORC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/07_RESEARCH_ORC_ENT/00__INDEX_MANIFEST__RCH__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/07_RESEARCH_ORC_ENT/00__INDEX_MANIFEST__RCH__ORC__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.PIPE.RCH_ORC_ENT.001
  KIND: PIPE
  ROLE: Navigator for realm actions
  DESC: Uses KEYS, resolves RAW via INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/07_RESEARCH_ORC_ENT/00__PIPELINE_CONTRACT__RCH__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/07_RESEARCH_ORC_ENT/00__PIPELINE_CONTRACT__RCH__ORC__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

### [O] RESEARCH ORC ENT (modules)
- KEY: RCH.QUERY_PLANNER
  UID:
  KIND: FILE
  ROLE: Query planner
  DESC: Plans research queries and decomposes tasks into search intents
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/07_RESEARCH_ORC_ENT/01__RCH__QUERY_PLANNER__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/07_RESEARCH_ORC_ENT/01__RCH__QUERY_PLANNER__ORC__ENT.md
  MARKERS: [RCH, QUERY, PLAN]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: RCH.SOURCE_TRIAGE
  UID:
  KIND: FILE
  ROLE: Source triage
  DESC: Filters sources by trust, recency, relevance, and de-duplication rules
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/07_RESEARCH_ORC_ENT/02__RCH__SOURCE_TRIAGE__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/07_RESEARCH_ORC_ENT/02__RCH__SOURCE_TRIAGE__ORC__ENT.md
  MARKERS: [RCH, SOURCE, QA]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: RCH.SUMMARY_SYNTH
  UID:
  KIND: FILE
  ROLE: Summary synthesis
  DESC: Synthesizes findings into structured summary with minimal claims
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/07_RESEARCH_ORC_ENT/03__RCH__SUMMARY_SYNTH__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/07_RESEARCH_ORC_ENT/03__RCH__SUMMARY_SYNTH__ORC__ENT.md
  MARKERS: [RCH, SYNTH, OUTPUT]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: RCH.CITATION_POLICY_BRIDGE
  UID:
  KIND: FILE
  ROLE: Citation policy bridge
  DESC: Applies citation policy: what must be cited and how to attach sources
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/07_RESEARCH_ORC_ENT/04__RCH__CITATION_POLICY_BRIDGE__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/07_RESEARCH_ORC_ENT/04__RCH__CITATION_POLICY_BRIDGE__ORC__ENT.md
  MARKERS: [RCH, CITE, POLICY]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02
