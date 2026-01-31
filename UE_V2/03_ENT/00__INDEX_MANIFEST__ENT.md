FILE: UE_V2/03_ENT/00__INDEX_MANIFEST__ENT.md
SCOPE: UE_V2 / 03_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: ENT
UID: UE.V2.ENT.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма 03_ENT.
Хранит RAW и машинные паспорта ENT-слоя: входы в семейства сущностей и корневые контракты/модель.
Никаких “историй” и длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Любая навигация по 03_ENT выполняется через KEY → RAW.
- PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).
- Не перечислять тысячи сущностей в корневом индексе: только входы и корневые контракты.

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT
- FOLDER_NAME: 03_ENT
- INDEX_SCOPE_TAGS: [ENT, NAV, SYS]

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
  UID: UE.V2.ENT.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 03_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/00__INDEX_MANIFEST__ENT.md
  PATH: UE_V2/03_ENT/00__INDEX_MANIFEST__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (минимум для слоя)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for ENT layer
  DESC: Raw addresses + short meaning for 03_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/00__INDEX_MANIFEST__ENT.md
  PATH: UE_V2/03_ENT/00__INDEX_MANIFEST__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: ENT layer step-run navigator
  DESC: KEY-only contract; resolves targets via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/00__PIPELINE_CONTRACT__ENT.md
  PATH: UE_V2/03_ENT/00__PIPELINE_CONTRACT__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (ENT layer core files)

