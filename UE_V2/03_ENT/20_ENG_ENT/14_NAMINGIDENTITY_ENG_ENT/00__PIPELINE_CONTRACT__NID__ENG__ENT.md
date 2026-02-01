FILE: UE_V2/03_ENT/20_ENG_ENT/14_NAMINGIDENTITY_ENG_ENT/00__PIPELINE_CONTRACT__NID__ENG__ENT.md
SCOPE: UE_V2 / 03_ENT / 20_ENG_ENT / 14_NAMINGIDENTITY_ENG_ENT
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: NID_ENG
UID: UE.V2.ENT.ENG.NID.PIPELINE_CONTRACT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: Contract has no RAW

---

## [M] PURPOSE
PIPELINE_CONTRACT — навигатор действий для реалма NAMINGIDENTITY_ENG_ENT (NID).
Не хранит RAW-адреса. Работает через KEY и резолвит адреса в INDEX_MANIFEST.

## [M] HARD_RULES
- Запрещено хранить RAW внутри CONTRACT.
- Все обращения: TARGET_KEY -> resolve via INDEX_MANIFEST -> open.
- Выполнение по STEP-RUN: один шаг = одна пачка действий.
- Каждый шаг должен выдавать NEXT_PROMPT: "го" или FAIL_CODE.
- Минимальная загрузка: INDEX_MANIFEST + 1–3 target engine.

## [M] REQUIRED_KEYS (must exist in INDEX_MANIFEST)
- INDEX_MANIFEST
- PIPELINE_CONTRACT
- NID.NAMING_BRIEF
- NID.NAMING_GENERATION
- NID.NAMING_COLLISION
- NID.PLATFORM_FORMAT_TITLES
- NID.SERIES_NAMING

## [M] CONTRACT_HEADER
- REALM_ID: UE_V2/03_ENT/20_ENG_ENT/14_NAMINGIDENTITY_ENG_ENT
- DOMAIN: NID_ENG
- ARTIFACT_TYPES: [INDEX, PIPE, ENTITY, TOKEN_PACK]
- DEFAULT_MODE: FAST

## [M] EXEC_MODEL
1) Resolve INDEX_MANIFEST via KEY: INDEX_MANIFEST
2) Validate REQUIRED_KEYS exist (or downgrade to GAP)
3) Build WORK_SET_KEYS (KEYS only)
4) Run steps sequentially (STEP-RUN)
5) Output NID_OUTPUT_PACK + NEXT "го"

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
  GOAL: Build minimal NID work set
  INPUTS: [TASK_TOKEN]
  TARGETS: [INDEX_MANIFEST, PIPELINE_CONTRACT]
  ACTIONS:
    - Validate REQUIRED_KEYS exist in INDEX_MANIFEST ENTRIES
    - Select WORK_SET_KEYS based on TASK_TOKEN:
      - Always include NID.NAMING_BRIEF
      - Include NID.NAMING_GENERATION if needs candidates
      - Include NID.NAMING_COLLISION if needs filtering
      - Include NID.PLATFORM_FORMAT_TITLES if platform formatting requested
      - Include NID.SERIES_NAMING if series/season naming requested
  OUTPUTS: [WORK_SET_KEYS]
  CHECKS: [REQUIRED_KEYS_OK]
  FAIL: UE.FAIL.MISSING_KEY
  NEXT: "го"

- STEP: S2
  GOAL: Execute NID engines (KEY-only orchestration)
  INPUTS: [WORK_SET_KEYS, TASK_TOKEN]
  TARGETS: [NID.NAMING_BRIEF, NID.NAMING_GENERATION, NID.NAMING_COLLISION, NID.PLATFORM_FORMAT_TITLES, NID.SERIES_NAMING]
  ACTIONS:
    - Resolve and open only keys present in WORK_SET_KEYS
    - Run in canonical order:
      1) NID.NAMING_BRIEF (constraints + target)
      2) NID.NAMING_GENERATION (variants)
      3) NID.NAMING_COLLISION (filter)
      4) NID.PLATFORM_FORMAT_TITLES (normalize)
      5) NID.SERIES_NAMING (if needed)
    - Produce NID_OUTPUT_PACK (summary + final set + checks + next keys)
  OUTPUTS: [NID_OUTPUT_PACK]
  CHECKS: [QUALITY_GATE]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

- STEP: S3
  GOAL: Emit next-open keys for handoff
  INPUTS: [NID_OUTPUT_PACK]
  TARGETS: [INDEX_MANIFEST]
  ACTIONS:
    - Output NEXT_OPEN_KEYS list (KEYS only) for follow-up steps
  OUTPUTS: [NEXT_OPEN_KEYS]
  CHECKS: [OUTPUT_PRESENT]
  FAIL: UE.FAIL.OUTPUT_MISSING
  NEXT: "го"
