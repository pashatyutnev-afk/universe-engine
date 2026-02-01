FILE: UE_V2/03_ENT/20_ENG_ENT/03_CHARACTER_ENG_ENT/00__INDEX_MANIFEST__CHR__ENG__ENT.md
SCOPE: UE_V2 / 03_ENT / 20_ENG_ENT / 03_CHARACTER_ENG_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: CHR_ENG
UID: UE.V2.ENT.ENG.CHR.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма CHARACTER_ENG_ENT (CHR).
Хранит RAW и машинные паспорта CHR-движков. Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Любая навигация по реалму: KEY -> resolve RAW here -> open.
- PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).
- NO GUESSING: для движков RAW заполняем только после фиксации кнопкой Raw (иначе GAP).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/20_ENG_ENT/03_CHARACTER_ENG_ENT
- FOLDER_NAME: 03_CHARACTER_ENG_ENT
- INDEX_SCOPE_TAGS: [ENT, ENG, CHR]

## [M] KEYSPACE
KEY_FORMAT: CHR.
RESOLUTION_RULE: KEY -> RAW берётся только из ENTRIES ниже

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
  UID: UE.V2.ENT.ENG.CHR.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for CHARACTER_ENG_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/03_CHARACTER_ENG_ENT/00__INDEX_MANIFEST__CHR__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/03_CHARACTER_ENG_ENT/00__INDEX_MANIFEST__CHR__ENG__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (minimum for realm)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.ENG.CHR.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for CHR engines
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/03_CHARACTER_ENG_ENT/00__INDEX_MANIFEST__CHR__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/03_CHARACTER_ENG_ENT/00__INDEX_MANIFEST__CHR__ENG__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.ENG.CHR.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Realm step-run navigator
  DESC: KEY-only contract; resolves targets via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/03_CHARACTER_ENG_ENT/00__PIPELINE_CONTRACT__CHR__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/03_CHARACTER_ENG_ENT/00__PIPELINE_CONTRACT__CHR__ENG__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (CHR engines)
