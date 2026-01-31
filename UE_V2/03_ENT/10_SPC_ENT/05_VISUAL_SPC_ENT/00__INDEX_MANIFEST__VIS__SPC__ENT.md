FILE: UE_V2/03_ENT/10_SPC_ENT/05_VISUAL_SPC_ENT/00__INDEX_MANIFEST__VIS__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 05_VISUAL_SPC_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: VIS_SPC
UID: UE.V2.ENT.SPC.VIS.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма VISUAL_SPC_ENT.
Хранит RAW и машинные паспорта visual-специалистов (VIS). Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- Коротко: 1–2 строки смысла. Без лирики.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/10_SPC_ENT/05_VISUAL_SPC_ENT
- FOLDER_NAME: 05_VISUAL_SPC_ENT
- INDEX_SCOPE_TAGS: [ENT, SPC, VIS]

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
  UID: UE.V2.ENT.SPC.VIS.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for VISUAL_SPC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/05_VISUAL_SPC_ENT/00__INDEX_MANIFEST__VIS__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/05_VISUAL_SPC_ENT/00__INDEX_MANIFEST__VIS__SPC__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.SPC.VIS.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for VISUAL_SPC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/05_VISUAL_SPC_ENT/00__INDEX_MANIFEST__VIS__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/05_VISUAL_SPC_ENT/00__INDEX_MANIFEST__VIS__SPC__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.SPC.VIS.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Realm step-run navigator
  DESC: KEY-only contract; resolves targets via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/05_VISUAL_SPC_ENT/00__PIPELINE_CONTRACT__VIS__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/05_VISUAL_SPC_ENT/00__PIPELINE_CONTRACT__VIS__SPC__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (visual specialists)

- KEY: SPC.VIS.VISUAL_DIRECTOR
  UID:
  KIND: ENTITY
  ROLE: Visual direction owner
  DESC: Owns visual intent and coherence; approves final visual direction and constraints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/05_VISUAL_SPC_ENT/01__VIS__VISUAL_DIRECTOR__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/05_VISUAL_SPC_ENT/01__VIS__VISUAL_DIRECTOR__SPC__ENT.md
  MARKERS: [SPC, VIS, SPECIALIST, DIR]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.VIS.PRODUCTION_DESIGNER
  UID:
  KIND: ENTITY
  ROLE: Production designer
  DESC: Designs production look: sets, props, materials, era cues; outputs production design frame
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/05_VISUAL_SPC_ENT/02__VIS__PRODUCTION_DESIGNER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/05_VISUAL_SPC_ENT/02__VIS__PRODUCTION_DESIGNER__SPC__ENT.md
  MARKERS: [SPC, VIS, SPECIALIST, PROD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.VIS.SCENE_VISUALIZATION_SPECIALIST
  UID:
  KIND: ENTITY
  ROLE: Scene visualization specialist
  DESC: Converts narrative beats into visual scene plans; outputs visualization briefs and shot-level notes
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/05_VISUAL_SPC_ENT/03__VIS__SCENE_VISUALIZATION_SPECIALIST__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/05_VISUAL_SPC_ENT/03__VIS__SCENE_VISUALIZATION_SPECIALIST__SPC__ENT.md
  MARKERS: [SPC, VIS, SPECIALIST, SCENE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.VIS.STORYBOARD_ARTIST
  UID:
  KIND: ENTITY
  ROLE: Storyboard artist
  DESC: Produces storyboard frames and camera continuity; outputs storyboard pack for sequences
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/05_VISUAL_SPC_ENT/04__VIS__STORYBOARD_ARTIST__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/05_VISUAL_SPC_ENT/04__VIS__STORYBOARD_ARTIST__SPC__ENT.md
  MARKERS: [SPC, VIS, SPECIALIST, BOARD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.VIS.CINEMATOGRAPHER
  UID:
  KIND: ENTITY
  ROLE: Cinematographer
  DESC: Owns camera/lens/lighting intent; outputs cinematography constraints and shot grammar
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/05_VISUAL_SPC_ENT/05__VIS__CINEMATOGRAPHER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/05_VISUAL_SPC_ENT/05__VIS__CINEMATOGRAPHER__SPC__ENT.md
  MARKERS: [SPC, VIS, SPECIALIST, CAM]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.VIS.CAMERA_MOVEMENT_SPECIALIST
  UID:
  KIND: ENTITY
  ROLE: Camera movement specialist
  DESC: Designs camera movement patterns; outputs movement plan, continuity checks, and constraints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/05_VISUAL_SPC_ENT/06__VIS__CAMERA_MOVEMENT_SPECIALIST__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/05_VISUAL_SPC_ENT/06__VIS__CAMERA_MOVEMENT_SPECIALIST__SPC__ENT.md
  MARKERS: [SPC, VIS, SPECIALIST, MOVE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31