- KEY: ENT.MODEL
  UID:
  KIND: FILE
  ROLE: Entity model definition
  DESC: Canon entity model, sections and invariants
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/01__ENT_MODEL.md
  PATH: UE_V2/03_ENT/01__ENT_MODEL.md
  MARKERS: [ENT, MODEL, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: ENT.CONTRACT.ENT
  UID:
  KIND: FILE
  ROLE: ENT contract
  DESC: Rules for entity lifecycle and layer operations
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/02__ENT_CONTRACT.md
  PATH: UE_V2/03_ENT/02__ENT_CONTRACT.md
  MARKERS: [ENT, CONTRACT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: ENT.CONTRACT.SPC
  UID:
  KIND: FILE
  ROLE: SPC contract
  DESC: SPC layer integration contract for entities
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/03__SPC_CONTRACT.md
  PATH: UE_V2/03_ENT/03__SPC_CONTRACT.md
  MARKERS: [ENT, SPC, CONTRACT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: ENT.CONTRACT.ORC
  UID:
  KIND: FILE
  ROLE: ORC contract
  DESC: ORC integration contract for entities
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/04__ORC_CONTRACT.md
  PATH: UE_V2/03_ENT/04__ORC_CONTRACT.md
  MARKERS: [ENT, ORC, CONTRACT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: ENT.CONTRACT.CTL
  UID:
  KIND: FILE
  ROLE: CTL contract
  DESC: CTL integration contract for entities
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/05__CTL_CONTRACT.md
  PATH: UE_V2/03_ENT/05__CTL_CONTRACT.md
  MARKERS: [ENT, CTL, CONTRACT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: ENT.CONTRACT.VAL
  UID:
  KIND: FILE
  ROLE: VAL contract
  DESC: VAL integration contract for entities
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/06__VAL_CONTRACT.md
  PATH: UE_V2/03_ENT/06__VAL_CONTRACT.md
  MARKERS: [ENT, VAL, CONTRACT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: ENT.CONTRACT.QA
  UID:
  KIND: FILE
  ROLE: QA contract
  DESC: QA integration contract for entities
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/07__QA_CONTRACT.md
  PATH: UE_V2/03_ENT/07__QA_CONTRACT.md
  MARKERS: [ENT, QA, CONTRACT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: ENT.CONTRACT.XREF
  UID:
  KIND: FILE
  ROLE: XREF contract
  DESC: XREF integration contract for entities
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/08__XREF_CONTRACT.md
  PATH: UE_V2/03_ENT/08__XREF_CONTRACT.md
  MARKERS: [ENT, XREF, CONTRACT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: ENT.DOMAIN_PLUGIN
  UID:
  KIND: FILE
  ROLE: Domain plugin interface
  DESC: Domain plugin interface for ENT usage in domains
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/09__DOMAIN_PLUGIN.md
  PATH: UE_V2/03_ENT/09__DOMAIN_PLUGIN.md
  MARKERS: [ENT, DOM]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: ENT.REGISTRY_CONTRACT
  UID:
  KIND: FILE
  ROLE: Registry contract
  DESC: Registry discipline and operations contract for ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10__REGISTRY_CONTRACT.md
  PATH: UE_V2/03_ENT/10__REGISTRY_CONTRACT.md
  MARKERS: [ENT, REG]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: ENT.TEMPLATE_SET
  UID:
  KIND: FILE
  ROLE: Template set definition
  DESC: Canon template set for entity families
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/11__TEMPLATE_SET.md
  PATH: UE_V2/03_ENT/11__TEMPLATE_SET.md
  MARKERS: [ENT, TPL]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: ENT.ENTITY_MIN_PASS
  UID:
  KIND: FILE
  ROLE: Minimal entity pass gate
  DESC: Minimal pass criteria for entities (ready/not ready)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/12__ENTITY_MIN_PASS.md
  PATH: UE_V2/03_ENT/12__ENTITY_MIN_PASS.md
  MARKERS: [ENT, GATE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (family entrypoints)
# RULE: Root ENT index stores only family entrypoints (subrealm INDEX_MANIFEST).
# Each family resolves its own PIPELINE_CONTRACT internally (no duplicates here).

- KEY: ENT.FAM.REG.INDEX_MANIFEST
  UID: UE.V2.REG.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Family index for 00_REG_ENT
  DESC: Registry/rules tables for entities (REG_ENT)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/00_REG_ENT/00__INDEX_MANIFEST__REG__ENT.md
  PATH: UE_V2/03_ENT/00_REG_ENT/00__INDEX_MANIFEST__REG__ENT.md
  MARKERS: [INDEX, ENT, REG]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: ENT.FAM.TPL.INDEX_MANIFEST
  UID: UE.V2.ENT.TPL.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Family index for 01_TPL_ENT
  DESC: Canon templates for entity passports (TPL_ENT)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/01_TPL_ENT/00__INDEX_MANIFEST__TPL__ENT.md
  PATH: UE_V2/03_ENT/01_TPL_ENT/00__INDEX_MANIFEST__TPL__ENT.md
  MARKERS: [INDEX, ENT, TPL]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: ENT.FAM.SPC.INDEX_MANIFEST
  UID: UE.V2.ENT.SPC.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Family index for 10_SPC_ENT
  DESC: Master index for SPC families (SPC_ENT)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/00__INDEX_MANIFEST__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/00__INDEX_MANIFEST__SPC__ENT.md
  MARKERS: [INDEX, ENT, SPC]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: ENT.FAM.ENG.LAYER
  UID:
  KIND: FOLDER
  ROLE: Family folder placeholder for 20_ENG_ENT
  DESC: Family exists; INDEX_MANIFEST not registered yet
  RAW:
  PATH: UE_V2/03_ENT/20_ENG_ENT
  MARKERS: [ENT, ENG, FAMILY, GAP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: ENT.FAM.ORC.LAYER
  UID:
  KIND: FOLDER
  ROLE: Family folder placeholder for 30_ORC_ENT
  DESC: Family exists; INDEX_MANIFEST not registered yet
  RAW:
  PATH: UE_V2/03_ENT/30_ORC_ENT
  MARKERS: [ENT, ORC, FAMILY, GAP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: ENT.FAM.CTL.LAYER
  UID:
  KIND: FOLDER
  ROLE: Family folder placeholder for 40_CTL_ENT
  DESC: Family exists; INDEX_MANIFEST not registered yet
  RAW:
  PATH: UE_V2/03_ENT/40_CTL_ENT
  MARKERS: [ENT, CTL, FAMILY, GAP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: ENT.FAM.VAL.LAYER
  UID:
  KIND: FOLDER
  ROLE: Family folder placeholder for 50_VAL_ENT
  DESC: Family exists; INDEX_MANIFEST not registered yet
  RAW:
  PATH: UE_V2/03_ENT/50_VAL_ENT
  MARKERS: [ENT, VAL, FAMILY, GAP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: ENT.FAM.QA.LAYER
  UID:
  KIND: FOLDER
  ROLE: Family folder placeholder for 60_QA_ENT
  DESC: Family exists; INDEX_MANIFEST not registered yet
  RAW:
  PATH: UE_V2/03_ENT/60_QA_ENT
  MARKERS: [ENT, QA, FAMILY, GAP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: ENT.FAM.XREF.LAYER
  UID:
  KIND: FOLDER
  ROLE: Family folder placeholder for 90_XREF_ENT
  DESC: Family exists; INDEX_MANIFEST not registered yet
  RAW:
  PATH: UE_V2/03_ENT/90_XREF_ENT
  MARKERS: [ENT, XREF, FAMILY, GAP]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31
