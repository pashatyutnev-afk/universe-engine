FILE: UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/00__INDEX_MANIFEST__GVN__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 00_TOP_GOVERNANCE_SPC_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: GVN_SPC
UID: UE.V2.ENT.SPC.GVN.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма TOP_GOVERNANCE_SPC_ENT.
Хранит RAW и машинные паспорта элементов. Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- Коротко: 1–2 строки смысла. Без лирики.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT
- FOLDER_NAME: 00_TOP_GOVERNANCE_SPC_ENT
- INDEX_SCOPE_TAGS: [ENT, SPC, GVN]

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
  UID: UE.V2.ENT.SPC.GVN.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for TOP_GOVERNANCE_SPC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/00__INDEX_MANIFEST__GVN__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/00__INDEX_MANIFEST__GVN__SPC__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.SPC.GVN.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for TOP_GOVERNANCE_SPC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/00__INDEX_MANIFEST__GVN__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/00__INDEX_MANIFEST__GVN__SPC__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.SPC.GVN.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Navigator for realm actions
  DESC: Uses KEYS, resolves RAW via INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/00__PIPELINE_CONTRACT__GVN__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/00__PIPELINE_CONTRACT__GVN__SPC__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (SPC governance set)

- KEY: SPC.GVN.MACHINE_ARCHITECT
  UID:
  KIND: ENTITY
  ROLE: Governance machine architect
  DESC: Top governance: system architecture ownership
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/01__GVN__MACHINE_ARCHITECT__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/01__GVN__MACHINE_ARCHITECT__SPC__ENT.md
  MARKERS: [SPC, GVN]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.GVN.GOVERNANCE_OWNER
  UID:
  KIND: ENTITY
  ROLE: Governance owner
  DESC: Canon governance ownership and arbitration rules
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/02__GVN__GOVERNANCE_OWNER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/02__GVN__GOVERNANCE_OWNER__SPC__ENT.md
  MARKERS: [SPC, GVN]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.GVN.STANDARDS_OWNER
  UID:
  KIND: ENTITY
  ROLE: Standards owner
  DESC: Owns standards lifecycle and compliance gates
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/03__GVN__STANDARDS_OWNER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/03__GVN__STANDARDS_OWNER__SPC__ENT.md
  MARKERS: [SPC, GVN, STD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.GVN.DOC_CONTROLLER
  UID:
  KIND: ENTITY
  ROLE: Documentation controller
  DESC: Controls doc structure, headers, minimality, traceability
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/04__GVN__DOC_CONTROLLER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/04__GVN__DOC_CONTROLLER__SPC__ENT.md
  MARKERS: [SPC, GVN, DOC]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.GVN.PIPELINE_ARCHITECT
  UID:
  KIND: ENTITY
  ROLE: Pipeline architect
  DESC: Designs STEP-RUN contracts and routing policies
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/05__GVN__PIPELINE_ARCHITECT__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/05__GVN__PIPELINE_ARCHITECT__SPC__ENT.md
  MARKERS: [SPC, GVN, PIPE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.GVN.INTEGRATION_PACKER
  UID:
  KIND: ENTITY
  ROLE: Integration packer
  DESC: Packs outputs and integration bundles for handoff
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/06__GVN__INTEGRATION_PACKER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/06__GVN__INTEGRATION_PACKER__SPC__ENT.md
  MARKERS: [SPC, GVN, OUTPUT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31
