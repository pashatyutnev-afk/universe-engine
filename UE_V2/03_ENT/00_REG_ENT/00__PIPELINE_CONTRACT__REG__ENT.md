FILE: UE_V2/03_ENT/00_REG_ENT/00__PIPELINE_CONTRACT__REG__ENT.md
SCOPE: UE_V2 / 03_ENT / 00_REG_ENT
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: REG
UID: UE.V2.ENT.REG.PIPELINE_CONTRACT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-30
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: Contract has no RAW

---

## [M] PURPOSE
PIPELINE_CONTRACT — навигатор действий для реалма REG_ENT.
Не хранит RAW-адреса. Работает через KEY и резолвит адреса в INDEX_MANIFEST.

## [M] HARD_RULES
- Запрещено хранить RAW внутри CONTRACT (кроме ссылки на INDEX_MANIFEST как KEY).
- Все обращения: TARGET_KEY -> resolve via INDEX_MANIFEST -> open.
- Выполнение по STEP-RUN: один шаг = одна пачка действий.
- Каждый шаг обязан выдавать NEXT_PROMPT: "го" или FAIL_CODE.

## [M] REQUIRED_KEYS (must exist in INDEX_MANIFEST)
- REG.INDEX_MANIFEST
- REG.PIPELINE_CONTRACT
- REG.ENTITY_IDS
- REG.PATH_MAP
- REG.UID_REGISTRY
- REG.ENTITY_CATALOG
- REG.ENTITY_TYPES
- REG.ENTITY_MIN_SET
- REG.ENTITY_REGISTRY
- REG.ARTIFACT_REGISTRY
- REG.CHANGELOG
- REG.DEPRECATION

## [M] CONTRACT_HEADER
- REALM_ID: UE_V2/03_ENT/00_REG_ENT
- DOMAIN: REG
- ARTIFACT_TYPES: [INDEX, PIPE, REG, LOG, OUTPUT_PACK]
- DEFAULT_MODE: FAST

## [M] EXEC_MODEL (how it runs)
1) Resolve INDEX_MANIFEST via KEY: REG.INDEX_MANIFEST
2) Validate REQUIRED_KEYS exist
3) Build WORK_SET (what to open) using KEYS only
4) Run steps sequentially (STEP-RUN)
5) Log decisions and run entries via LOG templates (when present)

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
  TARGETS: [REG.INDEX_MANIFEST]
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
  TARGETS: [REG.INDEX_MANIFEST, REG.PIPELINE_CONTRACT]
  ACTIONS:
    - Resolve required KEYS and confirm they exist in INDEX_MANIFEST
    - Validate REQUIRED_KEYS exist (strict)
    - Build WORK_SET_KEYS (INDEX_MANIFEST + 1-3 target docs by task)
  OUTPUTS: [WORK_SET_KEYS]
  CHECKS: [REQUIRED_KEYS_OK]
  FAIL: UE.FAIL.MISSING_KEY
  NEXT: "го"

- STEP: S2
  GOAL: Domain execution (registry / schema / mapping)
  INPUTS: [WORK_SET_KEYS, TASK_TOKEN]
  TARGETS: [REG.ENTITY_IDS, REG.PATH_MAP, REG.UID_REGISTRY, REG.ENTITY_CATALOG, REG.ENTITY_TYPES, REG.ENTITY_MIN_SET, REG.ENTITY_REGISTRY, REG.ARTIFACT_REGISTRY]
  ACTIONS:
    - Resolve target docs via KEYS only (no RAW in contract)
    - Open only minimal set required by TASK_TOKEN
    - Execute REG-domain logic (IDs, paths, UID policy, types, min-sets)
  OUTPUTS: [ARTIFACTS, PATCH_NOTES?]
  CHECKS: [QUALITY_GATE]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

- STEP: S3
  GOAL: Log and archive tokens
  INPUTS: [ARTIFACTS, DECISIONS]
  TARGETS: [REG.CHANGELOG, REG.DEPRECATION]
  ACTIONS:
    - Write RUN_LOG_ENTRY when LOG layer exists
    - Write DECISION_LOG_ENTRY when route/choice made
    - Record deprecation/redirect notes when applicable
  OUTPUTS: [RUN_LOG?, DECISION_LOG?, DEPRECATION_NOTE?]
  CHECKS: [LOG_WRITTEN?]
  FAIL: UE.FAIL.LOG_MISSING
  NEXT: "го"
