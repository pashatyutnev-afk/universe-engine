FILE: UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS_CTL_ENT/14__MUS__STEP_BUDGET__CTL__ENT.md
SCOPE: UE_V2 / 03_ENT / 40_CTL_ENT / 10_MUSIC_CONTROLLERS_CTL_ENT
DOC_TYPE: CTL_ENTITY
DOMAIN: MUS_CTL_ENT
UID: UE.V2.ENT.CTL.MUS.STEP_BUDGET.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: CTL_ENT
NAV_RULE: No RAW in entity docs
---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_STEP_BUDGET_CTL
- ENTITY_CLASS: CTL
- UID: UE.V2.ENT.CTL.MUS.STEP_BUDGET.001

## [M] PURPOSE
Ограничивает количество итераций. Защищает от бесконечных циклов без улучшения.

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [STEP_TOKEN, LOOP_NOTES, QA_REPORT?]
- NON_GOALS: [оценка качества как таковая]

## [M] INPUTS / OUTPUTS
- Inputs: [EXEC_MODE?, CURRENT_STEP_COUNT?, IMPROVEMENT_NOTES?]
- Outputs: [CTL_DECISION, CTL_FINDINGS, REQUIRED_FIXES]

## [M] RULESET
- R1: Если нет измеримого прогресса 2 итерации подряд -> ASK остановку или смену стратегии.
- R2: Для RELEASE_READY рекомендованный лимит итераций: 6–10 (как принцип).
- R3: Бюджет не должен нарушать обязательные блокеры, сначала безопасность.

## [M] DECISION_MATRIX
- IF нет данных о шагах -> PASS
- IF прогресс отсутствует -> WARN
- IF лимит превышен и прогресса нет -> ASK
- ELSE -> PASS

## [M] VIOLATIONS
- V.STEP.NO_PROGRESS
- V.STEP.OVER_BUDGET

## [M] FAIL_CODES
- UE.FAIL.GATE_FAIL

## [M] KB SCOPE
- KB Inputs: [step notes]
- KB Outputs: [stop guidance]
- KB Boundaries: [не завершать релиз без решения пользователя]
- KB RAW refs: []

## [M] GATES
- PASS if: бюджет соблюдён или есть прогресс
- FAIL if: бесконечный цикл без прогресса и без решения

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT]
- Handoff rules: ASK -> user decision; PASS -> continue
