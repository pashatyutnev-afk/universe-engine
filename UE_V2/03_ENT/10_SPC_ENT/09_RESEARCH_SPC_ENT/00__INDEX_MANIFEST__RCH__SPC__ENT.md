FILE: UE_V2/03_ENT/10_SPC_ENT/09_RESEARCH_SPC_ENT/00__INDEX_MANIFEST__RCH__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 09_RESEARCH_SPC_ENT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: RCH_SPC
UID: UE.V2.ENT.SPC.RCH.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма RESEARCH_SPC_ENT.
Хранит RAW и машинные паспорта research-специалистов (RCH). Без длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Каждый элемент имеет KEY. PIPELINE_CONTRACT ссылается только на KEY.
- Коротко: 1–2 строки смысла. Без лирики.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/03_ENT/10_SPC_ENT/09_RESEARCH_SPC_ENT
- FOLDER_NAME: 09_RESEARCH_SPC_ENT
- INDEX_SCOPE_TAGS: [ENT, SPC, RCH]

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
  UID: UE.V2.ENT.SPC.RCH.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for RESEARCH_SPC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/09_RESEARCH_SPC_ENT/00__INDEX_MANIFEST__RCH__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/09_RESEARCH_SPC_ENT/00__INDEX_MANIFEST__RCH__SPC__ENT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.ENT.SPC.RCH.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for RESEARCH_SPC_ENT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/09_RESEARCH_SPC_ENT/00__INDEX_MANIFEST__RCH__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/09_RESEARCH_SPC_ENT/00__INDEX_MANIFEST__RCH__SPC__ENT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.ENT.SPC.RCH.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Realm step-run navigator
  DESC: KEY-only contract; resolves targets via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/09_RESEARCH_SPC_ENT/00__PIPELINE_CONTRACT__RCH__SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/09_RESEARCH_SPC_ENT/00__PIPELINE_CONTRACT__RCH__SPC__ENT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (research specialists)

- KEY: SPC.RCH.RESEARCH_DIRECTOR
  UID:
  KIND: ENTITY
  ROLE: Research director
  DESC: Owns research strategy and scope; defines what must be proven vs what may be assumed
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/09_RESEARCH_SPC_ENT/01__RCH__RESEARCH_DIRECTOR_SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/09_RESEARCH_SPC_ENT/01__RCH__RESEARCH_DIRECTOR_SPC__ENT.md
  MARKERS: [SPC, RCH, SPECIALIST, LEAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.RCH.SCIENTIFIC_RESEARCHER
  UID:
  KIND: ENTITY
  ROLE: Scientific researcher
  DESC: Provides scientific grounding and constraints; outputs evidence-backed notes and hypotheses boundaries
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/09_RESEARCH_SPC_ENT/02__RCH__SCIENTIFIC_RESEARCHER_SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/09_RESEARCH_SPC_ENT/02__RCH__SCIENTIFIC_RESEARCHER_SPC__ENT.md
  MARKERS: [SPC, RCH, SPECIALIST, SCI]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.RCH.HISTORICAL_RESEARCHER
  UID:
  KIND: ENTITY
  ROLE: Historical researcher
  DESC: Provides historical analogs and timelines; outputs historical references and constraints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/09_RESEARCH_SPC_ENT/03__RCH__HISTORICAL_RESEARCHER_SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/09_RESEARCH_SPC_ENT/03__RCH__HISTORICAL_RESEARCHER_SPC__ENT.md
  MARKERS: [SPC, RCH, SPECIALIST, HIST]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.RCH.CULTURAL_ANTHROPOLOGIST
  UID:
  KIND: ENTITY
  ROLE: Cultural anthropologist
  DESC: Ensures cultural plausibility and social logic; outputs cultural notes and pitfalls
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/09_RESEARCH_SPC_ENT/04__RCH__CULTURAL_ANTHROPOLOGIST_SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/09_RESEARCH_SPC_ENT/04__RCH__CULTURAL_ANTHROPOLOGIST_SPC__ENT.md
  MARKERS: [SPC, RCH, SPECIALIST, CULT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.RCH.KNOWLEDGE_CURATOR
  UID:
  KIND: ENTITY
  ROLE: Knowledge curator
  DESC: Curates KB scope and references; outputs KB_PACK pointers and boundaries
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/09_RESEARCH_SPC_ENT/05__RCH__KNOWLEDGE_CURATOR_SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/09_RESEARCH_SPC_ENT/05__RCH__KNOWLEDGE_CURATOR_SPC__ENT.md
  MARKERS: [SPC, RCH, SPECIALIST, KB]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.RCH.SOURCE_VALIDATION_SPECIALIST
  UID:
  KIND: ENTITY
  ROLE: Source validation specialist
  DESC: Validates sources and trust levels; outputs source grade and exclusion notes
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/09_RESEARCH_SPC_ENT/06__RCH__SOURCE_VALIDATION_SPECIALIST_SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/09_RESEARCH_SPC_ENT/06__RCH__SOURCE_VALIDATION_SPECIALIST_SPC__ENT.md
  MARKERS: [SPC, RCH, SPECIALIST, VAL]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.RCH.FACT_CHECKING_SPECIALIST
  UID:
  KIND: ENTITY
  ROLE: Fact-checking specialist
  DESC: Fact-checks claims vs sources; outputs FACT_CHECK report and corrections list
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/09_RESEARCH_SPC_ENT/07__RCH__FACT_CHECKING_SPECIALIST_SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/09_RESEARCH_SPC_ENT/07__RCH__FACT_CHECKING_SPECIALIST_SPC__ENT.md
  MARKERS: [SPC, RCH, SPECIALIST, FACT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: SPC.RCH.SPECULATIVE_PLAUSIBILITY_ANALYST
  UID:
  KIND: ENTITY
  ROLE: Speculative plausibility analyst
  DESC: Evaluates speculative elements for plausibility; outputs plausibility map and risk notes
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/09_RESEARCH_SPC_ENT/08__RCH__SPECULATIVE_PLAUSIBILITY_ANALYST_SPC__ENT.md
  PATH: UE_V2/03_ENT/10_SPC_ENT/09_RESEARCH_SPC_ENT/08__RCH__SPECULATIVE_PLAUSIBILITY_ANALYST_SPC__ENT.md
  MARKERS: [SPC, RCH, SPECIALIST, RISK]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31
