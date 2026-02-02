FILE: UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/09__MUS__REGRESSION_GUARD__QA__ENT.md
SCOPE: UE_V2 / 03_ENT / 60_QA_ENT / 10_MUSIC_QA
DOC_TYPE: QA_ENTITY
DOMAIN: MUS_QA_ENT
UID: UE.V2.ENT.QA.MUS.REGRESSION_GUARD.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: QA_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_REGRESSION_GUARD_QA
- ENTITY_CLASS: QA
- UID: UE.V2.ENT.QA.MUS.REGRESSION_GUARD.001

## [M] PURPOSE
Гард от регрессии: новые итерации не должны делать хуже по ключевым метрикам (hook/clarity/translation).

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [BASELINE_NOTES?, CURRENT_NOTES?]
- NON_GOALS: [числовые метрики без данных]

## [M] INPUTS / OUTPUTS
- Inputs: [BASELINE_NOTES?, CURRENT_NOTES?]
- Outputs: [QA_DECISION, QA_FINDINGS, REQUIRED_FIXES]

## [M] CHECKS
- C1: Есть baseline vs current.
- C2: Нет ухудшения по: hook clarity, intro impact, mix translation.
- C3: Если ухудшение есть — зафиксировать что сломалось.

## [M] DECISION_MATRIX
- IF нет baseline/current -> ASK
- IF регресс подтвержден -> WARN
- ELSE -> PASS

## [M] REQUIRED_FIXES
- Откатить часть изменений.
- Восстановить baseline элементы (хук/баланс).
- Сравнить причины ухудшения.

## [M] KB SCOPE
- KB Inputs: [notes]
- KB Outputs: [regression report]
- KB Boundaries: [не выдумывать baseline]
- KB RAW refs: []

## [M] GATES
- PASS if: нет регресса
- FAIL if: релиз и регресс критичный
