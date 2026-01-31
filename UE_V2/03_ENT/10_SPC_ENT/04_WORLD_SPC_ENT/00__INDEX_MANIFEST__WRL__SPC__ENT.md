FILE: UE_V2/03_ENT/10_SPC_ENT/04_WORLD_SPC_ENT/00__INDEX_MANIFEST__WRL__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 04_WORLD_SPC_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: WRL_SPC
UID: UE.V2.ENT.SPC.WRL.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма WORLD_SPC_ENT.
Хранит RAW и машинные паспорта world-специалистов (WRL). Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- Коротко: 1–2 строки смысла. Без лирики.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/10_SPC_ENT/04_WORLD_SPC_ENT
- FOLDER_NAME: 04_WORLD_SPC_ENT
- INDEX_SCOPE_TAGS: [ENT, SPC, WRL]

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
  UID: UE.V2.ENT.SPC.WRL.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for WORLD_SPC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/04_WORLD_SPC_ENT/00__INDEX_MANIFEST__WRL__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/04_WORLD_SPC_ENT/00__INDEX_MANIFEST__WRL__SPC__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.SPC.WRL.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for WORLD_SPC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/04_WORLD_SPC_ENT/00__INDEX_MANIFEST__WRL__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/04_WORLD_SPC_ENT/00__INDEX_MANIFEST__WRL__SPC__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.SPC.WRL.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Realm step-run navigator
  DESC: KEY-only contract; resolves targets via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/04_WORLD_SPC_ENT/00__PIPELINE_CONTRACT__WRL__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/04_WORLD_SPC_ENT/00__PIPELINE_CONTRACT__WRL__SPC__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (world specialists)

- KEY: SPC.WRL.WORLD_BUILDER
  UID:
  KIND: ENTITY
  ROLE: World builder
  DESC: Defines world foundations, constraints, and canon-safe world bible frame
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/04_WORLD_SPC_ENT/01__WRL__WORLD_BUILDER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/04_WORLD_SPC_ENT/01__WRL__WORLD_BUILDER__SPC__ENT.md
  MARKERS: [SPC, WRL, SPECIALIST, ARCH]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.WRL.CULTURE_SOCIETY_ARCHITECT
  UID:
  KIND: ENTITY
  ROLE: Culture and society architect
  DESC: Designs cultures/societies; outputs social rules, norms, conflicts, and texture
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/04_WORLD_SPC_ENT/02__WRL__CULTURE_SOCIETY_ARCHITECT__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/04_WORLD_SPC_ENT/02__WRL__CULTURE_SOCIETY_ARCHITECT__SPC__ENT.md
  MARKERS: [SPC, WRL, SPECIALIST, SOC]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.WRL.CIVILIZATION_DESIGNER
  UID:
  KIND: ENTITY
  ROLE: Civilization designer
  DESC: Designs civilizations, timelines, tech/magic level, governance patterns; outputs civ frame
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/04_WORLD_SPC_ENT/03__WRL__CIVILIZATION_DESIGNER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/04_WORLD_SPC_ENT/03__WRL__CIVILIZATION_DESIGNER__SPC__ENT.md
  MARKERS: [SPC, WRL, SPECIALIST, CIV]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.WRL.GEOGRAPHY_LOCATION_DESIGNER
  UID:
  KIND: ENTITY
  ROLE: Geography and location designer
  DESC: Designs geography, locations, routes, constraints; outputs location grid and map notes
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/04_WORLD_SPC_ENT/04__WRL__GEOGRAPHY_LOCATION_DESIGNER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/04_WORLD_SPC_ENT/04__WRL__GEOGRAPHY_LOCATION_DESIGNER__SPC__ENT.md
  MARKERS: [SPC, WRL, SPECIALIST, GEO]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.WRL.ECONOMY_POWER_SYSTEMS_DESIGNER
  UID:
  KIND: ENTITY
  ROLE: Economy and power systems designer
  DESC: Designs power structures, governance/economy mechanics (non-currency civilizations supported); outputs systems map
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/04_WORLD_SPC_ENT/05__WRL__ECONOMY_POWER_SYSTEMS_DESIGNER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/04_WORLD_SPC_ENT/05__WRL__ECONOMY_POWER_SYSTEMS_DESIGNER__SPC__ENT.md
  MARKERS: [SPC, WRL, SPECIALIST, SYS]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.WRL.RELIGION_MYTHOLOGY_DESIGNER
  UID:
  KIND: ENTITY
  ROLE: Religion and mythology designer
  DESC: Designs religions/mythologies, symbols, rituals; outputs myth map and canon-safe constraints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/04_WORLD_SPC_ENT/06__WRL__RELIGION_MYTHOLOGY_DESIGNER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/04_WORLD_SPC_ENT/06__WRL__RELIGION_MYTHOLOGY_DESIGNER__SPC__ENT.md
  MARKERS: [SPC, WRL, SPECIALIST, MYTH]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.WRL.ECOLOGY_SURVIVAL_DESIGNER
  UID:
  KIND: ENTITY
  ROLE: Ecology and survival designer
  DESC: Designs ecology, survival constraints, hazards/resources; outputs ecology frame and risk notes
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/04_WORLD_SPC_ENT/07__WRL__ECOLOGY_SURVIVAL_DESIGNER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/04_WORLD_SPC_ENT/07__WRL__ECOLOGY_SURVIVAL_DESIGNER__SPC__ENT.md
  MARKERS: [SPC, WRL, SPECIALIST, ECO]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31
