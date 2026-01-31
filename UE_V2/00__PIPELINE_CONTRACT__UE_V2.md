FILE: UE_V2/00__PIPELINE_CONTRACT__UE_V2.md
SCOPE: UE_V2
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: UE_V2
UID: UE.V2.ROOT.PIPELINE_CONTRACT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: Contract has no RAW

---

## [M] PURPOSE
PIPELINE_CONTRACT — корневой навигатор выполнения UE_V2.
Не хранит RAW-адреса. Работает через KEY и резолвит адреса в корневом INDEX_MANIFEST.
Роутит в слой через его INDEX_MANIFEST и дальше передаёт управление слою (его PIPELINE_CONTRACT).

## [M] HARD_RULES
- Запрещено хранить RAW внутри CONTRACT (без исключений).
- Все обращения: TARGET_KEY -> resolve via root INDEX_MANIFEST -> open.
- Выполнение по STEP-RUN: один шаг = одна пачка действий.
- Никаких догадок: LAYER_HINT обязателен.
- PIPELINE_CONTRACT слоя обязан резолвиться внутри layer INDEX_MANIFEST (дубликатов в root индексе нет).

## [M] REQUIRED_KEYS (must exist in root INDEX_MANIFEST)
- INDEX_MANIFEST
- PIPELINE_CONTRACT
- UEV2.BOOT.INDEX_MANIFEST
- UEV2.SYS.INDEX_MANIFEST
- UEV2.STD.INDEX_MANIFEST
- UEV2.ENT.INDEX_MANIFEST

## [M] LAYER_SELECTOR (no guessing)
# RULE: LAYER_HINT must be one of these tokens.
- BOOT: UEV2.BOOT.INDEX_MANIFEST
- SYS: UEV2.SYS.INDEX_MANIFEST
- STD: UEV2.STD.INDEX_MANIFEST
- ENT: UEV2.ENT.INDEX_MANIFEST

## [M] FAIL_CODES
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.MISSING_KEY
- UE.FAIL.INVALID_LAYER_HINT
- UE.FAIL.LAYER_PIPELINE_MISSING

## [M] CONTRACT_HEADER
- REALM_ID: UE_V2
- DOMAIN: UE_V2
- ARTIFACT_TYPES: [INDEX, PIPE, OUTPUT_PACK, LOG]
- DEFAULT_MODE: FAST

## [M] EXEC_MODEL (how it runs)
1) Resolve root INDEX_MANIFEST via KEY: INDEX_MANIFEST
2) Validate REQUIRED_KEYS exist
3) Resolve LAYER_INDEX_KEY via LAYER_SELECTOR(LAYER_HINT)
4) Open LAYER INDEX_MANIFEST (resolved from root index)
5) Inside layer index, resolve KEY: PIPELINE_CONTRACT and open it
6) Handoff: continue execution in layer pipeline

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

## [M] STEPS

- STEP: S0
  GOAL: Entry sanity and deterministic layer selection
  INPUTS: [TASK_TEXT, LAYER_HINT, MODE_HINT?]
  TARGETS: [INDEX_MANIFEST]
  ACTIONS:
    - Ensure TASK_TEXT exists, else FAIL
    - Ensure LAYER_HINT exists, else FAIL
    - Validate LAYER_HINT is one of LAYER_SELECTOR tokens, else FAIL
    - Decide EXEC_MODE using MODE_HINT or DEFAULT_MODE
  OUTPUTS: [TASK_TOKEN, EXEC_MODE, LAYER_HINT]
  CHECKS: [TASK_PRESENT, LAYER_HINT_VALID]
  FAIL: UE.FAIL.INVALID_LAYER_HINT
  NEXT: "го"

- STEP: S1
  GOAL: Load root navigation layer and validate readiness
  INPUTS: [TASK_TOKEN]
  TARGETS: [INDEX_MANIFEST, PIPELINE_CONTRACT]
  ACTIONS:
    - Resolve INDEX_MANIFEST via KEY: INDEX_MANIFEST
    - Validate ALL REQUIRED_KEYS exist in root INDEX_MANIFEST ENTRIES
  OUTPUTS: [ROOT_READY]
  CHECKS: [REQUIRED_KEYS_OK]
  FAIL: UE.FAIL.MISSING_KEY
  NEXT: "го"

- STEP: S2
  GOAL: Enter layer via layer index and open layer pipeline
  INPUTS: [TASK_TOKEN, LAYER_HINT]
  TARGETS: [INDEX_MANIFEST]
  ACTIONS:
    - Map LAYER_HINT -> LAYER_INDEX_KEY via LAYER_SELECTOR
    - Resolve and open LAYER INDEX_MANIFEST using LAYER_INDEX_KEY
    - Inside LAYER INDEX_MANIFEST, resolve KEY: PIPELINE_CONTRACT
    - Open LAYER PIPELINE_CONTRACT
  OUTPUTS: [LAYER_INDEX_KEY, LAYER_PIPELINE_KEY]
  CHECKS: [LAYER_INDEX_OK, LAYER_PIPELINE_OK]
  FAIL: UE.FAIL.LAYER_PIPELINE_MISSING
  NEXT: "го"

- STEP: S3
  GOAL: Handoff summary (KEYS only) and continue
  INPUTS: [LAYER_INDEX_KEY, LAYER_PIPELINE_KEY]
  TARGETS: [INDEX_MANIFEST]
  ACTIONS:
    - Return route summary (which layer, which keys opened)
    - Continue in layer pipeline
  OUTPUTS: [ROUTE_SUMMARY]
  CHECKS: [TRACE_PRESENT]
  FAIL: UE.FAIL.MISSING_KEY
  NEXT: "го"
