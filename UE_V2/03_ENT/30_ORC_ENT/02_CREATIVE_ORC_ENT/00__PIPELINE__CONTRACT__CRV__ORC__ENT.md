FILE: UE_V2/03_ENT/30_ORC_ENT/02_CREATIVE_ORC_ENT/00__PIPELINE_CONTRACT__CRV__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 02_CREATIVE_ORC_ENT
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: CRV_ORC_ENT
UID: UE.V2.ENT.PIPE.CRV_ORC_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: Contract has no RAW

---

## [M] PURPOSE
CREATIVE PIPELINE_CONTRACT — раннер творческой оркестрации.
Конвертирует “идею” в управляемый набор токенов: identity -> style system -> trend synthesis -> concept-to-artifact.
RAW не хранит: всё через KEY -> INDEX_MANIFEST -> open.

## [M] HARD_RULES
- RAW запрещён внутри CONTRACT.
- Роутинг только через KEYS и INDEX_MANIFEST.
- STEP-RUN: один шаг = одна пачка действий, затем NEXT_PROMPT.
- Минимальные открытия: только то, что нужно для текущего шага.
- MODE REPO: никаких правок репозитория.
- Любой выход: NEXT_PROMPT: "го" или FAIL_CODE.

## [M] REQUIRED_KEYS (must exist in INDEX_MANIFEST of this realm)
- INDEX_MANIFEST
- PIPELINE_CONTRACT
- CRV.IDENTITY_FACTORY
- CRV.STYLE_SYSTEM_BUILDER
- CRV.TREND_SYNTHESIZER
- CRV.CONCEPT_TO_ARTIFACT_BRIDGE

## [M] CONTRACT_HEADER
- REALM_ID: UE_V2/03_ENT/30_ORC_ENT/02_CREATIVE_ORC_ENT
- DOMAIN: CRV_ORC_ENT
- ARTIFACT_TYPES: [CREATIVE_BRIEF, IDENTITY_TOKEN, STYLE_TOKEN, TREND_TOKEN, ARTIFACT_SPEC, OUTPUT_PACK]
- DEFAULT_MODE: RELEASE_READY

## [M] EXEC_MODEL
1) Resolve INDEX_MANIFEST via KEY: INDEX_MANIFEST
2) Validate REQUIRED_KEYS exist
3) Run steps S0..S3
4) Emit OUTPUT_PACK-style result tokens (no repo writes)

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

## [M] STEPS (creative)
- STEP: S0
  GOAL: Normalize creative task into CREATIVE_BRIEF
  INPUTS: [TASK_TEXT, MODE_HINT?]
  TARGETS: []
  ACTIONS:
    - Extract: target artifact type (music/video/web/docs/brand), audience, vibe, constraints
    - Lock constraints into CREATIVE_CONSTRAINTS_LOCK
  OUTPUTS: [CREATIVE_BRIEF, CREATIVE_CONSTRAINTS_LOCK, EXEC_MODE]
  CHECKS: [TASK_PRESENT]
  FAIL: UE.FAIL.INPUT_ABSENT
  NEXT: "го"

- STEP: S1
  GOAL: Build identity token
  INPUTS: [CREATIVE_BRIEF, CREATIVE_CONSTRAINTS_LOCK]
  TARGETS: [CRV.IDENTITY_FACTORY]
  ACTIONS:
    - Build IDENTITY_TOKEN (name/tone/voice rules/brand tags)
    - Ensure “no forbidden words/markers” (project policy)
  OUTPUTS: [IDENTITY_TOKEN]
  CHECKS: [IDENTITY_OK]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

- STEP: S2
  GOAL: Build style system + trend synthesis
  INPUTS: [IDENTITY_TOKEN, CREATIVE_BRIEF]
  TARGETS: [CRV.STYLE_SYSTEM_BUILDER, CRV.TREND_SYNTHESIZER]
  ACTIONS:
    - Build STYLE_TOKEN (principles, constraints, do/don’t, variation slots)
    - Build TREND_TOKEN (patterns, references-as-principles, freshness notes)
  OUTPUTS: [STYLE_TOKEN, TREND_TOKEN]
  CHECKS: [STYLE_OK, TREND_OK]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

- STEP: S3
  GOAL: Convert concept to artifact spec and package outputs
  INPUTS: [CREATIVE_BRIEF, IDENTITY_TOKEN, STYLE_TOKEN, TREND_TOKEN]
  TARGETS: [CRV.CONCEPT_TO_ARTIFACT_BRIDGE]
  ACTIONS:
    - Build ARTIFACT_SPEC (structured instructions for target tool/domain)
    - Package OUTPUT_PACK_TOKEN (brief + spec + gates + next)
  OUTPUTS: [ARTIFACT_SPEC, OUTPUT_PACK_TOKEN]
  CHECKS: [SPEC_COMPLETE]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

## [M] FAIL_CODES (local)
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.MISSING_KEY
- UE.FAIL.RULE_VIOLATION
- UE.FAIL.GATE_FAIL

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
