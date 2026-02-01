FILE: UE_V2/03_ENT/20_ENG_ENT/02_NARRATIVE_ENG_ENT/00__INDEX_MANIFEST__NRR__ENG__ENT.md
SCOPE: UE_V2 / 03_ENT / 20_ENG_ENT / 02_NARRATIVE_ENG_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: NRR_ENG
UID: UE.V2.ENT.ENG.NRR.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма NARRATIVE_ENG_ENT (NRR).
Хранит RAW и машинные паспорта NRR-движков. Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Любая навигация по реалму: KEY -> resolve RAW here -> open.
- PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).
- NO GUESSING: для движков RAW заполняем только после фиксации кнопкой Raw (иначе GAP).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/20_ENG_ENT/02_NARRATIVE_ENG_ENT
- FOLDER_NAME: 02_NARRATIVE_ENG_ENT
- INDEX_SCOPE_TAGS: [ENT, ENG, NRR]

## [M] KEYSPACE
KEY_FORMAT: NRR.
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
  UID: UE.V2.ENT.ENG.NRR.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for NARRATIVE_ENG_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/02_NARRATIVE_ENG_ENT/00__INDEX_MANIFEST__NRR__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/02_NARRATIVE_ENG_ENT/00__INDEX_MANIFEST__NRR__ENG__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (minimum for realm)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.ENG.NRR.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for NRR engines
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/02_NARRATIVE_ENG_ENT/00__INDEX_MANIFEST__NRR__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/02_NARRATIVE_ENG_ENT/00__INDEX_MANIFEST__NRR__ENG__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.ENG.NRR.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Realm step-run navigator
  DESC: KEY-only contract; resolves targets via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/02_NARRATIVE_ENG_ENT/00__PIPELINE_CONTRACT__NRR__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/02_NARRATIVE_ENG_ENT/00__PIPELINE_CONTRACT__NRR__ENG__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (NRR engines)
