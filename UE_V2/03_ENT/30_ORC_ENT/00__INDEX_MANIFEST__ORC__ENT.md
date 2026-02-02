FILE: UE_V2/03_ENT/30_ORC_ENT/00__INDEX_MANIFEST__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: ORC_ENT
UID: UE.V2.ENT.IDX.ORC_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — адресная таблица реалма 30_ORC_ENT.
Хранит KEYS, короткий смысл, RAW и PATH (как справка). Без длинных историй.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- Коротко: 1–2 строки смысла. Без лирики.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/30_ORC_ENT
- FOLDER_NAME: 30_ORC_ENT
- INDEX_SCOPE_TAGS: [ENT, ORC]

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
  UID: UE.V2.ENT.IDX.ORC_ENT.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 30_ORC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/00__INDEX_MANIFEST__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/00__INDEX_MANIFEST__ORC__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.IDX.ORC_ENT.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for 30_ORC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/00__INDEX_MANIFEST__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/00__INDEX_MANIFEST__ORC__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.PIPE.ORC_ENT.001
  KIND: PIPE
  ROLE: Root navigator for ORC_ENT realm
  DESC: Routes to sub-realms by KEY and enforces core orchestration steps
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/00__PIPELINE_CONTRACT__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/00__PIPELINE_CONTRACT__ORC__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

### [O] SUB-REALMS (folders)
- KEY: REALM.GOVERNANCE_ORC_ENT
  UID:
  KIND: FOLDER
  ROLE: Governance orchestrators
  DESC: Compliance, approvals, audit, risk, and change-control for ORC entities
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/00__INDEX_MANIFEST__GVN__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT
  MARKERS: [NAV, REALM]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: REALM.CORE_ORC_ENT
  UID:
  KIND: FOLDER
  ROLE: Core orchestrator runtime
  DESC: Intake, routing, sentinels, step-run, logging, failure handling, output packaging
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/00__INDEX_MANIFEST__COR__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT
  MARKERS: [NAV, REALM]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: REALM.CREATIVE_ORC_ENT
  UID:
  KIND: FOLDER
  ROLE: Creative orchestration
  DESC: Identity/style/trend synthesis and concept-to-artifact bridging
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/02_CREATIVE_ORC_ENT/00__INDEX_MANIFEST__CRV__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/02_CREATIVE_ORC_ENT
  MARKERS: [NAV, REALM]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: REALM.MUSIC_ORC_ENT
  UID:
  KIND: FOLDER
  ROLE: Music orchestration
  DESC: Music brief→lyrics→prompt→loops→QA→release packaging and portfolio planning
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/00__INDEX_MANIFEST__MUS__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT
  MARKERS: [NAV, REALM]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: REALM.VIDEO_ORC_ENT
  UID:
  KIND: FOLDER
  ROLE: Video orchestration
  DESC: Video brief→shot plan→prompt→style packaging→QA→export handoff
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/04_VIDEO_ORC_ENT/00__INDEX_MANIFEST__VID__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/04_VIDEO_ORC_ENT
  MARKERS: [NAV, REALM]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: REALM.DOCS_ORC_ENT
  UID:
  KIND: FOLDER
  ROLE: Documentation orchestration
  DESC: Doc briefs, building, KB scope, lint/QA, release packaging
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/05_DOCS_ORC_ENT/00__INDEX_MANIFEST__DOC__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/05_DOCS_ORC_ENT
  MARKERS: [NAV, REALM]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: REALM.WEB_ORC_ENT
  UID:
  KIND: FOLDER
  ROLE: Web orchestration
  DESC: Web briefs, block factory, a11y QA, SEO packaging, deploy handoff
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/06_WEB_ORC_ENT/00__INDEX_MANIFEST__WEB__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/06_WEB_ORC_ENT
  MARKERS: [NAV, REALM]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: REALM.RESEARCH_ORC_ENT
  UID:
  KIND: FOLDER
  ROLE: Research orchestration
  DESC: Query planning, source triage, summary synth, citation policy bridge
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/07_RESEARCH_ORC_ENT/00__INDEX_MANIFEST__RCH__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/07_RESEARCH_ORC_ENT
  MARKERS: [NAV, REALM]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: REALM.META_ORC_ENT
  UID:
  KIND: FOLDER
  ROLE: Meta orchestration
  DESC: Self-checks, template applying, UID normalization, deprecation policy
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/08_META_ORC_ENT/00__INDEX_MANIFEST__MET__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/08_META_ORC_ENT
  MARKERS: [NAV, REALM]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02
