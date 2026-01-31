FILE: UE_V2/03_ENT/10_SPC_ENT/03_CHARACTER_SPC_ENT/00__INDEX_MANIFEST__CHR__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 03_CHARACTER_SPC_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: CHR_SPC
UID: UE.V2.ENT.SPC.CHR.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма CHARACTER_SPC_ENT.
Хранит RAW и машинные паспорта character-специалистов (CHR). Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- Коротко: 1–2 строки смысла. Без лирики.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/10_SPC_ENT/03_CHARACTER_SPC_ENT
- FOLDER_NAME: 03_CHARACTER_SPC_ENT
- INDEX_SCOPE_TAGS: [ENT, SPC, CHR]

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
  UID: UE.V2.ENT.SPC.CHR.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for CHARACTER_SPC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/03_CHARACTER_SPC_ENT/00__INDEX_MANIFEST__CHR__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/03_CHARACTER_SPC_ENT/00__INDEX_MANIFEST__CHR__SPC__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.SPC.CHR.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for CHARACTER_SPC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/03_CHARACTER_SPC_ENT/00__INDEX_MANIFEST__CHR__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/03_CHARACTER_SPC_ENT/00__INDEX_MANIFEST__CHR__SPC__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.SPC.CHR.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Realm step-run navigator
  DESC: KEY-only contract; resolves targets via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/03_CHARACTER_SPC_ENT/00__PIPELINE_CONTRACT__CHR__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/03_CHARACTER_SPC_ENT/00__PIPELINE_CONTRACT__CHR__SPC__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (character specialists)

- KEY: SPC.CHR.CHARACTER_ARCHITECT
  UID:
  KIND: ENTITY
  ROLE: Character architecture owner
  DESC: Defines character core, invariants, arc constraints, and canon-safe evolution surface
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/03_CHARACTER_SPC_ENT/01__CHR__CHARACTER_ARCHITECT__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/03_CHARACTER_SPC_ENT/01__CHR__CHARACTER_ARCHITECT__SPC__ENT.md
  MARKERS: [SPC, CHR, SPECIALIST, ARCH]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.CHR.PERSONALITY_PSYCHOLOGIST
  UID:
  KIND: ENTITY
  ROLE: Personality psychologist
  DESC: Models personality traits, coping styles, and behavior consistency; outputs personality frame
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/03_CHARACTER_SPC_ENT/02__CHR__PERSONALITY_PSYCHOLOGIST__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/03_CHARACTER_SPC_ENT/02__CHR__PERSONALITY_PSYCHOLOGIST__SPC__ENT.md
  MARKERS: [SPC, CHR, SPECIALIST, PSY]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.CHR.TRAUMA_MOTIVATION_DESIGNER
  UID:
  KIND: ENTITY
  ROLE: Trauma and motivation designer
  DESC: Defines trauma patterns, motivations, inner conflicts, triggers; outputs motivation map and constraints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/03_CHARACTER_SPC_ENT/03__CHR__TRAUMA_MOTIVATION_DESIGNER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/03_CHARACTER_SPC_ENT/03__CHR__TRAUMA_MOTIVATION_DESIGNER__SPC__ENT.md
  MARKERS: [SPC, CHR, SPECIALIST, MOTIVE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.CHR.RELATIONSHIP_DYNAMICS_DESIGNER
  UID:
  KIND: ENTITY
  ROLE: Relationship dynamics designer
  DESC: Designs relationship dynamics, power balance, bonds, conflict loops; outputs relationship grid + risks
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/03_CHARACTER_SPC_ENT/04__CHR__RELATIONSHIP_DYNAMICS_DESIGNER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/03_CHARACTER_SPC_ENT/04__CHR__RELATIONSHIP_DYNAMICS_DESIGNER__SPC__ENT.md
  MARKERS: [SPC, CHR, SPECIALIST, REL]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.CHR.DIALOGUE_BEHAVIOR_ANALYST
  UID:
  KIND: ENTITY
  ROLE: Dialogue and behavior analyst
  DESC: Analyzes dialogue/behavior consistency; flags out-of-character lines; outputs correction notes
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/03_CHARACTER_SPC_ENT/05__CHR__DIALOGUE_BEHAVIOR_ANALYST__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/03_CHARACTER_SPC_ENT/05__CHR__DIALOGUE_BEHAVIOR_ANALYST__SPC__ENT.md
  MARKERS: [SPC, CHR, SPECIALIST, DLG]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.CHR.CHARACTER_EVOLUTION_SUPERVISOR
  UID:
  KIND: ENTITY
  ROLE: Character evolution supervisor
  DESC: Supervises character evolution across arcs; ensures continuity; outputs evolution checkpoints + canon locks
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/03_CHARACTER_SPC_ENT/06__CHR__CHARACTER_EVOLUTION_SUPERVISOR__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/03_CHARACTER_SPC_ENT/06__CHR__CHARACTER_EVOLUTION_SUPERVISOR__SPC__ENT.md
  MARKERS: [SPC, CHR, SPECIALIST, ARC]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31
