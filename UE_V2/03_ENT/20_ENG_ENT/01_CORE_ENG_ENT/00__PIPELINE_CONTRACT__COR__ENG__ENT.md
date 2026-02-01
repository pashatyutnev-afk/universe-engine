FILE: UE_V2/03_ENT/20_ENG_ENT/01_CORE_ENG_ENT/00__PIPELINE_CONTRACT__COR__ENG__ENT.md
SCOPE: UE_V2 / 03_ENT / 20_ENG_ENT / 01_CORE_ENG_ENT
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: COR_ENG
UID: UE.V2.ENT.ENG.COR.PIPELINE_CONTRACT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: Contract has no RAW

---

## [M] PURPOSE
PIPELINE_CONTRACT — навигатор действий для реалма CORE_ENG_ENT (COR).
Не хранит RAW-адреса. Работает через KEY и резолвит адреса в INDEX_MANIFEST.

## [M] HARD_RULES
- No RAW inside CONTRACT.
- Все обращения: TARGET_KEY -> resolve via INDEX_MANIFEST -> open.
- STEP-RUN: один шаг = одна пачка действий.
- Каждый шаг выдаёт NEXT_PROMPT: "го" или FAIL_CODE.
- Минимальная загрузка: INDEX_MANIFEST + 1–3 engine targets.

## [M] REQUIRED_KEYS (must exist in INDEX_MANIFEST)
- INDEX_MANIFEST
- PIPELINE_CONTRACT
# engines may be GAP while building (allowed):
- COR.CORE_IDENTITY
- COR.CORE_STATE
- COR.CORE_LIFECYCLE

## [M] CONTRACT_HEADER
- REALM_ID: UE_V2/03_ENT/20_ENG_ENT/01_CORE_ENG_ENT
- DOMAIN: COR_ENG
- ARTIFACT_TYPES: [INDEX, PIPE, ENTITY, TOKEN_PACK, OUTPUT_PACK]
- DEFAULT_MODE: FAST

## [M] EXEC_MODEL
1) Resolve INDEX_MANIFEST via KEY: INDEX_MANIFEST
2) Validate REQUIRED_KEYS exist (engines may be GAP during build)
3) Build WORK_SET_KEYS (KEYS only)
4) Run steps sequentially (STEP-RUN)
5) Output COR_OUTPUT_PACK + NEXT "го"

## [M] STEP-RUN (canonical)
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
  GOAL: Select COR work set (minimal opens)
  INPUTS: [TASK_TOKEN]
  TARGETS: [INDEX_MANIFEST, PIPELINE_CONTRACT]
  ACTIONS:
    - Resolve INDEX_MANIFEST via KEY: INDEX_MANIFEST
    - Confirm REQUIRED_KEYS exist in ENTRIES
    - Build WORK_SET_KEYS (KEYS only):
      - identity -> [COR.CORE_IDENTITY]
      - state -> [COR.CORE_STATE]
      - lifecycle -> [COR.CORE_LIFECYCLE]
      - full COR run -> [COR.CORE_IDENTITY, COR.CORE_STATE, COR.CORE_LIFECYCLE]
  OUTPUTS: [WORK_SET_KEYS]
  CHECKS: [REQUIRED_KEYS_OK]
  FAIL: UE.FAIL.MISSING_KEY
  NEXT: "го"

- STEP: S2
  GOAL: Execute COR engines (KEY-only orchestration)
  INPUTS: [WORK_SET_KEYS, TASK_TOKEN]
  TARGETS: [COR.CORE_IDENTITY, COR.CORE_STATE, COR.CORE_LIFECYCLE]
  ACTIONS:
    - Resolve and open only keys present in WORK_SET_KEYS
    - Canonical order when multiple:
      1) COR.CORE_IDENTITY
      2) COR.CORE_STATE
      3) COR.CORE_LIFECYCLE
    - Produce COR_OUTPUT_PACK (summary + outputs + checks + next-open keys)
  OUTPUTS: [COR_OUTPUT_PACK]
  CHECKS: [QUALITY_GATE]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

- STEP: S3
  GOAL: Emit NEXT_OPEN_KEYS
  INPUTS: [COR_OUTPUT_PACK]
  TARGETS: [INDEX_MANIFEST]
  ACTIONS:
    - Output NEXT_OPEN_KEYS list (KEYS only) for follow-up steps
  OUTPUTS: [NEXT_OPEN_KEYS]
  CHECKS: [OUTPUT_PRESENT]
  FAIL: UE.FAIL.OUTPUT_MISSING
  NEXT: "го"
