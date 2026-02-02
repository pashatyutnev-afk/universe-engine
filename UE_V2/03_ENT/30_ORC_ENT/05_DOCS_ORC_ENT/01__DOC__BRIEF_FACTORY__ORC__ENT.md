FILE: UE_V2/03_ENT/30_ORC_ENT/05_DOCS_ORC_ENT/01__DOC__BRIEF_FACTORY__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 05_DOCS_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: DOC_ORC_ENT
UID: UE.V2.ENT.ORC.DOC.BRIEF_FACTORY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: DOC_BRIEF_FACTORY
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.DOC.BRIEF_FACTORY.001

## [M] PURPOSE
Строит DOC_BRIEF: цель, аудитория, scope, формат, обязательные секции, ограничения и критерии качества.

## [M] INPUTS / OUTPUTS
- Inputs: [TASK_TEXT, TEMPLATE_HINT?, REQUIRED_SECTIONS?]
- Outputs: [DOC_BRIEF, DOC_CONSTRAINTS_LOCK, FAIL_CODE?]

## [M] DOC_BRIEF (minimum fields)
- PURPOSE
- AUDIENCE
- SCOPE_IN
- SCOPE_OUT
- REQUIRED_SECTIONS
- FORMAT (md/html/etc)
- TONE (principles)
- CONSTRAINTS (hard)
- ACCEPTANCE_CRITERIA

## [M] KB SCOPE
- KB Inputs: [task text + provided constraints]
- KB Outputs: [doc brief token]
- KB Boundaries: [без расширения scope без входа]
- KB RAW refs: []

## [M] GATES
- PASS: brief заполнен и непротиворечив
- FAIL: неясна цель/аудитория/формат

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA, CTL]
- Handoff: DOC_BRIEF -> DOC_BUILDER

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
