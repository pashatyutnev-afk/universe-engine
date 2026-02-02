FILE: UE_V2/03_ENT/30_ORC_ENT/04_VIDEO_ORC_ENT/00__INDEX_MANIFEST__VID__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 04_VIDEO_ORC_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: VID_ORC_ENT
UID: UE.V2.ENT.IDX.VID_ORC_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — адресная таблица реалма 04_VIDEO_ORC_ENT.
Хранит KEYS, короткий смысл, RAW и PATH (как справка). Без длинных историй.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- Коротко: 1–2 строки смысла. Без лирики.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/30_ORC_ENT/04_VIDEO_ORC_ENT
- FOLDER_NAME: 04_VIDEO_ORC_ENT
- INDEX_SCOPE_TAGS: [ENT, ORC, VIDEO]

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
  UID: UE.V2.ENT.IDX.VID_ORC_ENT.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 04_VIDEO_ORC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/04_VIDEO_ORC_ENT/00__INDEX_MANIFEST__VID__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/04_VIDEO_ORC_ENT/00__INDEX_MANIFEST__VID__ORC__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.IDX.VID_ORC_ENT.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for 04_VIDEO_ORC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/04_VIDEO_ORC_ENT/00__INDEX_MANIFEST__VID__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/04_VIDEO_ORC_ENT/00__INDEX_MANIFEST__VID__ORC__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.PIPE.VID_ORC_ENT.001
  KIND: PIPE
  ROLE: Navigator for realm actions
  DESC: Uses KEYS, resolves RAW via INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/04_VIDEO_ORC_ENT/00__PIPELINE_CONTRACT__VID__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/04_VIDEO_ORC_ENT/00__PIPELINE_CONTRACT__VID__ORC__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

### [O] VIDEO ORC ENT (modules)
- KEY: VID.BRIEF_FACTORY
  UID:
  KIND: FILE
  ROLE: Video brief factory
  DESC: Builds video brief: scene, subject, constraints, duration, resolution, style slots
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/04_VIDEO_ORC_ENT/01__VID__BRIEF_FACTORY__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/04_VIDEO_ORC_ENT/01__VID__BRIEF_FACTORY__ORC__ENT.md
  MARKERS: [VID, BRIEF, NAV]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: VID.SHOT_PLANNER
  UID:
  KIND: FILE
  ROLE: Shot planner
  DESC: Plans shots: beats, camera, transitions, style-change timings
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/04_VIDEO_ORC_ENT/02__VID__SHOT_PLANNER__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/04_VIDEO_ORC_ENT/02__VID__SHOT_PLANNER__ORC__ENT.md
  MARKERS: [VID, SHOT, PLAN]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: VID.PROMPT_FACTORY
  UID:
  KIND: FILE
  ROLE: Prompt factory
  DESC: Produces generation prompts (Veo/others) from brief + shot plan + constraints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/04_VIDEO_ORC_ENT/03__VID__PROMPT_FACTORY__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/04_VIDEO_ORC_ENT/03__VID__PROMPT_FACTORY__ORC__ENT.md
  MARKERS: [VID, PROMPT, OUTPUT]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: VID.STYLE_PACKAGER
  UID:
  KIND: FILE
  ROLE: Style packager
  DESC: Packages style directives and variation slots for multi-style clips
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/04_VIDEO_ORC_ENT/04__VID__STYLE_PACKAGER__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/04_VIDEO_ORC_ENT/04__VID__STYLE_PACKAGER__ORC__ENT.md
  MARKERS: [VID, STYLE, PACK]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: VID.QA_CHECKS
  UID:
  KIND: FILE
  ROLE: QA checks for video artifacts
  DESC: Runs checklist: continuity, style-switch timing, resolution, subject lock, policy
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/04_VIDEO_ORC_ENT/05__VID__QA_CHECKS__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/04_VIDEO_ORC_ENT/05__VID__QA_CHECKS__ORC__ENT.md
  MARKERS: [VID, QA, GATE]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02

- KEY: VID.EXPORT_HANDOFF
  UID:
  KIND: FILE
  ROLE: Export handoff
  DESC: Defines export targets, naming, packaging, and handoff checklist
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/30_ORC_ENT/04_VIDEO_ORC_ENT/06__VID__EXPORT_HANDOFF__ORC__ENT.md
  PATH: UE_V2/03_ENT/30_ORC_ENT/04_VIDEO_ORC_ENT/06__VID__EXPORT_HANDOFF__ORC__ENT.md
  MARKERS: [VID, EXPORT, OUTPUT]
  STATUS: ACTIVE
  OWNER: ORC_ENT
  UPDATED: 2026-02-02
