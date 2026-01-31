FILE: UE_V2/01_SYS/01_TPL_SYS/00__PIPELINE_CONTRACT__TPL__SYS.md
SCOPE: UE_V2 / 01_SYS / 01_TPL_SYS
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: TPL_SYS
UID: UE.V2.SYS.PIPE.TPL_SYS.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: Contract has no RAW

---

## [M] PURPOSE
PIPELINE_CONTRACT — навигатор действий для реалма 01_TPL_SYS.
Не хранит RAW-адреса. Работает через KEY и резолвит адреса в INDEX_MANIFEST.

## [M] HARD_RULES
- Запрещено хранить RAW внутри CONTRACT (кроме ссылки на INDEX_MANIFEST как KEY).
- Все обращения: TARGET_KEY -> resolve via INDEX_MANIFEST -> open.
- Выполнение по STEP-RUN: один шаг = одна пачка действий.
- Каждый шаг должен выдавать NEXT_PROMPT: "го" или FAIL_CODE.

## [M] REQUIRED_KEYS (must exist in INDEX_MANIFEST)
- INDEX_MANIFEST
- PIPELINE_CONTRACT
- TPL.INDEX_MANIFEST
- TPL.PIPELINE_CONTRACT
- TPL.ENTITY_PASSPORT
- TPL.DECISION_LOG_ENTRY
- TPL.FILE_HEADER
- TPL.OUTPUT_PACK
- TPL.RUN_LOG_ENTRY

## [M] CONTRACT_HEADER
- REALM_ID: UE_V2/01_SYS/01_TPL_SYS
- DOMAIN: TPL_SYS
- ARTIFACT_TYPES: [INDEX, PIPE, TPL, OUTPUT_PACK, LOG]
- DEFAULT_MODE: FAST

## [M] EXEC_MODEL (how it runs)
1) Resolve INDEX_MANIFEST via KEY: INDEX_MANIFEST
2) Validate REQUIRED_KEYS exist
3) Build WORK_SET (what to open) using KEYS only
4) Run steps sequentially (STEP-RUN)

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
    - Resolve INDEX_MANIFEST via KEY: INDEX_MANIFEST
    - Validate REQUIRED_KEYS exist in INDEX_MANIFEST ENTRIES
    - Build WORK_SET_KEYS (INDEX_MANIFEST + 1-3 target templates)
  OUTPUTS: [WORK_SET_KEYS]
  CHECKS: [REQUIRED_KEYS_OK]
  FAIL: UE.FAIL.MISSING_KEY
  NEXT: "го"

- STEP: S2
  GOAL: Template execution (selection / packaging)
  INPUTS: [WORK_SET_KEYS, TASK_TOKEN]
  TARGETS: [TPL.INDEX_MANIFEST, TPL.PIPELINE_CONTRACT, TPL.ENTITY_PASSPORT, TPL.DECISION_LOG_ENTRY, TPL.FILE_HEADER, TPL.OUTPUT_PACK, TPL.RUN_LOG_ENTRY]
  ACTIONS:
    - Resolve target templates via KEYS only
    - Open only minimal set required by TASK_TOKEN
    - Produce requested OUTPUT_PACK or PATCH_NOTES
  OUTPUTS: [ARTIFACTS, PATCH_NOTES?]
  CHECKS: [QUALITY_GATE]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

- STEP: S3
  GOAL: Log and archive tokens
  INPUTS: [ARTIFACTS, DECISIONS]
  TARGETS: [TPL.RUN_LOG_ENTRY, TPL.DECISION_LOG_ENTRY]
  ACTIONS:
    - If LOG layer is enabled, write RUN_LOG_ENTRY
    - If routing/choice made, write DECISION_LOG_ENTRY
    - Archive tokens if required by system policy
  OUTPUTS: [RUN_LOG?, DECISION_LOG?]
  CHECKS: [LOG_WRITTEN?]
  FAIL: UE.FAIL.LOG_MISSING
  NEXT: "го"
