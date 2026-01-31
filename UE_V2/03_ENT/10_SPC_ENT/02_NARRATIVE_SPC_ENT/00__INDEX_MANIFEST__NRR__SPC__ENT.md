FILE: UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/00__INDEX_MANIFEST__NRR__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 02_NARRATIVE_SPC_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: NRR_SPC
UID: UE.V2.ENT.SPC.NRR.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма NARRATIVE_SPC_ENT.
Хранит RAW и машинные паспорта narrative-специалистов (NRR). Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- Коротко: 1–2 строки смысла. Без лирики.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT
- FOLDER_NAME: 02_NARRATIVE_SPC_ENT
- INDEX_SCOPE_TAGS: [ENT, SPC, NRR]

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
  UID: UE.V2.ENT.SPC.NRR.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for NARRATIVE_SPC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/00__INDEX_MANIFEST__NRR__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/00__INDEX_MANIFEST__NRR__SPC__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.SPC.NRR.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for NARRATIVE_SPC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/00__INDEX_MANIFEST__NRR__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/00__INDEX_MANIFEST__NRR__SPC__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.SPC.NRR.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Realm step-run navigator
  DESC: KEY-only contract; resolves targets via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/00__PIPELINE_CONTRACT__NRR__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/00__PIPELINE_CONTRACT__NRR__SPC__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (narrative specialists)

- KEY: SPC.NRR.EPISODE_SHOWRUNNER
  UID:
  KIND: ENTITY
  ROLE: Episode showrunner
  DESC: Owns episode-level narrative cohesion; decisions on beats, pacing, and priorities
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/01__NRR__EPISODE_SHOWRUNNER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/01__NRR__EPISODE_SHOWRUNNER__SPC__ENT.md
  MARKERS: [SPC, NRR, SPECIALIST, EP]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.NRR.HEAD_WRITER
  UID:
  KIND: ENTITY
  ROLE: Head writer
  DESC: Owns writers-room coherence; guards tone, constraints, and canon alignment
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/02__NRR__HEAD_WRITER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/02__NRR__HEAD_WRITER__SPC__ENT.md
  MARKERS: [SPC, NRR, SPECIALIST, ROOM]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.NRR.STORY_ARCHITECT
  UID:
  KIND: ENTITY
  ROLE: Story architect
  DESC: Designs story structure across episodes/arcs; outputs structure + constraints + cross-check list
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/03__NRR__STORY_ARCHITECT__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/03__NRR__STORY_ARCHITECT__SPC__ENT.md
  MARKERS: [SPC, NRR, SPECIALIST, STRUCT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.NRR.DRAMATURG
  UID:
  KIND: ENTITY
  ROLE: Dramaturg
  DESC: Validates dramatic logic, stakes, and tension; flags contradictions and weak causality
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/04__NRR__DRAMATURG__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/04__NRR__DRAMATURG__SPC__ENT.md
  MARKERS: [SPC, NRR, SPECIALIST, DRAMA]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.NRR.SCREENWRITER
  UID:
  KIND: ENTITY
  ROLE: Screenwriter
  DESC: Writes scenes and sequences to spec; outputs scene drafts aligned to story structure
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/05__NRR__SCREENWRITER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/05__NRR__SCREENWRITER__SPC__ENT.md
  MARKERS: [SPC, NRR, SPECIALIST, SCRIPT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.NRR.DIALOGUE_WRITER
  UID:
  KIND: ENTITY
  ROLE: Dialogue writer
  DESC: Tunes dialogue for subtext, voice, rhythm; outputs dialogue revisions and voice checks
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/06__NRR__DIALOGUE_WRITER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/06__NRR__DIALOGUE_WRITER__SPC__ENT.md
  MARKERS: [SPC, NRR, SPECIALIST, DLG]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.NRR.CLIFFHANGER_SPECIALIST
  UID:
  KIND: ENTITY
  ROLE: Cliffhanger specialist
  DESC: Designs cliffhangers and episode-end hooks; outputs hook options + risk notes
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/07__NRR__CLIFFHANGER_SPECIALIST__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/07__NRR__CLIFFHANGER_SPECIALIST__SPC__ENT.md
  MARKERS: [SPC, NRR, SPECIALIST, HOOK]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.NRR.EMOTIONAL_ARC_DESIGNER
  UID:
  KIND: ENTITY
  ROLE: Emotional arc designer
  DESC: Designs emotional arc and turning points; outputs emotion curve + anchors per beat
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/08__NRR__EMOTIONAL_ARC_DESIGNER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/08__NRR__EMOTIONAL_ARC_DESIGNER__SPC__ENT.md
  MARKERS: [SPC, NRR, SPECIALIST, EMO]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.NRR.THEME_MEANING_CURATOR
  UID:
  KIND: ENTITY
  ROLE: Theme and meaning curator
  DESC: Guards theme axis and meaning coherence; outputs theme map + motif anchors
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/09__NRR__THEME_MEANING_CURATOR__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/09__NRR__THEME_MEANING_CURATOR__SPC__ENT.md
  MARKERS: [SPC, NRR, SPECIALIST, THEME]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.NRR.LORE_MASTER
  UID:
  KIND: ENTITY
  ROLE: Lore master
  DESC: Controls lore consistency and canon links; outputs lore constraints and required xrefs
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/10__NRR__LORE_MASTER__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/10__NRR__LORE_MASTER__SPC__ENT.md
  MARKERS: [SPC, NRR, SPECIALIST, LORE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.NRR.NOVELIST
  UID:
  KIND: ENTITY
  ROLE: Novelist
  DESC: Converts narrative into prose chapters; outputs chapter drafts aligned to canon constraints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/11__NRR__NOVELIST__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/02_NARRATIVE_SPC_ENT/11__NRR__NOVELIST__SPC__ENT.md
  MARKERS: [SPC, NRR, SPECIALIST, PROSE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31
