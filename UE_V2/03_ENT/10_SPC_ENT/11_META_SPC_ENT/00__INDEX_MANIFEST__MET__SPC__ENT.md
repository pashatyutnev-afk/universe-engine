FILE: UE_V2/03_ENT/10_SPC_ENT/11_META_SPC_ENT/00__INDEX_MANIFEST__MET__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 11_META_SPC_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: MET_SPC
UID: UE.V2.ENT.SPC.MET.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма META_SPC_ENT.
Хранит RAW и машинные паспорта meta-специалистов (MET). Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- Коротко: 1–2 строки смысла. Без лирики.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/10_SPC_ENT/11_META_SPC_ENT
- FOLDER_NAME: 11_META_SPC_ENT
- INDEX_SCOPE_TAGS: [ENT, SPC, MET]

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
  UID: UE.V2.ENT.SPC.MET.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for META_SPC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/11_META_SPC_ENT/00__INDEX_MANIFEST__MET__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/11_META_SPC_ENT/00__INDEX_MANIFEST__MET__SPC__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.SPC.MET.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for META_SPC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/11_META_SPC_ENT/00__INDEX_MANIFEST__MET__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/11_META_SPC_ENT/00__INDEX_MANIFEST__MET__SPC__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.SPC.MET.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Realm step-run navigator
  DESC: KEY-only contract; resolves targets via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/11_META_SPC_ENT/00__PIPELINE_CONTRACT__MET__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/11_META_SPC_ENT/00__PIPELINE_CONTRACT__MET__SPC__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (meta specialists)

- KEY: SPC.MET.UNIVERSE_CURATOR
  UID:
  KIND: ENTITY
  ROLE: Universe curator
  DESC: Curates canon coherence across domains; outputs canon notes and consolidation actions
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/11_META_SPC_ENT/01__MET__UNIVERSE_CURATOR_SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/11_META_SPC_ENT/01__MET__UNIVERSE_CURATOR_SPC__ENT.md
  MARKERS: [SPC, MET, SPECIALIST, CANON]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.MET.SYSTEM_ARCHITECT
  UID:
  KIND: ENTITY
  ROLE: System architect
  DESC: Owns system-level architecture constraints; outputs architecture decisions and boundary rules
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/11_META_SPC_ENT/02__MET__SYSTEM_ARCHITECT_SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/11_META_SPC_ENT/02__MET__SYSTEM_ARCHITECT_SPC__ENT.md
  MARKERS: [SPC, MET, SPECIALIST, ARCH]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.MET.RULE_SYSTEM_DESIGNER
  UID:
  KIND: ENTITY
  ROLE: Rule system designer
  DESC: Designs rule systems and formal constraints; outputs rule packs and compatibility notes
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/11_META_SPC_ENT/03__MET__RULE_SYSTEM_DESIGNER_SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/11_META_SPC_ENT/03__MET__RULE_SYSTEM_DESIGNER_SPC__ENT.md
  MARKERS: [SPC, MET, SPECIALIST, RULE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.MET.DEPENDENCY_SUPERVISOR
  UID:
  KIND: ENTITY
  ROLE: Dependency supervisor
  DESC: Tracks dependencies between layers/entities; outputs dependency map and breakage alerts
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/11_META_SPC_ENT/04__MET__DEPENDENCY_SUPERVISOR_SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/11_META_SPC_ENT/04__MET__DEPENDENCY_SUPERVISOR_SPC__ENT.md
  MARKERS: [SPC, MET, SPECIALIST, DEP]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.MET.KNOWLEDGE_INTEGRATOR
  UID:
  KIND: ENTITY
  ROLE: Knowledge integrator
  DESC: Integrates KB scope/refs into system work; outputs KB integration notes and next-opens
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/11_META_SPC_ENT/05__MET__KNOWLEDGE_INTEGRATOR_SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/11_META_SPC_ENT/05__MET__KNOWLEDGE_INTEGRATOR_SPC__ENT.md
  MARKERS: [SPC, MET, SPECIALIST, KB]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.MET.META_ANALYST
  UID:
  KIND: ENTITY
  ROLE: Meta analyst
  DESC: Analyzes system performance and failure modes; outputs meta report and improvement proposals
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/11_META_SPC_ENT/06__MET__META_ANALYST_SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/11_META_SPC_ENT/06__MET__META_ANALYST_SPC__ENT.md
  MARKERS: [SPC, MET, SPECIALIST, ANALYTICS]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.MET.LONG_TERM_STRATEGY_PLANNER
  UID:
  KIND: ENTITY
  ROLE: Long-term strategy planner
  DESC: Builds long-term roadmap and milestone structure; outputs strategy plan and checkpoints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/11_META_SPC_ENT/07__MET__LONG_TERM_STRATEGY_PLANNER_SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/11_META_SPC_ENT/07__MET__LONG_TERM_STRATEGY_PLANNER_SPC__ENT.md
  MARKERS: [SPC, MET, SPECIALIST, STRAT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.MET.EVOLUTION_SCALING_PLANNER
  UID:
  KIND: ENTITY
  ROLE: Evolution scaling planner
  DESC: Plans system evolution and scaling; outputs migration path proposals and scaling constraints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/11_META_SPC_ENT/08__MET__EVOLUTION_SCALING_PLANNER_SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/11_META_SPC_ENT/08__MET__EVOLUTION_SCALING_PLANNER_SPC__ENT.md
  MARKERS: [SPC, MET, SPECIALIST, SCALE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31
