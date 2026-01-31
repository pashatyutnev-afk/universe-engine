FILE: UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT/00__INDEX_MANIFEST__CRV__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 01_CREATIVE_SPC_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: CRV_SPC
UID: UE.V2.ENT.SPC.CRV.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма CREATIVE_SPC_ENT.
Хранит RAW и машинные паспорта элементов. Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- Коротко: 1–2 строки смысла. Без лирики.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT
- FOLDER_NAME: 01_CREATIVE_SPC_ENT
- INDEX_SCOPE_TAGS: [ENT, SPC, CRV]

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
  UID: UE.V2.ENT.SPC.CRV.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for CREATIVE_SPC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT/00__INDEX_MANIFEST__CRV__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT/00__INDEX_MANIFEST__CRV__SPC__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.SPC.CRV.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for CREATIVE_SPC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT/00__INDEX_MANIFEST__CRV__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT/00__INDEX_MANIFEST__CRV__SPC__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.SPC.CRV.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Realm step-run navigator
  DESC: KEY-only contract; resolves targets via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT/00__PIPELINE_CONTRACT__CRV__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT/00__PIPELINE_CONTRACT__CRV__SPC__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (creative specialists)

- KEY: SPC.CRV.CREATIVE_DIRECTOR
  UID:
  KIND: ENTITY
  ROLE: Creative direction owner
  DESC: Defines creative intent, theme axis, constraints, and final direction in SPECIALIST_OUTPUT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT/01__CRV__CREATIVE_DIRECTOR__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT/01__CRV__CREATIVE_DIRECTOR__SPC__ENT.md
  MARKERS: [SPC, CRV, SPECIALIST, DIR]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.CRV.VISUAL_STYLE_ARCHITECT
  UID:
  KIND: ENTITY
  ROLE: Visual style system architect
  DESC: Defines visual style rules, constraints, style tokens, coherence checks
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT/02__CRV__VISUAL_STYLE_ARCHITECT__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT/02__CRV__VISUAL_STYLE_ARCHITECT__SPC__ENT.md
  MARKERS: [SPC, CRV, SPECIALIST, VIS]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.CRV.WORLD_AESTHETIC_DESIGNER
  UID:
  KIND: ENTITY
  ROLE: World aesthetic designer
  DESC: Shapes world aesthetics, texture, motifs, era-feel; outputs aesthetic frame
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT/03__CRV__WORLD_AESTHETIC_DESIGNER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT/03__CRV__WORLD_AESTHETIC_DESIGNER__SPC__ENT.md
  MARKERS: [SPC, CRV, SPECIALIST, WORLD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.CRV.CONCEPT_DESIGNER
  UID:
  KIND: ENTITY
  ROLE: Concept designer
  DESC: Generates concept variants and selects canon concept direction (artifact output)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT/04__CRV__CONCEPT_DESIGNER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT/04__CRV__CONCEPT_DESIGNER__SPC__ENT.md
  MARKERS: [SPC, CRV, SPECIALIST, CONCEPT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.CRV.SYMBOLISM_METAPHOR_DESIGNER
  UID:
  KIND: ENTITY
  ROLE: Symbolism and metaphor designer
  DESC: Defines symbolic layer, metaphor map, narrative/visual anchors (artifact output)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT/05__CRV__SYMBOLISM_METAPHOR_DESIGNER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT/05__CRV__SYMBOLISM_METAPHOR_DESIGNER__SPC__ENT.md
  MARKERS: [SPC, CRV, SPECIALIST, META]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.CRV.MOOD_ATMOSPHERE_CURATOR
  UID:
  KIND: ENTITY
  ROLE: Mood and atmosphere curator
  DESC: Curates mood/atmosphere palette, tension curve, emotional anchors (artifact output)
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT/06__CRV__MOOD_ATMOSPHERE_CURATOR__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT/06__CRV__MOOD_ATMOSPHERE_CURATOR__SPC__ENT.md
  MARKERS: [SPC, CRV, SPECIALIST, MOOD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.CRV.ARTISTIC_RISK_DESIGNER
  UID:
  KIND: ENTITY
  ROLE: Artistic risk designer
  DESC: Identifies creative risks and controlled breakpoints; outputs risk plan + mitigations
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT/07__CRV__ARTISTIC_RISK_DESIGNER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT/07__CRV__ARTISTIC_RISK_DESIGNER__SPC__ENT.md
  MARKERS: [SPC, CRV, SPECIALIST, RISK]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.CRV.IDEA_GENERATOR
  UID:
  KIND: ENTITY
  ROLE: Idea generator
  DESC: Generates idea batches and creative prompts; outputs structured idea pack
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT/08__CRV__IDEA_GENERATOR__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/01_CREATIVE_SPC_ENT/08__CRV__IDEA_GENERATOR__SPC__ENT.md
  MARKERS: [SPC, CRV, SPECIALIST, IDEA]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31
