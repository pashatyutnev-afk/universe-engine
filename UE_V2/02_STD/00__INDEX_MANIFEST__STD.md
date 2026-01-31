FILE: UE_V2/02_STD/00__INDEX_MANIFEST__STD.md
SCOPE: UE_V2 / 02_STD
DOC_TYPE: INDEX_MANIFEST
DOMAIN: STD
UID: UE.V2.STD.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма 02_STD.
Хранит RAW и машинные паспорта STD-доков. Никаких “историй” и длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Любая навигация по 02_STD выполняется через KEY → RAW.
- PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/02_STD
- FOLDER_NAME: 02_STD
- INDEX_SCOPE_TAGS: [STD, SYS]

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
  UID: UE.V2.STD.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 02_STD
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/02_STD/00__INDEX_MANIFEST__STD.md
  PATH: UE_V2/02_STD/00__INDEX_MANIFEST__STD.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.STD.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for 02_STD
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/02_STD/00__INDEX_MANIFEST__STD.md
  PATH: UE_V2/02_STD/00__INDEX_MANIFEST__STD.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.STD.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Realm step-run navigator
  DESC: KEY-only contract; resolves targets via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/02_STD/00__PIPELINE_CONTRACT__STD.md
  PATH: UE_V2/02_STD/00__PIPELINE_CONTRACT__STD.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (standards set)
