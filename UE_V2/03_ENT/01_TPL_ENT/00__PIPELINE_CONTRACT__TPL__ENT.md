FILE: UE_V2/03_ENT/01_TPL_ENT/00__PIPELINE_CONTRACT__TPL__ENT.md
SCOPE: UE_V2 / 03_ENT / 01_TPL_ENT
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: TPL
UID: UE.V2.ENT.TPL.PIPELINE_CONTRACT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: Contract has no RAW

---

## [M] PURPOSE
PIPELINE_CONTRACT — навигатор действий для реалма TPL_ENT.
Не хранит RAW-адреса. Работает через KEY и резолвит адреса в INDEX_MANIFEST.

## [M] HARD_RULES
- Запрещено хранить RAW внутри CONTRACT (без исключений).
- Все обращения: TARGET_KEY -> resolve via INDEX_MANIFEST -> open.
- Выполнение по STEP-RUN: один шаг = одна пачка действий.
- Каждый шаг обязан выдавать NEXT_PROMPT: "го" или FAIL_CODE.

## [M] REQUIRED_KEYS (must exist in INDEX_MANIFEST)
- INDEX_MANIFEST
- PIPELINE_CONTRACT
- TPL.ENGINE
- TPL.ORCHESTRATOR
- TPL.SPECIALIST
- TPL.CONTROLLER
- TPL.VALIDATOR
- TPL.QA
- TPL.XREF

## [M] CONTRACT_HEADER
- REALM_ID: UE_V2/03_ENT/01_TPL_ENT
- DOMAIN: TPL
- ARTIFACT_TYPES: [INDEX, PIPE, TPL, OUTPUT_PACK, LOG]
- DEFAULT_MODE: FAST

## [M] EXEC_MODEL (how it runs)
1) Resolve INDEX_MANIFEST via KEY: INDEX_MANIFEST
2) Validate REQUIRED_KEYS exist in INDEX_MANIFEST
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
    - Resolve INDEX_MANIFEST and confirm it opens
    - Validate REQUIRED_KEYS exist in INDEX_MANIFEST ENTRIES
    - Build WORK_SET_KEYS (INDEX_MANIFEST + 1-3 relevant templates by task)
  OUTPUTS: [WORK_SET_KEYS]
  CHECKS: [REQUIRED_KEYS_OK]
  FAIL: UE.FAIL.MISSING_KEY
  NEXT: "го"

- STEP: S2
  GOAL: Domain execution (templates selection / handoff)
  INPUTS: [WORK_SET_KEYS, TASK_TOKEN]
  TARGETS: [TPL.ENGINE, TPL.ORCHESTRATOR, TPL.SPECIALIST, TPL.CONTROLLER, TPL.VALIDATOR, TPL.QA, TPL.XREF]
  ACTIONS:
    - Resolve target templates via KEYS only (no RAW in contract)
    - Open only minimal set required by TASK_TOKEN
    - Produce requested artifact pack or patch notes
  OUTPUTS: [ARTIFACTS, PATCH_NOTES?]
  CHECKS: [QUALITY_GATE]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

- STEP: S3
  GOAL: Log and archive tokens
  INPUTS: [ARTIFACTS, DECISIONS]
  TARGETS: [INDEX_MANIFEST]
  ACTIONS:
    - Write RUN_LOG_ENTRY if LOG layer is present in realm
    - Write DECISION_LOG_ENTRY when route/choice made
    - Archive tokens if required by system policy
  OUTPUTS: [RUN_LOG?, DECISION_LOG?]
  CHECKS: [LOG_WRITTEN?]
  FAIL: UE.FAIL.LOG_MISSING
  NEXT: "го"
