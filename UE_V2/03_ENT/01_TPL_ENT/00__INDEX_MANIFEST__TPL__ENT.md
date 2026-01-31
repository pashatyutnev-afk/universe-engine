FILE: UE_V2/03_ENT/01_TPL_ENT/00__INDEX_MANIFEST__TPL__ENT.md
SCOPE: UE_V2 / 03_ENT / 01_TPL_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: TPL
UID: UE.V2.ENT.TPL.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для папки/реалма TPL_ENT.
Хранит RAW и машинные паспорта элементов. Никаких “историй” и длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- Коротко: 1–2 строки смысла. Без лирики.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/01_TPL_ENT
- FOLDER_NAME: 01_TPL_ENT
- INDEX_SCOPE_TAGS: [ENT, TPL]

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
  UID: UE.V2.ENT.TPL.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for TPL_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/01_TPL_ENT/00__INDEX_MANIFEST__TPL__ENT.md
  PATH: UE_V2/03_ENT/01_TPL_ENT/00__INDEX_MANIFEST__TPL__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.TPL.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for TPL_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/01_TPL_ENT/00__INDEX_MANIFEST__TPL__ENT.md
  PATH: UE_V2/03_ENT/01_TPL_ENT/00__INDEX_MANIFEST__TPL__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.TPL.PIPELINE_CONTRACT.001
  KIND: FILE
  ROLE: Navigator for realm actions
  DESC: Uses KEYS, resolves RAW via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/01_TPL_ENT/00__PIPELINE_CONTRACT__TPL__ENT.md
  PATH: UE_V2/03_ENT/01_TPL_ENT/00__PIPELINE_CONTRACT__TPL__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT
- KEY: TPL.ENGINE
  UID: UE.V2.ENT.TPL.ENGINE.001
  KIND: TPL
  ROLE: Template for ENGINE entity
  DESC: Canonical ENGINE entity passport template
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/01_TPL_ENT/10__TPL__ENGINE__ENT.md
  PATH: UE_V2/03_ENT/01_TPL_ENT/10__TPL__ENGINE__ENT.md
  MARKERS: [TPL, ENT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: TPL.ORCHESTRATOR
  UID: UE.V2.ENT.TPL.ORCHESTRATOR.001
  KIND: TPL
  ROLE: Template for ORCHESTRATOR entity
  DESC: Canonical ORCHESTRATOR entity passport template
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/01_TPL_ENT/20__TPL__ORCHESTRATOR__ENT.md
  PATH: UE_V2/03_ENT/01_TPL_ENT/20__TPL__ORCHESTRATOR__ENT.md
  MARKERS: [TPL, ENT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: TPL.SPECIALIST
  UID: UE.V2.ENT.TPL.SPECIALIST.001
  KIND: TPL
  ROLE: Template for SPECIALIST entity
  DESC: Canonical SPECIALIST entity passport template
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/01_TPL_ENT/30__TPL__SPECIALIST__ENT.md
  PATH: UE_V2/03_ENT/01_TPL_ENT/30__TPL__SPECIALIST__ENT.md
  MARKERS: [TPL, ENT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: TPL.CONTROLLER
  UID: UE.V2.ENT.TPL.CONTROLLER.001
  KIND: TPL
  ROLE: Template for CONTROLLER entity
  DESC: Canonical CONTROLLER entity passport template
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/01_TPL_ENT/40__TPL__CONTROLLER__ENT.md
  PATH: UE_V2/03_ENT/01_TPL_ENT/40__TPL__CONTROLLER__ENT.md
  MARKERS: [TPL, ENT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: TPL.VALIDATOR
  UID: UE.V2.ENT.TPL.VALIDATOR.001
  KIND: TPL
  ROLE: Template for VALIDATOR entity
  DESC: Canonical VALIDATOR entity passport template
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/01_TPL_ENT/50__TPL__VALIDATOR__ENT.md
  PATH: UE_V2/03_ENT/01_TPL_ENT/50__TPL__VALIDATOR__ENT.md
  MARKERS: [TPL, ENT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: TPL.QA
  UID: UE.V2.ENT.TPL.QA.001
  KIND: TPL
  ROLE: Template for QA entity
  DESC: Canonical QA entity passport template
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/01_TPL_ENT/60__TPL__QA__ENT.md
  PATH: UE_V2/03_ENT/01_TPL_ENT/60__TPL__QA__ENT.md
  MARKERS: [TPL, ENT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: TPL.XREF
  UID: UE.V2.ENT.TPL.XREF.001
  KIND: TPL
  ROLE: Template for XREF entity
  DESC: Canonical XREF entity passport template
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/01_TPL_ENT/90__TPL__XREF__ENT.md
  PATH: UE_V2/03_ENT/01_TPL_ENT/90__TPL__XREF__ENT.md
  MARKERS: [TPL, ENT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31