- KEY: CHR.CHARACTER_CORE
  UID:
  KIND: ENTITY
  ROLE: Character core engine
  DESC: Core identity, traits, contradictions; emits CHARACTER_CORE_TOKEN
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/03_CHARACTER_ENG_ENT/01__CHR__CHARACTER_CORE__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/03_CHARACTER_ENG_ENT/01__CHR__CHARACTER_CORE__ENG__ENT.md
  MARKERS: [ENG, CHR, CORE]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: CHR.MOTIVATION_DESIRE
  UID:
  KIND: ENTITY
  ROLE: Motivation and desire engine
  DESC: Motivations, needs, goals, obstacles; emits MOTIVATION_MAP
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/03_CHARACTER_ENG_ENT/02__CHR__MOTIVATION_DESIRE__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/03_CHARACTER_ENG_ENT/02__CHR__MOTIVATION_DESIRE__ENG__ENT.md
  MARKERS: [ENG, CHR, MOTIVE]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: CHR.MORAL_VALUE
  UID:
  KIND: ENTITY
  ROLE: Moral and value engine
  DESC: Values, ethics, taboos, breaking points; emits VALUE_AXIS
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/03_CHARACTER_ENG_ENT/03__CHR__MORAL_VALUE__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/03_CHARACTER_ENG_ENT/03__CHR__MORAL_VALUE__ENG__ENT.md
  MARKERS: [ENG, CHR, VALUE]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: CHR.CHARACTER_PSYCHOLOGY
  UID:
  KIND: ENTITY
  ROLE: Character psychology engine
  DESC: Psychology profile, inner conflicts; emits PSY_PROFILE
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/03_CHARACTER_ENG_ENT/04__CHR__CHARACTER_PSYCHOLOGY__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/03_CHARACTER_ENG_ENT/04__CHR__CHARACTER_PSYCHOLOGY__ENG__ENT.md
  MARKERS: [ENG, CHR, PSY]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: CHR.CHARACTER_BEHAVIOR
  UID:
  KIND: ENTITY
  ROLE: Character behavior engine
  DESC: Behavior patterns, impulses, tells; emits BEHAVIOR_PATTERN_SET
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/03_CHARACTER_ENG_ENT/05__CHR__CHARACTER_BEHAVIOR__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/03_CHARACTER_ENG_ENT/05__CHR__CHARACTER_BEHAVIOR__ENG__ENT.md
  MARKERS: [ENG, CHR, BEHAVIOR]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: CHR.RELATIONSHIP
  UID:
  KIND: ENTITY
  ROLE: Relationship engine
  DESC: Relationship dynamics and arcs; emits RELATIONSHIP_MATRIX
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/03_CHARACTER_ENG_ENT/06__CHR__RELATIONSHIP__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/03_CHARACTER_ENG_ENT/06__CHR__RELATIONSHIP__ENG__ENT.md
  MARKERS: [ENG, CHR, REL]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: CHR.DIALOGUE
  UID:
  KIND: ENTITY
  ROLE: Dialogue engine
  DESC: Dialogue logic, subtext, beats; emits DIALOGUE_BEAT_SHEET
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/03_CHARACTER_ENG_ENT/07__CHR__DIALOGUE__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/03_CHARACTER_ENG_ENT/07__CHR__DIALOGUE__ENG__ENT.md
  MARKERS: [ENG, CHR, DIALOGUE]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: CHR.SPEECH_NATURALIZATION
  UID:
  KIND: ENTITY
  ROLE: Speech naturalization engine
  DESC: Natural speech patterns and stylization; emits SPEECH_STYLE_TOKEN
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/03_CHARACTER_ENG_ENT/08__CHR__SPEECH_NATURALIZATION__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/03_CHARACTER_ENG_ENT/08__CHR__SPEECH_NATURALIZATION__ENG__ENT.md
  MARKERS: [ENG, CHR, SPEECH]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: CHR.GROWTH_TRAUMA
  UID:
  KIND: ENTITY
  ROLE: Growth and trauma engine
  DESC: Trauma shaping, healing/growth; emits GROWTH_TRAUMA_ARC
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/03_CHARACTER_ENG_ENT/09__CHR__GROWTH_TRAUMA__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/03_CHARACTER_ENG_ENT/09__CHR__GROWTH_TRAUMA__ENG__ENT.md
  MARKERS: [ENG, CHR, TRAUMA]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: CHR.CHARACTER_EVOLUTION
  UID:
  KIND: ENTITY
  ROLE: Character evolution engine
  DESC: Evolution over time and state transitions; emits CHARACTER_EVOLUTION_MODEL
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/03_CHARACTER_ENG_ENT/10__CHR__CHARACTER_EVOLUTION__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/03_CHARACTER_ENG_ENT/10__CHR__CHARACTER_EVOLUTION__ENG__ENT.md
  MARKERS: [ENG, CHR, EVOLUTION]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

---

## [M] LOAD_HINTS
MIN_SET_KEYS:
- INDEX_MANIFEST
- PIPELINE_CONTRACT

OPTIONAL_KEYS:
- CHR.CHARACTER_CORE
- CHR.MOTIVATION_DESIRE
- CHR.MORAL_VALUE
- CHR.CHARACTER_PSYCHOLOGY
- CHR.CHARACTER_BEHAVIOR
- CHR.RELATIONSHIP
- CHR.DIALOGUE
- CHR.SPEECH_NATURALIZATION
- CHR.GROWTH_TRAUMA
- CHR.CHARACTER_EVOLUTION

## [M] GUARDS
STOP_IF:
- RAW missing for any MIN_SET_KEYS
GAP_IF:
- requested KEY not present in ENTRIES
- any engine RAW not fixed yet (expected during build)
