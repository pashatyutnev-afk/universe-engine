FILE: UE_V2/00_BOOT/00__INDEX_MANIFEST__BOOT.md
SCOPE: UE_V2 / 00_BOOT
DOC_TYPE: INDEX_MANIFEST
DOMAIN: BOOT
UID: UE.V2.BOOT.INDEX_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: RAW lives here only

---

## [M] PURPOSE
INDEX_MANIFEST — “таблица адресов” и кратких смыслов для реалма 00_BOOT.
Хранит RAW и машинные паспорта BOOT-доков. Никаких “историй” и длинных объяснений.

## [M] HARD_RULES
- RAW ссылки допускаются только тут (и в ROOT LINK BASE / START по закону системы).
- Любая навигация по 00_BOOT выполняется через KEY → RAW.
- PIPELINE_CONTRACT ссылается только на KEY.
- SELF запись обязательна.
- Не обходить через PATH при наличии RAW (PATH хранится как справка).

## [M] INDEX_CONTEXT
- REALM_ID: UE_V2/00_BOOT
- FOLDER_NAME: 00_BOOT
- INDEX_SCOPE_TAGS: [BOOT, SYS, NAV]

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
  UID: UE.V2.BOOT.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Self pointer for deterministic nav
  DESC: This index-manifest file for 00_BOOT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/00__INDEX_MANIFEST__BOOT.md
  PATH: UE_V2/00_BOOT/00__INDEX_MANIFEST__BOOT.md
  MARKERS: [INDEX, SELF]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [M] REQUIRED (минимум для реалма)
