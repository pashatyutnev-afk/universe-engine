FILE: UE_V2/03_ENT/10_SPC_ENT/08_PSYCHOLOGY_SPC_ENT/00__INDEX_MANIFEST__PSY__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 08_PSYCHOLOGY_SPC_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: PSY_SPC
UID: UE.V2.ENT.SPC.PSY.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма PSYCHOLOGY_SPC_ENT.
Хранит RAW и машинные паспорта psychology-специалистов (PSY). Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- Коротко: 1–2 строки смысла. Без лирики.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/10_SPC_ENT/08_PSYCHOLOGY_SPC_ENT
- FOLDER_NAME: 08_PSYCHOLOGY_SPC_ENT
- INDEX_SCOPE_TAGS: [ENT, SPC, PSY]

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
  UID: UE.V2.ENT.SPC.PSY.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for PSYCHOLOGY_SPC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/08_PSYCHOLOGY_SPC_ENT/00__INDEX_MANIFEST__PSY__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/08_PSYCHOLOGY_SPC_ENT/00__INDEX_MANIFEST__PSY__SPC__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.SPC.PSY.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for PSYCHOLOGY_SPC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/08_PSYCHOLOGY_SPC_ENT/00__INDEX_MANIFEST__PSY__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/08_PSYCHOLOGY_SPC_ENT/00__INDEX_MANIFEST__PSY__SPC__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.SPC.PSY.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Realm step-run navigator
  DESC: KEY-only contract; resolves targets via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/08_PSYCHOLOGY_SPC_ENT/00__PIPELINE_CONTRACT__PSY__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/08_PSYCHOLOGY_SPC_ENT/00__PIPELINE_CONTRACT__PSY__SPC__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (psychology specialists)

- KEY: SPC.PSY.VIEWER_PSYCHOLOGY_ANALYST
  UID:
  KIND: ENTITY
  ROLE: Viewer psychology analyst
  DESC: Models audience perception and attention; outputs viewer response predictions and risks
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/08_PSYCHOLOGY_SPC_ENT/01__PSY__VIEWER_PSYCHOLOGY_ANALYST__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/08_PSYCHOLOGY_SPC_ENT/01__PSY__VIEWER_PSYCHOLOGY_ANALYST__SPC__ENT.md
  MARKERS: [SPC, PSY, SPECIALIST, VIEWER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.PSY.EMPATHY_IDENTIFICATION_SPECIALIST
  UID:
  KIND: ENTITY
  ROLE: Empathy and identification specialist
  DESC: Designs empathy hooks and identification pathways; outputs empathy map and constraints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/08_PSYCHOLOGY_SPC_ENT/02__PSY__EMPATHY_IDENTIFICATION_SPECIALIST__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/08_PSYCHOLOGY_SPC_ENT/02__PSY__EMPATHY_IDENTIFICATION_SPECIALIST__SPC__ENT.md
  MARKERS: [SPC, PSY, SPECIALIST, EMP]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.PSY.EMOTIONAL_IMPACT_DESIGNER
  UID:
  KIND: ENTITY
  ROLE: Emotional impact designer
  DESC: Designs emotional impact curve and target reactions; outputs impact plan and checkpoints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/08_PSYCHOLOGY_SPC_ENT/03__PSY__EMOTIONAL_IMPACT_DESIGNER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/08_PSYCHOLOGY_SPC_ENT/03__PSY__EMOTIONAL_IMPACT_DESIGNER__SPC__ENT.md
  MARKERS: [SPC, PSY, SPECIALIST, IMPACT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.PSY.NONVERBAL_BEHAVIOR_ANALYST
  UID:
  KIND: ENTITY
  ROLE: Nonverbal behavior analyst
  DESC: Analyzes body language and nonverbal signals; outputs nonverbal consistency notes
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/08_PSYCHOLOGY_SPC_ENT/04__PSY__NONVERBAL_BEHAVIOR_ANALYST__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/08_PSYCHOLOGY_SPC_ENT/04__PSY__NONVERBAL_BEHAVIOR_ANALYST__SPC__ENT.md
  MARKERS: [SPC, PSY, SPECIALIST, NVRB]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.PSY.BEHAVIORAL_CONSISTENCY_SPECIALIST
  UID:
  KIND: ENTITY
  ROLE: Behavioral consistency specialist
  DESC: Ensures behavioral consistency across arcs/scenes; outputs violation list and correction plan
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/08_PSYCHOLOGY_SPC_ENT/05__PSY__BEHAVIORAL_CONSISTENCY_SPECIALIST__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/08_PSYCHOLOGY_SPC_ENT/05__PSY__BEHAVIORAL_CONSISTENCY_SPECIALIST__SPC__ENT.md
  MARKERS: [SPC, PSY, SPECIALIST, CONSIST]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31
