FILE: UE_V2/03_ENT/30_ORC_ENT/02_CREATIVE_ORC_ENT/00__INDEX_MANIFEST__CRV__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 02_CREATIVE_ORC_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: CRV_ORC_ENT
UID: UE.V2.ENT.IDX.CRV_ORC_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — адресная таблица реалма 02_CREATIVE_ORC_ENT.
Хранит KEYS, короткий смысл, RAW и PATH (как справка). Без длинных историй.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- Коротко: 1–2 строки смысла. Без лирики.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/30_ORC_ENT/02_CREATIVE_ORC_ENT
- FOLDER_NAME: 02_CREATIVE_ORC_ENT
- INDEX_SCOPE_TAGS: [ENT, ORC, CREATIVE]

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
  UID: UE.V2.ENT.IDX.CRV_ORC_ENT.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 02_CREATIVE_ORC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/02_CREATIVE_ORC_ENT/00__INDEX_MANIFEST__CRV__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/02_CREATIVE_ORC_ENT/00__INDEX_MANIFEST__CRV__ORC__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.IDX.CRV_ORC_ENT.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for 02_CREATIVE_ORC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/02_CREATIVE_ORC_ENT/00__INDEX_MANIFEST__CRV__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/02_CREATIVE_ORC_ENT/00__INDEX_MANIFEST__CRV__ORC__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.PIPE.CRV_ORC_ENT.001
  KIND: PIPE
  ROLE: Navigator for realm actions
  DESC: Uses KEYS, resolves RAW via INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/02_CREATIVE_ORC_ENT/00__PIPELINE_CONTRACT__CRV__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/02_CREATIVE_ORC_ENT/00__PIPELINE_CONTRACT__CRV__ORC__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

### [O] CREATIVE ORC ENT (modules)
- KEY: CRV.IDENTITY_FACTORY
  UID:
  KIND: FILE
  ROLE: Identity factory for creative outputs
  DESC: Builds identity frames, naming, tone constraints, and brand tokens
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/02_CREATIVE_ORC_ENT/01__CRV__IDENTITY_FACTORY__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/02_CREATIVE_ORC_ENT/01__CRV__IDENTITY_FACTORY__ORC__ENT.md
  MARKERS: [CRV, ID, NAV]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: CRV.STYLE_SYSTEM_BUILDER
  UID:
  KIND: FILE
  ROLE: Style system builder
  DESC: Builds style system rules, constraints, and reusable style tokens
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/02_CREATIVE_ORC_ENT/02__CRV__STYLE_SYSTEM_BUILDER__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/02_CREATIVE_ORC_ENT/02__CRV__STYLE_SYSTEM_BUILDER__ORC__ENT.md
  MARKERS: [CRV, STYLE]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: CRV.TREND_SYNTHESIZER
  UID:
  KIND: FILE
  ROLE: Trend synthesizer
  DESC: Synthesizes trend patterns into usable creative directives
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/02_CREATIVE_ORC_ENT/03__CRV__TREND_SYNTHESIZER__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/02_CREATIVE_ORC_ENT/03__CRV__TREND_SYNTHESIZER__ORC__ENT.md
  MARKERS: [CRV, TREND]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: CRV.CONCEPT_TO_ARTIFACT_BRIDGE
  UID:
  KIND: FILE
  ROLE: Concept-to-artifact bridge
  DESC: Translates concept into final artifact specs and packaging tokens
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/02_CREATIVE_ORC_ENT/04__CRV__CONCEPT_TO_ARTIFACT_BRIDGE__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/02_CREATIVE_ORC_ENT/04__CRV__CONCEPT_TO_ARTIFACT_BRIDGE__ORC__ENT.md
  MARKERS: [CRV, BRIDGE, OUTPUT]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02
