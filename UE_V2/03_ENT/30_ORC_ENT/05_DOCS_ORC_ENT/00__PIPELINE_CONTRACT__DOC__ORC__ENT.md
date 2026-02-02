FILE: UE_V2/03_ENT/30_ORC_ENT/05_DOCS_ORC_ENT/00__PIPELINE_CONTRACT__DOC__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 05_DOCS_ORC_ENT
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: DOC_ORC_ENT
UID: UE.V2.ENT.PIPE.DOC_ORC_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: Contract has no RAW

---

## [M] PURPOSE
DOCS PIPELINE_CONTRACT — раннер документации: brief -> build -> KB scope -> lint/QA -> release packaging.
Работает через KEY и резолвит адреса в INDEX_MANIFEST. RAW внутри контракта запрещён.

## [M] HARD_RULES
- RAW запрещён внутри CONTRACT.
- Все ссылки и маршруты: KEY -> INDEX_MANIFEST -> open.
- MODE REPO: никаких правок репозитория.
- STEP-RUN: один шаг = одна пачка действий, затем NEXT_PROMPT.
- Любой шаг завершать NEXT_PROMPT: "го" или FAIL_CODE.
- INTERFACES: только RAW-ссылки (не PATH).
- KB SCOPE обязателен: inputs/outputs/boundaries + RAW refs.
- SPC PEER ROLES не смешивать с ENG-секциями (отдельный блок).

## [M] REQUIRED_KEYS (must exist in INDEX_MANIFEST)
- INDEX_MANIFEST
- PIPELINE_CONTRACT
- DOC.BRIEF_FACTORY
- DOC.BUILDER
- DOC.KB_SCOPE_BUILDER
- DOC.LINT_QA
- DOC.RELEASE_PACKAGER

## [M] CONTRACT_HEADER
- REALM_ID: UE_V2/03_ENT/30_ORC_ENT/05_DOCS_ORC_ENT
- DOMAIN: DOC_ORC_ENT
- ARTIFACT_TYPES: [DOC_BRIEF, DOC_DRAFT, DOC_FINAL, KB_SCOPE_TOKEN, QA_REPORT, OUTPUT_PACK]
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

## [M] STEPS (docs flow)
- STEP: S0
  GOAL: Normalize task into DOC_BRIEF and constraints lock
  INPUTS: [TASK_TEXT, MODE_HINT?]
  TARGETS: [DOC.BRIEF_FACTORY]
  ACTIONS:
    - Extract purpose, audience, scope, required sections, output format
    - Lock constraints into DOC_CONSTRAINTS_LOCK
  OUTPUTS: [DOC_BRIEF, DOC_CONSTRAINTS_LOCK, EXEC_MODE]
  CHECKS: [TASK_PRESENT]
  FAIL: UE.FAIL.INPUT_ABSENT
  NEXT: "го"

- STEP: S1
  GOAL: Build document draft
  INPUTS: [DOC_BRIEF, DOC_CONSTRAINTS_LOCK]
  TARGETS: [DOC.BUILDER]
  ACTIONS:
    - Produce DOC_DRAFT using canon headers/sections and stable structure
  OUTPUTS: [DOC_DRAFT]
  CHECKS: [DRAFT_PRESENT]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

- STEP: S2
  GOAL: Build KB scope token for the document
  INPUTS: [DOC_DRAFT, DOC_BRIEF]
  TARGETS: [DOC.KB_SCOPE_BUILDER]
  ACTIONS:
    - Produce KB_SCOPE_TOKEN: inputs/outputs/boundaries + RAW refs (no PATH)
  OUTPUTS: [KB_SCOPE_TOKEN]
  CHECKS: [KB_SCOPE_OK]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

- STEP: S3
  GOAL: Lint + QA and package release output
  INPUTS: [DOC_DRAFT, KB_SCOPE_TOKEN]
  TARGETS: [DOC.LINT_QA, DOC.RELEASE_PACKAGER]
  ACTIONS:
    - Run lint checks: headers, required sections, RAW-only interfaces, no mixed roles
    - Produce DOC_FINAL and QA_REPORT
    - Package OUTPUT_PACK
  OUTPUTS: [DOC_FINAL, QA_REPORT, OUTPUT_PACK]
  CHECKS: [FINAL_GATE]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

## [M] FAIL_CODES (local)
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.MISSING_KEY
- UE.FAIL.RULE_VIOLATION
- UE.FAIL.GATE_FAIL
- UE.FAIL.LOG_MISSING

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