- KEY: INDEX_MANIFEST
  UID: UE.V2.BOOT.INDEX_MANIFEST.001
  KIND: FILE
  ROLE: Address table for realm
  DESC: Raw addresses + short meaning for 00_BOOT
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/00__INDEX_MANIFEST__BOOT.md
  PATH: UE_V2/00_BOOT/00__INDEX_MANIFEST__BOOT.md
  MARKERS: [INDEX, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: PIPELINE_CONTRACT
  UID: UE.V2.BOOT.PIPELINE_CONTRACT.001
  KIND: PIPE
  ROLE: Realm step-run navigator
  DESC: KEY-only contract; resolves targets via this INDEX_MANIFEST
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/00__PIPELINE_CONTRACT__BOOT.md
  PATH: UE_V2/00_BOOT/00__PIPELINE_CONTRACT__BOOT.md
  MARKERS: [PIPE, MUST_LOAD, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

### [O] CONTENT (boot set)

- KEY: BOOT.ROOT_LINK_BASE.PART1
  UID:
  KIND: FILE
  ROLE: Root link base part 1
  DESC: RAW map (part 1) for deterministic navigation
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/00__ROOT_LINK_BASE_UE_V2__PART1.md
  PATH: UE_V2/00_BOOT/00__ROOT_LINK_BASE_UE_V2__PART1.md
  MARKERS: [BOOT, NAV, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: BOOT.ROOT_LINK_BASE.PART2
  UID:
  KIND: FILE
  ROLE: Root link base part 2
  DESC: RAW map (part 2) for deterministic navigation
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/00__ROOT_LINK_BASE_UE_V2__PART2.md
  PATH: UE_V2/00_BOOT/00__ROOT_LINK_BASE_UE_V2__PART2.md
  MARKERS: [BOOT, NAV, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: BOOT.START
  UID:
  KIND: FILE
  ROLE: Boot entrypoint
  DESC: Start instructions and first opens
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/00__START.md
  PATH: UE_V2/00_BOOT/00__START.md
  MARKERS: [BOOT, ENTRYPOINT, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: BOOT.BOOT_SEQ
  UID:
  KIND: FILE
  ROLE: Boot sequence
  DESC: Deterministic boot ordering and minimal opens
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/01__BOOT_SEQ.md
  PATH: UE_V2/00_BOOT/01__BOOT_SEQ.md
  MARKERS: [BOOT, NAV]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: BOOT.STOP_GAP
  UID:
  KIND: FILE
  ROLE: Stop/gap rules
  DESC: STOP and GAP conditions for boot/runtime
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/02__STOP_GAP.md
  PATH: UE_V2/00_BOOT/02__STOP_GAP.md
  MARKERS: [BOOT, GATE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: BOOT.CHAT_FMT
  UID:
  KIND: FILE
  ROLE: Chat format standard (boot)
  DESC: Canon chat format rules used at runtime
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/03__CHAT_FMT.md
  PATH: UE_V2/00_BOOT/03__CHAT_FMT.md
  MARKERS: [BOOT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: BOOT.ART_RULE
  UID:
  KIND: FILE
  ROLE: Artifact rule
  DESC: Artifact-only rule and packaging expectations
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/04__ART_RULE.md
  PATH: UE_V2/00_BOOT/04__ART_RULE.md
  MARKERS: [BOOT, ARTIFACT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: BOOT.MIN_ENT
  UID:
  KIND: FILE
  ROLE: Minimal entities
  DESC: Minimal entity set required for runtime
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/05__MIN_ENT.md
  PATH: UE_V2/00_BOOT/05__MIN_ENT.md
  MARKERS: [BOOT, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: BOOT.TRACE
  UID:
  KIND: FILE
  ROLE: Trace protocol
  DESC: Traceability rules and logging discipline
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/06__TRACE.md
  PATH: UE_V2/00_BOOT/06__TRACE.md
  MARKERS: [BOOT, TRACE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: BOOT.FAIL_CODES
  UID:
  KIND: FILE
  ROLE: Failure codes registry
  DESC: Canon FAIL codes for STOP and errors
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/07__FAIL_CODES.md
  PATH: UE_V2/00_BOOT/07__FAIL_CODES.md
  MARKERS: [BOOT, FAIL]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: BOOT.RUNTIME_MANIFEST
  UID:
  KIND: FILE
  ROLE: Runtime manifest
  DESC: Runtime components list and constraints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/08__RUNTIME_MANIFEST.md
  PATH: UE_V2/00_BOOT/08__RUNTIME_MANIFEST.md
  MARKERS: [BOOT, RUNTIME, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: BOOT.TASK_ROUTER
  UID:
  KIND: FILE
  ROLE: Task router
  DESC: Routing rules from task text to realm actions
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/09__TASK_ROUTER.md
  PATH: UE_V2/00_BOOT/09__TASK_ROUTER.md
  MARKERS: [BOOT, ROUTER]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: BOOT.STEP_RUN_PROTOCOL
  UID:
  KIND: FILE
  ROLE: Step-run protocol
  DESC: Canon step-run execution model
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/10__STEP_RUN_PROTOCOL.md
  PATH: UE_V2/00_BOOT/10__STEP_RUN_PROTOCOL.md
  MARKERS: [BOOT, PIPE, MUST_LOAD]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: BOOT.CHANGELOG
  UID:
  KIND: LOG
  ROLE: Boot changelog
  DESC: Append-only changes for boot realm
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/11__CHANGELOG.md
  PATH: UE_V2/00_BOOT/11__CHANGELOG.md
  MARKERS: [LOG, BOOT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: BOOT.FOCUS_LOOP_PROTOCOL
  UID:
  KIND: FILE
  ROLE: Focus loop protocol
  DESC: Focus loop execution discipline
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/12__FOCUS_LOOP_PROTOCOL.md
  PATH: UE_V2/00_BOOT/12__FOCUS_LOOP_PROTOCOL.md
  MARKERS: [BOOT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: BOOT.COMMANDS
  UID:
  KIND: FILE
  ROLE: Commands registry
  DESC: Canon commands and invocation format
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/13__COMMANDS.md
  PATH: UE_V2/00_BOOT/13__COMMANDS.md
  MARKERS: [BOOT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: BOOT.NAV_STACK_LAW
  UID:
  KIND: LAW
  ROLE: Navigation stack law
  DESC: Law governing nav stack and deterministic opens
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/14__NAV_STACK_LAW.md
  PATH: UE_V2/00_BOOT/14__NAV_STACK_LAW.md
  MARKERS: [LAW, NAV]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: BOOT.NAV_STACK_TEMPLATES
  UID:
  KIND: TPL
  ROLE: Nav stack templates
  DESC: Templates used by nav stack execution
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/15__NAV_STACK_TEMPLATES.md
  PATH: UE_V2/00_BOOT/15__NAV_STACK_TEMPLATES.md
  MARKERS: [TPL, NAV]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: BOOT.FOLDER_SYSTEM_FILES_STANDARD
  UID:
  KIND: STD
  ROLE: Folder system files standard
  DESC: Standard system files per folder and naming
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/16__FOLDER_SYSTEM_FILES_STANDARD.md
  PATH: UE_V2/00_BOOT/16__FOLDER_SYSTEM_FILES_STANDARD.md
  MARKERS: [STD, BOOT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: BOOT.NUMBERING_POLICY
  UID:
  KIND: STD
  ROLE: Numbering policy
  DESC: Numbering policy and ordering constraints
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/17__NUMBERING_POLICY.md
  PATH: UE_V2/00_BOOT/17__NUMBERING_POLICY.md
  MARKERS: [STD, BOOT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: BOOT.TEMPLATE_DISCOVERY_POLICY
  UID:
  KIND: STD
  ROLE: Template discovery policy
  DESC: How templates are discovered and validated
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/18__TEMPLATE_DISCOVERY_POLICY.md
  PATH: UE_V2/00_BOOT/18__TEMPLATE_DISCOVERY_POLICY.md
  MARKERS: [STD, BOOT, TPL]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: BOOT.ROUTER_VS_PIPELINE_CONFLICT_RULE
  UID:
  KIND: LAW
  ROLE: Router vs pipeline conflict rule
  DESC: Conflict resolution between router and pipeline
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/19__ROUTER_VS_PIPELINE_CONFLICT_RULE.md
  PATH: UE_V2/00_BOOT/19__ROUTER_VS_PIPELINE_CONFLICT_RULE.md
  MARKERS: [LAW, ROUTER, PIPE]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: BOOT.WORK_UNITS_STANDARD
  UID:
  KIND: STD
  ROLE: Work units standard
  DESC: Work units definition and packaging discipline
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/20__WORK_UNITS_STANDARD.md
  PATH: UE_V2/00_BOOT/20__WORK_UNITS_STANDARD.md
  MARKERS: [STD, BOOT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: BOOT.RESUME_TOKEN
  UID:
  KIND: STD
  ROLE: Resume token
  DESC: Resume token schema and usage rules
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/21__RESUME_TOKEN.md
  PATH: UE_V2/00_BOOT/21__RESUME_TOKEN.md
  MARKERS: [STD, TOKEN]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: BOOT.PATCH_PROTOCOL
  UID:
  KIND: STD
  ROLE: Patch protocol
  DESC: Patch protocol and patch packaging
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/22__PATCH_PROTOCOL.md
  PATH: UE_V2/00_BOOT/22__PATCH_PROTOCOL.md
  MARKERS: [STD, PATCH]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: BOOT.START_PROFILES
  UID:
  KIND: FILE
  ROLE: Start profiles
  DESC: Profiles for starting modes and boot presets
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/23__START_PROFILES.md
  PATH: UE_V2/00_BOOT/23__START_PROFILES.md
  MARKERS: [BOOT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31

- KEY: BOOT.CHECKPOINT_RULES
  UID:
  KIND: STD
  ROLE: Checkpoint rules
  DESC: Checkpoint creation and validation rules
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00_BOOT/24__CHECKPOINT_RULES.md
  PATH: UE_V2/00_BOOT/24__CHECKPOINT_RULES.md
  MARKERS: [STD, BOOT]
  STATUS: ACTIVE
  OWNER: SYS
  UPDATED: 2026-01-31
