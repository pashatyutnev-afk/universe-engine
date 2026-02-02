FILE: UE_V2/03_ENT/30_ORC_ENT/07_RESEARCH_ORC_ENT/02__RCH__SOURCE_TRIAGE__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 07_RESEARCH_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: RCH_ORC_ENT
UID: UE.V2.ENT.ORC.RCH.SOURCE_TRIAGE.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: RCH_SOURCE_TRIAGE
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.RCH.SOURCE_TRIAGE.001

## [M] PURPOSE
Фильтрует и отбирает источники по доверенности, релевантности, свежести и дедупликации.
Формирует SOURCE_SET + TRIAGE_REPORT (внутренний).

## [M] INPUTS / OUTPUTS
- Inputs: [QUERY_PLAN, RAW_SEARCH_RESULTS?]
- Outputs: [SOURCE_SET, TRIAGE_REPORT, FAIL_CODE?]

## [M] TRIAGE_RULES (minimum)
- Prefer primary / official / authoritative sources when possible
- Prefer recent when topic is time-sensitive
- Reject duplicates and low-value sources
- Mark uncertainty explicitly if evidence weak

## [M] KB SCOPE
- KB Inputs: [query plan + search results]
- KB Outputs: [source set token]
- KB Boundaries: [не подменять факт мнением]
- KB RAW refs: []

## [M] GATES
- PASS: источники покрывают вопрос
- FAIL: источников недостаточно или они противоречат без способа разрешить

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Handoff: SOURCE_SET -> SUMMARY_SYNTH

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
