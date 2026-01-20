# ORC PIPELINE STEP — TEMPLATE

FILE: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/00__TEMPLATES/00__TEMPLATE__ORC_PIPELINE_STEP.md
SCOPE: Universe Engine (Games volume) / Orchestrators (ORC) / Step schema template
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
ENTITY_GROUP: ORCHESTRATORS (ORC)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.GAMES.TPL.ORC.STEP.001
OWNER: SYSTEM
ROLE: Canonical schema for a single pipeline step inside any ORC entity.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MINOR
- SUMMARY: "DOC CONTROL alignment + normalized mandatory fields + gate ordering note."
- REASON: "Make steps machine-checkable and consistent."
- IMPACT: "ORC pipelines become auditable and comparable."
- CHANGE_ID: UE.CHG.2026-01-20.ORC.TPL.STEP.001

---

## STEP (SCHEMA)
STEP_ID: <01..NN>
NAME: <human-readable>
EXECUTOR_UID: <executor UID or canonical ref>
CONSUMES:
- <1..N inputs>

PRODUCES:
- <1..N outputs>

GATE: <NONE | CTL | VAL | QA | CTL+VAL | CTL+QA | VAL+QA | CTL+VAL+QA>
FAIL_SEVERITY: <S0|S1|S2|S3>
HANDOFF_TARGET: <KB|PRJ|OUT|AST|LOG|DB|NONE>
NOTES: "<optional>"

## GATE ORDER NOTE
Если указано несколько gate типов, порядок по умолчанию:
CTL → VAL → QA
Если нужно иначе, укажи явно в NOTES.
