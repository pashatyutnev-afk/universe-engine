FILE: UE_V2/03_ENT/30_ORC_ENT/08_META_ORC_ENT/00__PIPELINE_CONTRACT__MET__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 08_META_ORC_ENT
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: MET_ORC_ENT
UID: UE.V2.ENT.PIPE.MET_ORC_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: Contract has no RAW

---

## [M] PURPOSE
META PIPELINE_CONTRACT — раннер мета-контроля: self-check -> template apply -> UID normalization -> deprecation policy.
Используется как “санитарный слой” поверх любых доменных прогонов.
RAW внутри контракта запрещён.

## [M] HARD_RULES
- RAW запрещён внутри CONTRACT.
- Все ссылки и маршруты: KEY -> INDEX_MANIFEST -> open.
- MODE REPO: никаких правок репозитория.
- STEP-RUN: один шаг = одна пачка действий, затем NEXT_PROMPT.
- Любой шаг завершать NEXT_PROMPT: "го" или FAIL_CODE.
- Нормализация UID/CHANGE_ID допускается только как “output token / рекомендация”, не как запись в репо.

## [M] REQUIRED_KEYS (must exist in INDEX_MANIFEST)
- INDEX_MANIFEST
- PIPELINE_CONTRACT
- MET.SELF_CHECK
- MET.TEMPLATE_APPLIER
- MET.NORMALIZATION_UID
- MET.DEPRECATION_POLICY

## [M] CONTRACT_HEADER
- REALM_ID: UE_V2/03_ENT/30_ORC_ENT/08_META_ORC_ENT
- DOMAIN: MET_ORC_ENT
- ARTIFACT_TYPES: [SELF_CHECK_REPORT, TEMPLATE_APPLY_NOTES, UID_NORMALIZATION_TOKEN, DEPRECATION_TOKEN, OUTPUT_PACK]
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

## [M] STEPS (meta flow)
- STEP: S0
  GOAL: Run self-check on task/output draft
  INPUTS: [TASK_TEXT, DRAFT_OUTPUT?]
  TARGETS: [MET.SELF_CHECK]
  ACTIONS:
    - Produce SELF_CHECK_REPORT: missing inputs, contradictions, policy violations
  OUTPUTS: [SELF_CHECK_REPORT]
  CHECKS: [REPORT_PRESENT]
  FAIL: UE.FAIL.INPUT_ABSENT
  NEXT: "го"

- STEP: S1
  GOAL: Apply templates and structural canon
  INPUTS: [DRAFT_OUTPUT?, SELF_CHECK_REPORT]
  TARGETS: [MET.TEMPLATE_APPLIER]
  ACTIONS:
    - Produce TEMPLATE_APPLY_NOTES: required sections/order, formatting fixes
  OUTPUTS: [TEMPLATE_APPLY_NOTES]
  CHECKS: [TEMPLATE_OK]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

- STEP: S2
  GOAL: UID / CHANGE_ID normalization (token-only)
  INPUTS: [DRAFT_OUTPUT?, TEMPLATE_APPLY_NOTES]
  TARGETS: [MET.NORMALIZATION_UID]
  ACTIONS:
    - Produce UID_NORMALIZATION_TOKEN: suggested UID/CHANGE_ID normalization per UID_RULES hook
  OUTPUTS: [UID_NORMALIZATION_TOKEN]
  CHECKS: [UID_TOKEN_OK]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

- STEP: S3
  GOAL: Deprecation policy checks and packaging
  INPUTS: [TASK_TEXT, DRAFT_OUTPUT?, UID_NORMALIZATION_TOKEN]
  TARGETS: [MET.DEPRECATION_POLICY]
  ACTIONS:
    - Produce DEPRECATION_TOKEN: deprecation rules, migration notes, gates
    - Package OUTPUT_PACK
  OUTPUTS: [DEPRECATION_TOKEN, OUTPUT_PACK]
  CHECKS: [FINAL_GATE]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

## [M] FAIL_CODES (local)
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.GATE_FAIL
- UE.FAIL.RULE_VIOLATION

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
