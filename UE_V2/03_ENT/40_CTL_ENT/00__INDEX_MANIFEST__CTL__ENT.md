FILE: UE_V2/03_ENT/40_CTL_ENT/00__INDEX_MANIFEST__CTL__ENT.md
SCOPE: UE_V2 / 03_ENT / 40_CTL_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: CTL_ENT
UID: UE.V2.ENT.IDX.CTL_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: CTL_ENT
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — адресная таблица реалма 40_CTL_ENT.
Хранит RAW и короткие смыслы для CTL-реалмов (Templates, Music, Video, Web, Shared Lib).
Никаких длинных историй.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- Коротко: 1–2 строки смысла. Без лирики.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/40_CTL_ENT
- FOLDER_NAME: 40_CTL_ENT
- INDEX_SCOPE_TAGS: [ENT, CTL]

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
  UID: UE.V2.ENT.IDX.CTL_ENT.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 40_CTL_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/40_CTL_ENT/00__INDEX_MANIFEST__CTL__ENT.md
  PATH: UE_V2/03_ENT/40_CTL_ENT/00__INDEX_MANIFEST__CTL__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: CTL_ENT
  UPDATED: 2026-02-02

### [M] REQUIRED
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.IDX.CTL_ENT.001
  KIND: FILE
  ROLE: Address table for CTL realm
  DESC: RAW addresses + short meaning for 40_CTL_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/40_CTL_ENT/00__INDEX_MANIFEST__CTL__ENT.md
  PATH: UE_V2/03_ENT/40_CTL_ENT/00__INDEX_MANIFEST__CTL__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: CTL_ENT
  UPDATED: 2026-02-02

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.PIPE.CTL_ENT.001
  KIND: PIPE
  ROLE: Router for CTL realm actions
  DESC: Uses KEYS, resolves RAW via INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/40_CTL_ENT/00__PIPELINE_CONTRACT__CTL__ENT.md
  PATH: UE_V2/03_ENT/40_CTL_ENT/00__PIPELINE_CONTRACT__CTL__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: CTL_ENT
  UPDATED: 2026-02-02

- KEY: DOD
  UID: UE.V2.ENT.CTL.DOD.001
  KIND: FILE
  ROLE: Definition of done for CTL realm
  DESC: Completion checklist for 40_CTL_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/40_CTL_ENT/99__DEFINITION_OF_DONE__CTL__ENT.md
  PATH: UE_V2/03_ENT/40_CTL_ENT/99__DEFINITION_OF_DONE__CTL__ENT.md
  MARKERS: [STD, GATE]
  STATUS: ACTIVE
  OWNER: CTL_ENT
  UPDATED: 2026-02-02

### [O] REALMS (subfolders)
- KEY: REALM.TPL_CTL
  UID: UE.V2.ENT.REALM.TPL_CTL.001
  KIND: FOLDER
  ROLE: Templates for CTL documents
  DESC: TPL for CTL entities, blockers, and index skeletons
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/40_CTL_ENT/00_TEMPLATES_CTL_ENT/00__INDEX_MANIFEST__TPL__CTL__ENT.md
  PATH: UE_V2/03_ENT/40_CTL_ENT/00_TEMPLATES_CTL_ENT
  MARKERS: [NAV, TPL, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: CTL_ENT
  UPDATED: 2026-02-02

- KEY: REALM.MUS_CTL
  UID: UE.V2.ENT.REALM.MUS_CTL.001
  KIND: FOLDER
  ROLE: Music controllers realm
  DESC: CTL controllers for music prompts, variants, gates, policies
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS_CTL_ENT/00__INDEX_MANIFEST__MUS__CTL__ENT.md
  PATH: UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS_CTL_ENT
  MARKERS: [NAV, CTL, MUS, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: CTL_ENT
  UPDATED: 2026-02-02

- KEY: REALM.VID_CTL
  UID: UE.V2.ENT.REALM.VID_CTL.001
  KIND: FOLDER
  ROLE: Video controllers realm
  DESC: CTL controllers for video prompts and export constraints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/40_CTL_ENT/20_VIDEO_CONTROLLERS_CTL_ENT/00__INDEX_MANIFEST__VID__CTL__ENT.md
  PATH: UE_V2/03_ENT/40_CTL_ENT/20_VIDEO_CONTROLLERS_CTL_ENT
  MARKERS: [NAV, CTL, VID, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: CTL_ENT
  UPDATED: 2026-02-02

- KEY: REALM.WEB_CTL
  UID: UE.V2.ENT.REALM.WEB_CTL.001
  KIND: FOLDER
  ROLE: Web controllers realm
  DESC: CTL controllers for web blocks, a11y minimum, and lint rules
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/40_CTL_ENT/30_WEB_CONTROLLERS_CTL_ENT/00__INDEX_MANIFEST__WEB__CTL__ENT.md
  PATH: UE_V2/03_ENT/40_CTL_ENT/30_WEB_CONTROLLERS_CTL_ENT
  MARKERS: [NAV, CTL, WEB, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: CTL_ENT
  UPDATED: 2026-02-02

- KEY: REALM.LIB_CTL
  UID: UE.V2.ENT.REALM.LIB_CTL.001
  KIND: FOLDER
  ROLE: Shared CTL library realm
  DESC: Cross-domain libraries and global CTL policies
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/40_CTL_ENT/90_SHARED_LIB_CTL_ENT/00__INDEX_MANIFEST__LIB__CTL__ENT.md
  PATH: UE_V2/03_ENT/40_CTL_ENT/90_SHARED_LIB_CTL_ENT
  MARKERS: [NAV, CTL, LIB, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: CTL_ENT
  UPDATED: 2026-02-02