- KEY: STD.DOC_FMT
  UID:
  KIND: STD
  ROLE: Document format standard
  DESC: Canon structure for docs and sections ordering
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/02_STD/01__DOC_FMT.md
  PATH: UE_V2/02_STD/01__DOC_FMT.md
  MARKERS: [STD, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: STD.NAME_UID
  UID:
  KIND: STD
  ROLE: Naming and UID rules
  DESC: Naming, UID patterns, stability constraints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/02_STD/02__NAME_UID.md
  PATH: UE_V2/02_STD/02__NAME_UID.md
  MARKERS: [STD, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: STD.VER_CHG
  UID:
  KIND: STD
  ROLE: Version and change rules
  DESC: Versioning semantics and changelog discipline
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/02_STD/03__VER_CHG.md
  PATH: UE_V2/02_STD/03__VER_CHG.md
  MARKERS: [STD, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: STD.MARKERS
  UID:
  KIND: STD
  ROLE: Marker system
  DESC: Marker taxonomy and usage constraints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/02_STD/04__MARKERS.md
  PATH: UE_V2/02_STD/04__MARKERS.md
  MARKERS: [STD, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: STD.NAV_RULES
  UID:
  KIND: STD
  ROLE: Navigation rules
  DESC: RAW-only routing, no guessing, resolution discipline
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/02_STD/05__NAV_RULES.md
  PATH: UE_V2/02_STD/05__NAV_RULES.md
  MARKERS: [STD, MUST_LOAD, NAV]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: STD.IDX_RULES
  UID:
  KIND: STD
  ROLE: Index rules
  DESC: Index-manifest rules and deterministic KEY routing
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/02_STD/06__IDX_RULES.md
  PATH: UE_V2/02_STD/06__IDX_RULES.md
  MARKERS: [STD, MUST_LOAD, INDEX]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: STD.TPL_RULES
  UID:
  KIND: STD
  ROLE: Template rules
  DESC: Template discipline and compatibility expectations
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/02_STD/07__TPL_RULES.md
  PATH: UE_V2/02_STD/07__TPL_RULES.md
  MARKERS: [STD, MUST_LOAD, TPL]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: STD.KB_SCOPE
  UID:
  KIND: STD
  ROLE: KB scope standard
  DESC: KB inputs/outputs/boundaries + RAW references discipline
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/02_STD/08__KB_SCOPE.md
  PATH: UE_V2/02_STD/08__KB_SCOPE.md
  MARKERS: [STD, MUST_LOAD, KB]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: STD.GATES
  UID:
  KIND: STD
  ROLE: Gates standard
  DESC: Pass/fail gates definitions and enforcement format
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/02_STD/09__GATES.md
  PATH: UE_V2/02_STD/09__GATES.md
  MARKERS: [STD, MUST_LOAD, GATE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: STD.REPORTS
  UID:
  KIND: STD
  ROLE: Reports standard
  DESC: Reporting formats for audits and compliance
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/02_STD/10__REPORTS.md
  PATH: UE_V2/02_STD/10__REPORTS.md
  MARKERS: [STD, REPORT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: STD.PACKAGING
  UID:
  KIND: STD
  ROLE: Packaging standard
  DESC: Output pack structure and packaging discipline
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/02_STD/11__PACKAGING.md
  PATH: UE_V2/02_STD/11__PACKAGING.md
  MARKERS: [STD, OUTPUT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: STD.NOISE_BUDGET
  UID:
  KIND: STD
  ROLE: Noise budget standard
  DESC: Anti-noise constraints, minimality, allowable texture
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/02_STD/12__NOISE_BUDGET.md
  PATH: UE_V2/02_STD/12__NOISE_BUDGET.md
  MARKERS: [STD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: STD.DICTIONARY_USE
  UID:
  KIND: STD
  ROLE: Dictionary use standard
  DESC: Canon dictionary usage and term discipline
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/02_STD/13__DICTIONARY_USE.md
  PATH: UE_V2/02_STD/13__DICTIONARY_USE.md
  MARKERS: [STD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: STD.CONTRIBUTION_TOKEN_FMT
  UID:
  KIND: STD
  ROLE: Contribution token format
  DESC: Contribution tokens schema and rules
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/02_STD/14__CONTRIBUTION_TOKEN_FMT.md
  PATH: UE_V2/02_STD/14__CONTRIBUTION_TOKEN_FMT.md
  MARKERS: [STD, TOKEN]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: STD.STEP_TOKEN_SET
  UID:
  KIND: STD
  ROLE: Step token set
  DESC: Canon token set for step-run pipelines
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/02_STD/15__STEP_TOKEN_SET.md
  PATH: UE_V2/02_STD/15__STEP_TOKEN_SET.md
  MARKERS: [STD, TOKEN, PIPE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: STD.COVERAGE_RULES
  UID:
  KIND: STD
  ROLE: Coverage rules
  DESC: Coverage requirements and completeness checks
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/02_STD/16__COVERAGE_RULES.md
  PATH: UE_V2/02_STD/16__COVERAGE_RULES.md
  MARKERS: [STD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: STD.QUESTIONS_GATE
  UID:
  KIND: STD
  ROLE: Questions gate
  DESC: When questions are allowed; gating logic for missing inputs
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/02_STD/17__QUESTIONS_GATE.md
  PATH: UE_V2/02_STD/17__QUESTIONS_GATE.md
  MARKERS: [STD, GATE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: STD.PIPELINE_STAGE_MODEL
  UID:
  KIND: STD
  ROLE: Pipeline stage model
  DESC: Canon stage model for pipelines and handoffs
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/02_STD/18__PIPELINE_STAGE_MODEL.md
  PATH: UE_V2/02_STD/18__PIPELINE_STAGE_MODEL.md
  MARKERS: [STD, PIPE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: STD.IO_TYPES
  UID:
  KIND: STD
  ROLE: IO types standard
  DESC: Canon IO types and constraints for artifacts/tokens
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/02_STD/19__IO_TYPES.md
  PATH: UE_V2/02_STD/19__IO_TYPES.md
  MARKERS: [STD, IO]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: STD.SYNTHESIS_TOKEN_FMT
  UID:
  KIND: STD
  ROLE: Synthesis token format
  DESC: Synthesis tokens schema and rules
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/02_STD/22__SYNTHESIS_TOKEN_FMT.md
  PATH: UE_V2/02_STD/22__SYNTHESIS_TOKEN_FMT.md
  MARKERS: [STD, TOKEN]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: STD.SCORE_RUBRIC_FMT
  UID:
  KIND: STD
  ROLE: Score rubric format
  DESC: Rubric schema for scoring and evaluation
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/02_STD/23__SCORE_RUBRIC_FMT.md
  PATH: UE_V2/02_STD/23__SCORE_RUBRIC_FMT.md
  MARKERS: [STD, SCORE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: STD.COMPONENT_TAGS
  UID:
  KIND: STD
  ROLE: Component tags standard
  DESC: Tag taxonomy for components/entities
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/02_STD/24__COMPONENT_TAGS.md
  PATH: UE_V2/02_STD/24__COMPONENT_TAGS.md
  MARKERS: [STD, TAG]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: STD.ENTITY_ADDRESS_LINE_FMT
  UID:
  KIND: STD
  ROLE: Entity address line format
  DESC: Canon address line format for entity headers
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/02_STD/25__ENTITY_ADDRESS_LINE_FMT.md
  PATH: UE_V2/02_STD/25__ENTITY_ADDRESS_LINE_FMT.md
  MARKERS: [STD, ENTITY]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: STD.ENTRYPOINT_PATTERN
  UID:
  KIND: STD
  ROLE: Entrypoint pattern
  DESC: Canon entrypoint pattern and naming constraints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/02_STD/26__ENTRYPOINT_PATTERN.md
  PATH: UE_V2/02_STD/26__ENTRYPOINT_PATTERN.md
  MARKERS: [STD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: STD.SCOPE_GATE_PATTERN
  UID:
  KIND: STD
  ROLE: Scope gate pattern
  DESC: Canon pattern for scope gates and stop conditions
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/02_STD/27__SCOPE_GATE_PATTERN.md
  PATH: UE_V2/02_STD/27__SCOPE_GATE_PATTERN.md
  MARKERS: [STD, GATE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31
