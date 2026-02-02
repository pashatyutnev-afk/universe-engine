FILE: UE_V2/03_ENT/30_ORC_ENT/06_WEB_ORC_ENT/00__PIPELINE_CONTRACT__WEB__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 06_WEB_ORC_ENT
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: WEB_ORC_ENT
UID: UE.V2.ENT.PIPE.WEB_ORC_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: Contract has no RAW

---

## [M] PURPOSE
WEB PIPELINE_CONTRACT — раннер веб-оркестрации: brief -> block factory -> a11y QA -> SEO packaging -> deploy handoff.
Работает через KEY и резолвит адреса в INDEX_MANIFEST. RAW внутри контракта запрещён.

## [M] HARD_RULES
- RAW запрещён внутри CONTRACT.
- Все ссылки и маршруты: KEY -> INDEX_MANIFEST -> open.
- MODE REPO: никаких правок репозитория.
- STEP-RUN: один шаг = одна пачка действий, затем NEXT_PROMPT.
- Любой шаг завершать NEXT_PROMPT: "го" или FAIL_CODE.
- Выход по умолчанию: self-contained HTML/CSS/JS (один файл).
- a11y по умолчанию: семантика, фокус, клавиатурная навигация.
- Цвет описывать как principles (contrast/readability), не как конкретные палитры.

## [M] REQUIRED_KEYS (must exist in INDEX_MANIFEST)
- INDEX_MANIFEST
- PIPELINE_CONTRACT
- WEB.BRIEF_FACTORY
- WEB.BLOCK_FACTORY
- WEB.A11Y_QA
- WEB.SEO_PACKAGER
- WEB.DEPLOY_HANDOFF

## [M] CONTRACT_HEADER
- REALM_ID: UE_V2/03_ENT/30_ORC_ENT/06_WEB_ORC_ENT
- DOMAIN: WEB_ORC_ENT
- ARTIFACT_TYPES: [WEB_BRIEF, BLOCK_SPEC, HTML_BUNDLE, A11Y_REPORT, SEO_PACK, DEPLOY_HANDOFF_TOKEN, OUTPUT_PACK]
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

## [M] STEPS (web flow)
- STEP: S0
  GOAL: Normalize task into WEB_BRIEF and constraints lock
  INPUTS: [TASK_TEXT, MODE_HINT?]
  TARGETS: [WEB.BRIEF_FACTORY]
  ACTIONS:
    - Extract: page/block goal, audience, CTA, content structure, platform constraints
    - Lock constraints into WEB_CONSTRAINTS_LOCK
  OUTPUTS: [WEB_BRIEF, WEB_CONSTRAINTS_LOCK, EXEC_MODE]
  CHECKS: [TASK_PRESENT]
  FAIL: UE.FAIL.INPUT_ABSENT
  NEXT: "го"

- STEP: S1
  GOAL: Build block spec and produce self-contained HTML bundle
  INPUTS: [WEB_BRIEF, WEB_CONSTRAINTS_LOCK]
  TARGETS: [WEB.BLOCK_FACTORY]
  ACTIONS:
    - Produce BLOCK_SPEC (layout, components, states, microinteractions)
    - Produce HTML_BUNDLE (single file: HTML+CSS+JS)
  OUTPUTS: [BLOCK_SPEC, HTML_BUNDLE]
  CHECKS: [BUNDLE_PRESENT]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

- STEP: S2
  GOAL: a11y QA and SEO packaging
  INPUTS: [HTML_BUNDLE, WEB_BRIEF]
  TARGETS: [WEB.A11Y_QA, WEB.SEO_PACKAGER]
  ACTIONS:
    - Run a11y checks: semantics, focus order, keyboard nav, aria
    - Produce SEO_PACK (meta copy, json-ld suggestion, headings map)
  OUTPUTS: [A11Y_REPORT, SEO_PACK]
  CHECKS: [A11Y_PASS_MIN, SEO_OK]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

- STEP: S3
  GOAL: Deploy handoff
  INPUTS: [HTML_BUNDLE, SEO_PACK, A11Y_REPORT]
  TARGETS: [WEB.DEPLOY_HANDOFF]
  ACTIONS:
    - Produce DEPLOY_HANDOFF_TOKEN (paste instructions, assets, test checklist)
    - Package OUTPUT_PACK
  OUTPUTS: [DEPLOY_HANDOFF_TOKEN, OUTPUT_PACK]
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
