FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/00__INDEX_MANIFEST__COR__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: COR_ORC_ENT
UID: UE.V2.ENT.IDX.COR_ORC_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-03
OWNER: ORC_ENT
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — адресная таблица реалма 01_CORE_ORC_ENT.
Хранит KEYS, короткий смысл, RAW (если есть) и PATH (как справка). Без длинных историй.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- Коротко: 1–2 строки смысла. Без лирики.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT
- FOLDER_NAME: 01_CORE_ORC_ENT
- INDEX_SCOPE_TAGS: [ENT, ORC, CORE]

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
  UID: UE.V2.ENT.IDX.COR_ORC_ENT.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 01_CORE_ORC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/00__INDEX_MANIFEST__COR__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/00__INDEX_MANIFEST__COR__ORC__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-03

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.IDX.COR_ORC_ENT.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for 01_CORE_ORC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/00__INDEX_MANIFEST__COR__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/00__INDEX_MANIFEST__COR__ORC__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-03

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.PIPE.COR_ORC_ENT.001
  KIND: PIPE
  ROLE: Navigator for realm actions
  DESC: Uses KEYS, resolves RAW via INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/00__PIPELINE_CONTRACT__COR__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/00__PIPELINE_CONTRACT__COR__ORC__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-03

### [O] CORE ORC ENT (modules)
- KEY: COR.TASK_INTAKE
  UID: UE.V2.ENT.ORC.COR.TASK_INTAKE.001
  KIND: FILE
  ROLE: Task intake and normalization
  DESC: Parses user request, extracts constraints, sets initial run intent
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/01__COR__TASK_INTAKE__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/01__COR__TASK_INTAKE__ORC__ENT.md
  MARKERS: [CORE, INTAKE, NAV]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-03

- KEY: COR.DOMAIN_DETECTOR
  UID: UE.V2.ENT.ORC.COR.DOMAIN_DETECTOR.001
  KIND: FILE
  ROLE: Domain detection and routing hint
  DESC: Detects target domain/realm and proposes minimal route
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/02__COR__DOMAIN_DETECTOR__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/02__COR__DOMAIN_DETECTOR__ORC__ENT.md
  MARKERS: [CORE, DETECT, ROUTE]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-03

- KEY: COR.ROUTE_TOKEN_BUILDER
  UID: UE.V2.ENT.ORC.COR.ROUTE_TOKEN_BUILDER.001
  KIND: FILE
  ROLE: Route token builder
  DESC: Builds ROUTE_TOKEN (workset keys, minimal load plan, next action)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/03__COR__ROUTE_TOKEN_BUILDER__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/03__COR__ROUTE_TOKEN_BUILDER__ORC__ENT.md
  MARKERS: [CORE, TOKEN, ROUTER]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-03

- KEY: COR.NAV_SENTINEL
  UID: UE.V2.ENT.ORC.COR.NAV_SENTINEL.001
  KIND: FILE
  ROLE: Navigation sentinel
  DESC: Enforces RAW-only nav and blocks PATH обходы when RAW exists
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/04__COR__NAV_SENTINEL__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/04__COR__NAV_SENTINEL__ORC__ENT.md
  MARKERS: [CORE, NAV, GUARD]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-03

- KEY: COR.REG_SENTINEL
  UID: UE.V2.ENT.ORC.COR.REG_SENTINEL.001
  KIND: FILE
  ROLE: Registry sentinel
  DESC: Validates required registers/logging hooks for the run
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/05__COR__REG_SENTINEL__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/05__COR__REG_SENTINEL__ORC__ENT.md
  MARKERS: [CORE, REG, GUARD]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-03

- KEY: COR.XREF_SENTINEL
  UID: UE.V2.ENT.ORC.COR.XREF_SENTINEL.001
  KIND: FILE
  ROLE: Cross-reference sentinel
  DESC: Ensures xref boundaries and correct cross-realm references
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/06__COR__XREF_SENTINEL__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/06__COR__XREF_SENTINEL__ORC__ENT.md
  MARKERS: [CORE, XREF, GUARD]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-03

- KEY: COR.KB_SENTINEL
  UID: UE.V2.ENT.ORC.COR.KB_SENTINEL.001
  KIND: FILE
  ROLE: Knowledge base sentinel
  DESC: Enforces KB scope boundaries and required KB tokens
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/07__COR__KB_SENTINEL__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/07__COR__KB_SENTINEL__ORC__ENT.md
  MARKERS: [CORE, KB, GUARD]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-03

- KEY: COR.PIPE_SELECTOR
  UID: UE.V2.ENT.ORC.COR.PIPE_SELECTOR.001
  KIND: FILE
  ROLE: Pipeline selector
  DESC: Selects best-fit pipeline based on route token and constraints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/08__COR__PIPE_SELECTOR__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/08__COR__PIPE_SELECTOR__ORC__ENT.md
  MARKERS: [CORE, PIPE, SELECT]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-03

- KEY: COR.PIPE_DISPATCHER
  UID: UE.V2.ENT.ORC.COR.PIPE_DISPATCHER.001
  KIND: FILE
  ROLE: Pipeline dispatcher
  DESC: Dispatches execution into chosen pipe and maintains run context
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/09__COR__PIPE_DISPATCHER__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/09__COR__PIPE_DISPATCHER__ORC__ENT.md
  MARKERS: [CORE, PIPE, DISPATCH]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-03

