FILE: UE_V2/03_ENT/01_TPL_ENT/20__TPL__ORCHESTRATOR__ENT.md
SCOPE: UE_V2 / 03_ENT / 01_TPL_ENT
DOC_TYPE: TEMPLATE
TEMPLATE_FOR: ENTITY_PASSPORT (ORCHESTRATOR)
DOMAIN: ENT
UID: UE.V2.ENT.TPL.ORCHESTRATOR.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: Template has no RAW

---

## [M] PURPOSE
Шаблон паспорта сущности ORCHESTRATOR.
ORCHESTRATOR собирает WORK_SET, выбирает роли/шаблоны по REG+XREF+KB_SCOPE, запускает STEP-RUN и формирует OUTPUT_PACK.

## [M] HARD_RULES
- Никаких RAW внутри. Только KEYS.
- ROUTING: выбор участников только через REG + XREF + KB_SCOPE (KEYS ONLY).
- STEP-RUN обязателен: каждый этап = одна пачка действий.
- Каждый этап выдаёт NEXT: "го" или FAIL_CODE.
- Не раздувать состав: минимально-достаточный WORK_SET.

## [M] REQUIRED_SECTIONS
- PURPOSE
- ROUTING_RULES
- WORK_SET_POLICY
- STEP_RUN
- INPUTS/OUTPUTS
- INTERFACES (KEYS ONLY)
- KB_SCOPE
- GATES
- CHANGELOG

## [M] FAIL_CODES (canonical)
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.MISSING_KEY
- UE.FAIL.GATE_FAIL
- UE.FAIL.LOG_MISSING

## [M] BODY_TEMPLATE

### ENTITY_HEADER
ENTITY_TYPE: ORCHESTRATOR
ENTITY_NAME: <REPLACE_ME>
ENTITY_KEY: <KEY_FOR_INDEX_MANIFEST>
DOMAIN_TAGS: [<LIST>]
OWNER_TEAM: <SYS|TEAM>
LIFECYCLE: ACTIVE|DRAFT|DEPRECATED

### PURPOSE
<1-2 lines>

### ROUTING_RULES (KEYS ONLY)
- REG_KEYS: [<KEYS_ONLY>]                     # registries for types/minset
- XREF_KEYS: [<KEYS_ONLY>]                    # how to pick roles/entities
- KB_KEYS: [<KEYS_ONLY>]                      # allowed KB scope
- LAW_KEYS: [LAW_01, LAW_02, LAW_03, LAW_04, LAW_05, LAW_06, LAW_14, LAW_19, LAW_20, LAW_21]

### WORK_SET_POLICY
- MAX_ROLES: <number>                          # default 3-5
- MIN_SET_REQUIRED: true
- SELECTION_CRITERIA: <one line>
- NO_GUESS: true

### INPUTS
- TOKENS: [TASK_TEXT, MODE_HINT?]
- REQUIRED: [TASK_TEXT]

### OUTPUTS
- ARTIFACTS: [OUTPUT_PACK, RUN_LOG?, DECISION_LOG?]
- TOKENS: [WORK_SET_KEYS, RUN_SUMMARY]

### STEP_RUN
- STEP: S0
  GOAL: Task sanity + exec mode
  INPUTS: [TASK_TEXT, MODE_HINT?]
  TARGETS: [INDEX_MANIFEST]
  ACTIONS:
    - Ensure TASK_TEXT exists
    - Set EXEC_MODE (DEFAULT if no hint)
  OUTPUTS: [TASK_TOKEN, EXEC_MODE]
  CHECKS: [TASK_PRESENT]
  FAIL: UE.FAIL.INPUT_ABSENT
  NEXT: "го"

- STEP: S1
  GOAL: Build minimal WORK_SET
  INPUTS: [TASK_TOKEN]
  TARGETS: [INDEX_MANIFEST]
  ACTIONS:
    - Validate MIN_SET keys exist
    - Select required roles/entities via REG+XREF+KB_SCOPE (KEYS ONLY)
  OUTPUTS: [WORK_SET_KEYS]
  CHECKS: [REQUIRED_KEYS_OK]
  FAIL: UE.FAIL.MISSING_KEY
  NEXT: "го"

- STEP: S2
  GOAL: Execute domain run
  INPUTS: [WORK_SET_KEYS, TASK_TOKEN, EXEC_MODE]
  TARGETS: [<WORK_SET_KEYS_ONLY>]
  ACTIONS:
    - Resolve keys via INDEX_MANIFEST
    - Open minimal set
    - Produce OUTPUT_PACK artifact
  OUTPUTS: [OUTPUT_PACK, PATCH_NOTES?]
  CHECKS: [QUALITY_GATE]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

- STEP: S3
  GOAL: Trace + log
  INPUTS: [OUTPUT_PACK, DECISIONS]
  TARGETS: [<LOG_KEYS_ONLY>]
  ACTIONS:
    - Write RUN_LOG_ENTRY
    - Write DECISION_LOG_ENTRY (if routing/choice made)
  OUTPUTS: [RUN_LOG?, DECISION_LOG?]
  CHECKS: [LOG_WRITTEN?]
  FAIL: UE.FAIL.LOG_MISSING
  NEXT: "го"

### INTERFACES (KEYS ONLY)
- INPUT_INTERFACES: [<KEYS_ONLY>]
- OUTPUT_INTERFACES: [<KEYS_ONLY>]

### KB_SCOPE
KB_INPUTS:
- Only allowed KB keys via routing policy
KB_OUTPUTS:
- Output pack + logs only
KB_BOUNDARIES:
- No guessing, no RAW

### GATES
PASS_IF:
- WORK_SET minimal + trace present
REWORK_IF:
- Over-noise / too many roles / unclear outputs
FAIL_IF:
- RAW embedded / bypass manifest / missing required keys

### CHANGELOG (append-only)
- DATE: 0000-00-00
  CHANGE_ID: <REPLACE_ME>
  TYPE: CREATE|UPDATE|DEPRECATE
  NOTES: <one line>