- KEY: NRR.NARRATIVE_LOGIC_NAV
  UID:
  KIND: ENTITY
  ROLE: Narrative logic navigator engine
  DESC: Causal logic, constraints, story logic; emits NARRATIVE_LOGIC_TOKEN
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/02_NARRATIVE_ENG_ENT/01__NRR__NARRATIVE_LOGIC_NAV__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/02_NARRATIVE_ENG_ENT/01__NRR__NARRATIVE_LOGIC_NAV__ENG__ENT.md
  MARKERS: [ENG, NRR, LOGIC, NAV]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: NRR.STORY_STRUCTURE_NAV
  UID:
  KIND: ENTITY
  ROLE: Story structure navigator engine
  DESC: Macro structure, beats, acts; emits STORY_STRUCTURE_MAP
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/02_NARRATIVE_ENG_ENT/02__NRR__STORY_STRUCTURE_NAV__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/02_NARRATIVE_ENG_ENT/02__NRR__STORY_STRUCTURE_NAV__ENG__ENT.md
  MARKERS: [ENG, NRR, STRUCT, NAV]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: NRR.DRAMATIC_ARC_NAV
  UID:
  KIND: ENTITY
  ROLE: Dramatic arc navigator engine
  DESC: Dramatic arc model and pressure curve; emits DRAMATIC_ARC_CURVE
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/02_NARRATIVE_ENG_ENT/03__NRR__DRAMATIC_ARC_NAV__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/02_NARRATIVE_ENG_ENT/03__NRR__DRAMATIC_ARC_NAV__ENG__ENT.md
  MARKERS: [ENG, NRR, ARC, NAV]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: NRR.SCENE_CONSTRUCTION_NAV
  UID:
  KIND: ENTITY
  ROLE: Scene construction navigator engine
  DESC: Scene building blocks and composition; emits SCENE_BLUEPRINT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/02_NARRATIVE_ENG_ENT/04__NRR__SCENE_CONSTRUCTION_NAV__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/02_NARRATIVE_ENG_ENT/04__NRR__SCENE_CONSTRUCTION_NAV__ENG__ENT.md
  MARKERS: [ENG, NRR, SCENE, NAV]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: NRR.PACING_RHYTHM_NAV
  UID:
  KIND: ENTITY
  ROLE: Pacing and rhythm navigator engine
  DESC: Pacing, rhythm, tempo control; emits PACING_RHYTHM_MAP
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/02_NARRATIVE_ENG_ENT/05__NRR__PACING_RHYTHM_NAV__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/02_NARRATIVE_ENG_ENT/05__NRR__PACING_RHYTHM_NAV__ENG__ENT.md
  MARKERS: [ENG, NRR, PACING, NAV]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: NRR.TENSION_STAKES_NAV
  UID:
  KIND: ENTITY
  ROLE: Tension and stakes navigator engine
  DESC: Stakes escalation and tension control; emits TENSION_STAKES_CURVE
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/02_NARRATIVE_ENG_ENT/06__NRR__TENSION_STAKES_NAV__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/02_NARRATIVE_ENG_ENT/06__NRR__TENSION_STAKES_NAV__ENG__ENT.md
  MARKERS: [ENG, NRR, TENSION, NAV]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: NRR.FORESHADOWING_NAV
  UID:
  KIND: ENTITY
  ROLE: Foreshadowing navigator engine
  DESC: Setup/payoff planning; emits FORESHADOW_MAP
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/02_NARRATIVE_ENG_ENT/07__NRR__FORESHADOWING_NAV__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/02_NARRATIVE_ENG_ENT/07__NRR__FORESHADOWING_NAV__ENG__ENT.md
  MARKERS: [ENG, NRR, SETUP, NAV]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: NRR.TWIST_REVEAL_NAV
  UID:
  KIND: ENTITY
  ROLE: Twist/reveal navigator engine
  DESC: Twist design and reveal timing; emits TWIST_REVEAL_PLAN
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/02_NARRATIVE_ENG_ENT/08__NRR__TWIST_REVEAL_NAV__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/02_NARRATIVE_ENG_ENT/08__NRR__TWIST_REVEAL_NAV__ENG__ENT.md
  MARKERS: [ENG, NRR, TWIST, NAV]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: NRR.NARRATIVE_CONTINUITY_NAV
  UID:
  KIND: ENTITY
  ROLE: Narrative continuity navigator engine
  DESC: Continuity rules and consistency checks; emits CONTINUITY_CHECKLIST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/02_NARRATIVE_ENG_ENT/09__NRR__NARRATIVE_CONTINUITY_NAV__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/02_NARRATIVE_ENG_ENT/09__NRR__NARRATIVE_CONTINUITY_NAV__ENG__ENT.md
  MARKERS: [ENG, NRR, CONTINUITY, NAV]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: NRR.THEME_MEANING_NAV
  UID:
  KIND: ENTITY
  ROLE: Theme and meaning navigator engine
  DESC: Theme axis and meaning coherence; emits THEME_MEANING_TOKEN
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/20_ENG_ENT/02_NARRATIVE_ENG_ENT/10__NRR__THEME_MEANING_NAV__ENG__ENT.md
  PATH: UE_V2/03_ENT/20_ENG_ENT/02_NARRATIVE_ENG_ENT/10__NRR__THEME_MEANING_NAV__ENG__ENT.md
  MARKERS: [ENG, NRR, THEME, NAV]
  STATUS: DRAFT
  OWNER: SYS
  UPDATED: 2026-01-31

---

## [M] LOAD_HINTS
MIN_SET_KEYS:
- INDEX_MANIFEST
- PIPELINE_CONTRACT

OPTIONAL_KEYS:
- NRR.NARRATIVE_LOGIC_NAV
- NRR.STORY_STRUCTURE_NAV
- NRR.DRAMATIC_ARC_NAV
- NRR.SCENE_CONSTRUCTION_NAV
- NRR.PACING_RHYTHM_NAV
- NRR.TENSION_STAKES_NAV
- NRR.FORESHADOWING_NAV
- NRR.TWIST_REVEAL_NAV
- NRR.NARRATIVE_CONTINUITY_NAV
- NRR.THEME_MEANING_NAV

## [M] GUARDS
STOP_IF:
- RAW missing for any MIN_SET_KEYS
GAP_IF:
- requested KEY not present in ENTRIES
- any engine RAW not fixed yet (expected during build)
