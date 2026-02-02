FILE: UE_V2/03_ENT/30_ORC_ENT/04_VIDEO_ORC_ENT/00__PIPELINE_CONTRACT__VID__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 04_VIDEO_ORC_ENT
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: VID_ORC_ENT
UID: UE.V2.ENT.PIPE.VID_ORC_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: Contract has no RAW

---

## [M] PURPOSE
VIDEO PIPELINE_CONTRACT — раннер видео-оркестрации: brief -> shot plan -> prompt factory -> style packaging -> QA -> export handoff.
Работает через KEY и резолвит адреса в INDEX_MANIFEST. RAW внутри контракта запрещён.

## [M] HARD_RULES
- RAW запрещён внутри CONTRACT.
- Все ссылки и маршруты: KEY -> INDEX_MANIFEST -> open.
- MODE REPO: никаких правок репозитория.
- STEP-RUN: один шаг = одна пачка действий, затем NEXT_PROMPT.
- Любой шаг завершать NEXT_PROMPT: "го" или FAIL_CODE.
- Стиль/цвет как principles, без конкретных палитр.
- VISUAL: не принимать монтажных решений, только ограничения/риски и управляемые параметры.

## [M] REQUIRED_KEYS (must exist in INDEX_MANIFEST)
- INDEX_MANIFEST
- PIPELINE_CONTRACT
- VID.BRIEF_FACTORY
- VID.SHOT_PLANNER
- VID.PROMPT_FACTORY
- VID.STYLE_PACKAGER
- VID.QA_CHECKS
- VID.EXPORT_HANDOFF

## [M] CONTRACT_HEADER
- REALM_ID: UE_V2/03_ENT/30_ORC_ENT/04_VIDEO_ORC_ENT
- DOMAIN: VID_ORC_ENT
- ARTIFACT_TYPES: [VID_BRIEF, SHOT_PLAN, PROMPT_PACK, STYLE_PACK, QA_REPORT, EXPORT_HANDOFF_TOKEN, OUTPUT_PACK]
- DEFAULT_MODE: RELEASE_READY

## [M] STEP-RUN (canonical)
- STEP: S
  GOAL:
  INPUTS: []
  TARGETS: []
  ACTIONS:
    -
  OUTPUTS: []
  CHECKS: []
  FAIL:
  NEXT: "го"

## [M] STEPS (video flow)
- STEP: S0
  GOAL: Normalize task into VID_BRIEF and constraints lock
  INPUTS: [TASK_TEXT, MODE_HINT?]
  TARGETS: []
  ACTIONS:
    - Extract: subject, scene, duration, fps, resolution, camera constraints, style-switch count if any
    - Lock constraints into VID_CONSTRAINTS_LOCK
  OUTPUTS: [VID_BRIEF, VID_CONSTRAINTS_LOCK, EXEC_MODE]
  CHECKS: [TASK_PRESENT]
  FAIL: UE.FAIL.INPUT_ABSENT
  NEXT: "го"

- STEP: S1
  GOAL: Build shot plan (beats + timing)
  INPUTS: [VID_BRIEF, VID_CONSTRAINTS_LOCK]
  TARGETS: [VID.SHOT_PLANNER]
  ACTIONS:
    - Create SHOT_PLAN (beats, camera, transitions, style-change timings)
  OUTPUTS: [SHOT_PLAN]
  CHECKS: [SHOT_PLAN_OK]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

- STEP: S2
  GOAL: Build prompt pack and style pack
  INPUTS: [VID_BRIEF, SHOT_PLAN, VID_CONSTRAINTS_LOCK]
  TARGETS: [VID.PROMPT_FACTORY, VID.STYLE_PACKAGER]
  ACTIONS:
    - Produce PROMPT_PACK (tool-ready prompts + negatives + parameters)
    - Produce STYLE_PACK (principles + variation slots)
  OUTPUTS: [PROMPT_PACK, STYLE_PACK]
  CHECKS: [PROMPTS_OK]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

- STEP: S3
  GOAL: QA + export handoff packaging
  INPUTS: [PROMPT_PACK, STYLE_PACK, SHOT_PLAN, VID_BRIEF]
  TARGETS: [VID.QA_CHECKS, VID.EXPORT_HANDOFF]
  ACTIONS:
    - Run QA checks (continuity, subject lock, style timing, spec completeness)
    - Build EXPORT_HANDOFF_TOKEN (naming, output settings, checklist)
    - Package OUTPUT_PACK
  OUTPUTS: [QA_REPORT, EXPORT_HANDOFF_TOKEN, OUTPUT_PACK]
  CHECKS: [FINAL_GATE]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

## [M] FAIL_CODES (local)
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.MISSING_KEY
- UE.FAIL.RULE_VIOLATION
- UE.FAIL.GATE_FAIL

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
