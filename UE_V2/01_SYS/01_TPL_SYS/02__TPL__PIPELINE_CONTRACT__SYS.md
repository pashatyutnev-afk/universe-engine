FILE: 0000-00-00__TPL__PIPELINE_CONTRACT__SYS.md
SCOPE: UE_V2 / SYS
DOC_TYPE: TEMPLATE
TEMPLATE_FOR: PIPELINE_CONTRACT
UID: UE.V2.SYS.TPL.PIPELINE_CONTRACT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-30
UPDATED: 2026-01-30
OWNER: SYS
NAV_RULE: Contract has no RAW

---

## [M] PURPOSE
PIPELINE_CONTRACT — навигатор действий для реалма.
Не хранит RAW-адреса. Работает через KEY и резолвит адреса в INDEX_MANIFEST.

## [M] HARD_RULES
- Запрещено хранить RAW внутри CONTRACT (кроме ссылки на INDEX_MANIFEST как KEY).
- Все обращения: TARGET_KEY -> resolve via INDEX_MANIFEST -> open.
- Выполнение по STEP-RUN: один шаг = одна пачка действий.
- Каждый шаг должен выдавать NEXT_PROMPT: "го" или FAIL_CODE.

## [M] REQUIRED_KEYS (must exist in INDEX_MANIFEST)
- INDEX_MANIFEST
- PIPELINE_CONTRACT
# + доменные ключи ниже (пример)
# - ROUTER
# - REG
# - XREF
# - KB
# - LOG

## [M] CONTRACT_HEADER
- REALM_ID: <REPLACE_ME>
- DOMAIN: <REPLACE_ME>              # например: DOM_AUD
- ARTIFACT_TYPES: [<LIST>]          # например: [INDEX, PIPE, ENTITY, OUTPUT_PACK]
- DEFAULT_MODE: FAST|RELEASE_READY|MASTERPIECE

## [M] EXEC_MODEL (how it runs)
1) Resolve INDEX_MANIFEST via KEY: INDEX_MANIFEST
2) Validate REQUIRED_KEYS exist
3) Build WORK_SET (what to open) using KEYS only
4) Run steps sequentially (STEP-RUN)
5) Log decisions and run entries via LOG templates

## [M] STEP-RUN (canonical)
Each step block format:
- STEP: S<n>
  GOAL: <one line>
  INPUTS: [<tokens>]
  TARGETS: [<KEYS_ONLY>]
  ACTIONS:
    - <imperative action>
  OUTPUTS: [<tokens/artifacts>]
  CHECKS: [<gates>]
  FAIL: <FAIL_CODE_IF_ANY>
  NEXT: "го"

## [M] STEPS (skeleton)

- STEP: S0
  GOAL: Entry sanity and task framing
  INPUTS: [TASK_TEXT, MODE_HINT?]
  TARGETS: [INDEX_MANIFEST]
  ACTIONS:
    - Ensure TASK_TEXT exists, else FAIL
    - Decide EXEC_MODE using MODE_HINT or DEFAULT_MODE
  OUTPUTS: [TASK_TOKEN, EXEC_MODE]
  CHECKS: [TASK_PRESENT]
  FAIL: UE.FAIL.INPUT_ABSENT
  NEXT: "го"

- STEP: S1
  GOAL: Load minimal navigation layer for realm
  INPUTS: [TASK_TOKEN]
  TARGETS: [INDEX_MANIFEST, PIPELINE_CONTRACT]
  ACTIONS:
    - Resolve required KEYS and confirm they exist
    - Build WORK_SET_KEYS (1 realm index + 1-3 target files)
  OUTPUTS: [WORK_SET_KEYS]
  CHECKS: [REQUIRED_KEYS_OK]
  FAIL: UE.FAIL.MISSING_KEY
  NEXT: "го"

- STEP: S2
  GOAL: Domain execution (or handoff)
  INPUTS: [WORK_SET_KEYS, TASK_TOKEN]
  TARGETS: [<DOMAIN_KEYS...>]
  ACTIONS:
    - Resolve target entities/pipes via KEYS
    - Execute domain logic with minimal opens
  OUTPUTS: [ARTIFACTS, PATCH_NOTES?]
  CHECKS: [QUALITY_GATE]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

- STEP: S3
  GOAL: Log and archive tokens
  INPUTS: [ARTIFACTS, DECISIONS]
  TARGETS: [<LOG_KEYS...>]
  ACTIONS:
    - Write RUN_LOG_ENTRY
    - Write DECISION_LOG_ENTRY when route/choice made
    - Archive tokens if required
  OUTPUTS: [RUN_LOG, DECISION_LOG]
  CHECKS: [LOG_WRITTEN]
  FAIL: UE.FAIL.LOG_MISSING
  NEXT: "го"
