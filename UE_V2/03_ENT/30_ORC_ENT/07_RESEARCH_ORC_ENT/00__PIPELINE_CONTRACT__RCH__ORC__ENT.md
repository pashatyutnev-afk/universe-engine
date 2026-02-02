FILE: UE_V2/03_ENT/30_ORC_ENT/07_RESEARCH_ORC_ENT/00__PIPELINE_CONTRACT__RCH__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 07_RESEARCH_ORC_ENT
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: RCH_ORC_ENT
UID: UE.V2.ENT.PIPE.RCH_ORC_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: Contract has no RAW

---

## [M] PURPOSE
RESEARCH PIPELINE_CONTRACT — раннер исследовательского контура: план запросов -> триаж источников -> синтез -> политика цитирования.
Работает через KEY и резолвит адреса в INDEX_MANIFEST. RAW внутри контракта запрещён.

## [M] HARD_RULES
- RAW запрещён внутри CONTRACT.
- Все ссылки и маршруты: KEY -> INDEX_MANIFEST -> open.
- MODE REPO: никаких правок репозитория.
- STEP-RUN: один шаг = одна пачка действий, затем NEXT_PROMPT.
- Любой шаг завершать NEXT_PROMPT: "го" или FAIL_CODE.
- В пользовательском выводе по умолчанию: без ссылок/источников, если не требуется явно.
- Если задача требует свежести/верификации — запускать поиск (внешний контур), но результаты упаковывать безопасно.

## [M] REQUIRED_KEYS (must exist in INDEX_MANIFEST)
- INDEX_MANIFEST
- PIPELINE_CONTRACT
- RCH.QUERY_PLANNER
- RCH.SOURCE_TRIAGE
- RCH.SUMMARY_SYNTH
- RCH.CITATION_POLICY_BRIDGE

## [M] CONTRACT_HEADER
- REALM_ID: UE_V2/03_ENT/30_ORC_ENT/07_RESEARCH_ORC_ENT
- DOMAIN: RCH_ORC_ENT
- ARTIFACT_TYPES: [QUERY_PLAN, SOURCE_SET, TRIAGE_REPORT, SUMMARY_PACK, CITATION_PACK, OUTPUT_PACK]
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

## [M] STEPS (research flow)
- STEP: S0
  GOAL: Normalize task into RESEARCH_BRIEF
  INPUTS: [TASK_TEXT, RECENCY_HINT?, NO_CITATIONS_DEFAULT?]
  TARGETS: [RCH.QUERY_PLANNER]
  ACTIONS:
    - Extract: question, scope, constraints, needed recency, output format
    - Produce QUERY_PLAN (decompose into 2-5 queries + intent tags)
  OUTPUTS: [RESEARCH_BRIEF, QUERY_PLAN]
  CHECKS: [TASK_PRESENT]
  FAIL: UE.FAIL.INPUT_ABSENT
  NEXT: "го"

- STEP: S1
  GOAL: Source triage and minimal source set
  INPUTS: [QUERY_PLAN]
  TARGETS: [RCH.SOURCE_TRIAGE]
  ACTIONS:
    - Produce SOURCE_SET (selected sources) + TRIAGE_REPORT (why included/excluded)
  OUTPUTS: [SOURCE_SET, TRIAGE_REPORT]
  CHECKS: [SOURCES_PRESENT]
  FAIL: UE.FAIL.NO_SOURCES
  NEXT: "го"

- STEP: S2
  GOAL: Synthesize summary with minimal claims
  INPUTS: [SOURCE_SET, RESEARCH_BRIEF]
  TARGETS: [RCH.SUMMARY_SYNTH]
  ACTIONS:
    - Produce SUMMARY_PACK (structured answer, assumptions labeled)
  OUTPUTS: [SUMMARY_PACK]
  CHECKS: [SUMMARY_OK]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

- STEP: S3
  GOAL: Apply citation policy bridge and package output
  INPUTS: [SUMMARY_PACK, TRIAGE_REPORT]
  TARGETS: [RCH.CITATION_POLICY_BRIDGE]
  ACTIONS:
    - Decide CITATION_MODE: hidden / attach / none (default none in user output)
    - Produce CITATION_PACK (internal) if required by policy
    - Package OUTPUT_PACK
  OUTPUTS: [CITATION_PACK?, OUTPUT_PACK]
  CHECKS: [FINAL_GATE]
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

## [M] FAIL_CODES (local)
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.NO_SOURCES
- UE.FAIL.GATE_FAIL
- UE.FAIL.RULE_VIOLATION

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