- KEY: COR.STEP_RUN_CONTROLLER
  UID: UE.V2.ENT.ORC.COR.STEP_RUN_CONTROLLER.001
  KIND: FILE
  ROLE: Step-run controller
  DESC: Controls S0–S3 step cadence, gates, and minimal-open policy
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/10__COR__STEP_RUN_CONTROLLER__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/10__COR__STEP_RUN_CONTROLLER__ORC__ENT.md
  MARKERS: [CORE, STEP, CONTROL]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-03

- KEY: COR.FOCUS_LOOP_CONTROLLER
  UID: UE.V2.ENT.ORC.COR.FOCUS_LOOP_CONTROLLER.001
  KIND: FILE
  ROLE: Focus loop controller
  DESC: Maintains focus, prevents drift, enforces route token scope
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/11__COR__FOCUS_LOOP_CONTROLLER__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/11__COR__FOCUS_LOOP_CONTROLLER__ORC__ENT.md
  MARKERS: [CORE, FOCUS, CONTROL]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-03

- KEY: COR.GATEKEEPER
  UID: UE.V2.ENT.ORC.COR.GATEKEEPER.001
  KIND: FILE
  ROLE: Gatekeeper for run completion
  DESC: Applies final gates and decides PASS/FAIL with required next prompt
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/12__COR__GATEKEEPER__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/12__COR__GATEKEEPER__ORC__ENT.md
  MARKERS: [CORE, GATE, FINAL]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-03

- KEY: COR.LOGGER
  UID: UE.V2.ENT.ORC.COR.LOGGER.001
  KIND: FILE
  ROLE: Run logger
  DESC: Emits run logs, decision entries, and audit hooks
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/13__COR__LOGGER__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/13__COR__LOGGER__ORC__ENT.md
  MARKERS: [CORE, LOG]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-03

- KEY: COR.FAIL_HANDLER
  UID: UE.V2.ENT.ORC.COR.FAIL_HANDLER.001
  KIND: FILE
  ROLE: Failure handler
  DESC: Normalizes fail-codes, explains required inputs, sets safe next step
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/14__COR__FAIL_HANDLER__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/14__COR__FAIL_HANDLER__ORC__ENT.md
  MARKERS: [CORE, FAIL, SAFETY]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-03

- KEY: COR.RELEASE_PACKAGER
  UID: UE.V2.ENT.ORC.COR.RELEASE_PACKAGER.001
  KIND: FILE
  ROLE: Release/output packager
  DESC: Packages deliverables into OUTPUT_PACK with deterministic formatting
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/15__COR__RELEASE_PACKAGER__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/15__COR__RELEASE_PACKAGER__ORC__ENT.md
  MARKERS: [CORE, OUTPUT, PACK]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-03

### [O] LEGACY (back-compat)
- KEY: LEGACY.NARRATIVE_ORC_ENG
  UID: UE.V2.ENT.ORC.LEGACY.NARRATIVE_ORC_ENG.001
  KIND: FILE
  ROLE: Legacy narrative orchestrator (ENG flavor)
  DESC: Back-compat module for legacy narrative pipelines
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/90__LEGACY__NARRATIVE__ORC__ENG.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/90__LEGACY__NARRATIVE__ORC__ENG.md
  MARKERS: [LEGACY]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-03

- KEY: LEGACY.CHARACTER_ORC_ENG
  UID: UE.V2.ENT.ORC.LEGACY.CHARACTER_ORC_ENG.001
  KIND: FILE
  ROLE: Legacy character orchestrator (ENG flavor)
  DESC: Back-compat module for legacy character pipelines
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/91__LEGACY__CHARACTER__ORC__ENG.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/91__LEGACY__CHARACTER__ORC__ENG.md
  MARKERS: [LEGACY]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-03

- KEY: LEGACY.WORLD_ORC_ENG
  UID: UE.V2.ENT.ORC.LEGACY.WORLD_ORC_ENG.001
  KIND: FILE
  ROLE: Legacy world orchestrator (ENG flavor)
  DESC: Back-compat module for legacy world pipelines
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/92__LEGACY__WORLD__ORC__ENG.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/92__LEGACY__WORLD__ORC__ENG.md
  MARKERS: [LEGACY]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-03

- KEY: LEGACY.PRODUCTION_ORC_ENG
  UID: UE.V2.ENT.ORC.LEGACY.PRODUCTION_ORC_ENG.001
  KIND: FILE
  ROLE: Legacy production orchestrator (ENG flavor)
  DESC: Back-compat module for legacy production pipelines
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/93__LEGACY__PRODUCTION__ORC__ENG.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/93__LEGACY__PRODUCTION__ORC__ENG.md
  MARKERS: [LEGACY]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-03

- KEY: LEGACY.PIPELINE_ORC_ENG
  UID: UE.V2.ENT.ORC.LEGACY.PIPELINE_ORC_ENG.001
  KIND: FILE
  ROLE: Legacy pipeline orchestrator (ENG flavor)
  DESC: Back-compat module for legacy pipeline routing
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/94__LEGACY__PIPELINE__ORC__ENG.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/94__LEGACY__PIPELINE__ORC__ENG.md
  MARKERS: [LEGACY]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-03
