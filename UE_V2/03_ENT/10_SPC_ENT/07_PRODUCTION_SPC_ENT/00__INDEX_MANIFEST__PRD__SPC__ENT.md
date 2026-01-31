FILE: UE_V2/03_ENT/10_SPC_ENT/07_PRODUCTION_SPC_ENT/00__INDEX_MANIFEST__PRD__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 07_PRODUCTION_SPC_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: PRD_SPC
UID: UE.V2.ENT.SPC.PRD.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма PRODUCTION_SPC_ENT.
Хранит RAW и машинные паспорта production-специалистов (PRD). Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- Коротко: 1–2 строки смысла. Без лирики.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/10_SPC_ENT/07_PRODUCTION_SPC_ENT
- FOLDER_NAME: 07_PRODUCTION_SPC_ENT
- INDEX_SCOPE_TAGS: [ENT, SPC, PRD]

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
  UID: UE.V2.ENT.SPC.PRD.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for PRODUCTION_SPC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/07_PRODUCTION_SPC_ENT/00__INDEX_MANIFEST__PRD__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/07_PRODUCTION_SPC_ENT/00__INDEX_MANIFEST__PRD__SPC__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.SPC.PRD.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for PRODUCTION_SPC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/07_PRODUCTION_SPC_ENT/00__INDEX_MANIFEST__PRD__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/07_PRODUCTION_SPC_ENT/00__INDEX_MANIFEST__PRD__SPC__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.SPC.PRD.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Realm step-run navigator
  DESC: KEY-only contract; resolves targets via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/07_PRODUCTION_SPC_ENT/00__PIPELINE_CONTRACT__PRD__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/07_PRODUCTION_SPC_ENT/00__PIPELINE_CONTRACT__PRD__SPC__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (production specialists)

- KEY: SPC.PRD.EXECUTIVE_PRODUCER
  UID:
  KIND: ENTITY
  ROLE: Executive producer
  DESC: Owns production strategy and constraints; approves scope, budget/time logic, and priority tradeoffs
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/07_PRODUCTION_SPC_ENT/01__PRD__EXECUTIVE_PRODUCER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/07_PRODUCTION_SPC_ENT/01__PRD__EXECUTIVE_PRODUCER__SPC__ENT.md
  MARKERS: [SPC, PRD, SPECIALIST, LEAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.PRD.DIRECTOR
  UID:
  KIND: ENTITY
  ROLE: Director
  DESC: Owns execution direction (scene-to-scene); balances narrative/visual/audio constraints in production decisions
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/07_PRODUCTION_SPC_ENT/02__PRD__DIRECTOR__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/07_PRODUCTION_SPC_ENT/02__PRD__DIRECTOR__SPC__ENT.md
  MARKERS: [SPC, PRD, SPECIALIST, DIR]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.PRD.CONTENT_PRODUCER
  UID:
  KIND: ENTITY
  ROLE: Content producer
  DESC: Produces deliverables plan; coordinates specialists; drives task-to-output execution
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/07_PRODUCTION_SPC_ENT/03__PRD__CONTENT_PRODUCER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/07_PRODUCTION_SPC_ENT/03__PRD__CONTENT_PRODUCER__SPC__ENT.md
  MARKERS: [SPC, PRD, SPECIALIST, PROD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.PRD.TRANSMEDIA_PRODUCER
  UID:
  KIND: ENTITY
  ROLE: Transmedia producer
  DESC: Plans cross-platform story/material expansions; outputs transmedia map and release linkage
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/07_PRODUCTION_SPC_ENT/04__PRD__TRANSMEDIA_PRODUCER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/07_PRODUCTION_SPC_ENT/04__PRD__TRANSMEDIA_PRODUCER__SPC__ENT.md
  MARKERS: [SPC, PRD, SPECIALIST, XPLAT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.PRD.EPISODE_CHAPTER_PLANNER
  UID:
  KIND: ENTITY
  ROLE: Episode/chapter planner
  DESC: Plans episodes/chapters structure and delivery units; outputs episode map + dependencies
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/07_PRODUCTION_SPC_ENT/05__PRD__EPISODE_CHAPTER_PLANNER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/07_PRODUCTION_SPC_ENT/05__PRD__EPISODE_CHAPTER_PLANNER__SPC__ENT.md
  MARKERS: [SPC, PRD, SPECIALIST, PLAN]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.PRD.PLATFORM_ADAPTATION_SPECIALIST
  UID:
  KIND: ENTITY
  ROLE: Platform adaptation specialist
  DESC: Adapts outputs to platform constraints; outputs adaptation checklist and variants plan
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/07_PRODUCTION_SPC_ENT/06__PRD__PLATFORM_ADAPTATION_SPECIALIST__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/07_PRODUCTION_SPC_ENT/06__PRD__PLATFORM_ADAPTATION_SPECIALIST__SPC__ENT.md
  MARKERS: [SPC, PRD, SPECIALIST, PLATFORM]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.PRD.LOCALIZATION_MANAGER
  UID:
  KIND: ENTITY
  ROLE: Localization manager
  DESC: Manages localization process; outputs localization plan, glossary needs, and QA checkpoints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/07_PRODUCTION_SPC_ENT/07__PRD__LOCALIZATION_MANAGER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/07_PRODUCTION_SPC_ENT/07__PRD__LOCALIZATION_MANAGER__SPC__ENT.md
  MARKERS: [SPC, PRD, SPECIALIST, LOC]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.PRD.RELEASE_MANAGER
  UID:
  KIND: ENTITY
  ROLE: Release manager
  DESC: Owns release readiness; gates packaging, QA signoff, and publish sequencing
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/07_PRODUCTION_SPC_ENT/08__PRD__RELEASE_MANAGER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/07_PRODUCTION_SPC_ENT/08__PRD__RELEASE_MANAGER__SPC__ENT.md
  MARKERS: [SPC, PRD, SPECIALIST, REL]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.PRD.SCHEDULE_COORDINATOR
  UID:
  KIND: ENTITY
  ROLE: Schedule coordinator
  DESC: Coordinates schedule, dependencies, and deadlines; outputs schedule grid and critical path notes
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/07_PRODUCTION_SPC_ENT/09__PRD__SCHEDULE_COORDINATOR__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/07_PRODUCTION_SPC_ENT/09__PRD__SCHEDULE_COORDINATOR__SPC__ENT.md
  MARKERS: [SPC, PRD, SPECIALIST, TIME]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31
