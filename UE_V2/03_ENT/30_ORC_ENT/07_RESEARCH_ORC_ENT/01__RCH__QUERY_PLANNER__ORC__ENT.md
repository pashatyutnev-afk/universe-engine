FILE: UE_V2/03_ENT/30_ORC_ENT/07_RESEARCH_ORC_ENT/01__RCH__QUERY_PLANNER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 07_RESEARCH_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: RCH_ORC_ENT
UID: UE.V2.ENT.ORC.RCH.QUERY_PLANNER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: RCH_QUERY_PLANNER
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.RCH.QUERY_PLANNER.001

## [M] PURPOSE
Планирует исследование: разбивает задачу на запросы, задаёт intents, определяет требуемую свежесть и границы.
Делает QUERY_PLAN, а не “сам поиск”.

## [M] INPUTS / OUTPUTS
- Inputs: [TASK_TEXT, RECENCY_HINT?, OUTPUT_PREFS?]
- Outputs: [RESEARCH_BRIEF, QUERY_PLAN, FAIL_CODE?]

## [M] QUERY_PLAN (schema)
- MAIN_QUESTION
- SUBQUESTIONS
- QUERIES: [{q, intent, freshness_hint}]
- EXCLUSIONS
- REQUIRED_EVIDENCE (if any)
- OUTPUT_FORMAT

## [M] KB SCOPE
- KB Inputs: [task + user constraints]
- KB Outputs: [query plan]
- KB Boundaries: [не расширять тему без входа]
- KB RAW refs: []

## [M] GATES
- PASS: план покрывает вопрос и не уходит в стороны
- FAIL: вопрос неоднозначен и без уточнения нельзя построить план

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA, CTL]
- Handoff: QUERY_PLAN -> SOURCE_TRIAGE

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
