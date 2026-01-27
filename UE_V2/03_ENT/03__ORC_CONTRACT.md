# FILE: UE_V2/03_ENT/03__ORC_CONTRACT.md
SCOPE: UE_V2
LAYER: 03_ENT
DOC_TYPE: CONTRACT
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.ENT.ORC.CONTRACT.001
OWNER: PIPELINE_ARCHITECT
TITLE: ORC CONTRACT (ORCHESTRATOR)

## MARKERS
- [M] PURPOSE
- [M] PIPELINE_FORMAT
- [M] STEP_RULES
- [M] HANDOFFS
- [M] GATES

## [M] PURPOSE
ORC задаёт порядок шагов и передачу ответственности (handoff).

## [M] PIPELINE_FORMAT
Каждый PIPE документ обязан содержать:
- STEPS: 1..N
- Для каждого шага: OWNER, INPUT, OUTPUT, NEXT, CHECKS

## [M] STEP_RULES
- Один шаг = одна операция
- Каждый шаг завершает артефакт/промежуточный результат
- Если входов не хватает → STOP: input absent
- Если нужен новый шаблон/сущность → GAP

## [M] HANDOFFS
ORC всегда отдаёт результат:
CTL → VAL → QA → SPC signoff (минимум цепочки определяется задачей)

## [M] GATES
- G.ORC.MISSING_IO = FAIL если шаг без INPUT/OUTPUT
- G.ORC.NO_OWNER = FAIL если шаг без OWNER
