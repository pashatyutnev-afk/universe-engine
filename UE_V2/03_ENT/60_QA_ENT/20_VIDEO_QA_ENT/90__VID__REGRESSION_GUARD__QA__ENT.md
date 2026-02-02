FILE: UE_V2/03_ENT/60_QA_ENT/20_VIDEO_QA_ENT/90__VID__REGRESSION_GUARD__QA__ENT.md
SCOPE: UE_V2 / 03_ENT / 60_QA_ENT / 20_VIDEO_QA_ENT
DOC_TYPE: QA_ENTITY
DOMAIN: VID_QA_ENT
UID: UE.V2.ENT.QA.VID.REGRESSION_GUARD.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: QA_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: VID_REGRESSION_GUARD_QA
- ENTITY_CLASS: QA
- UID: UE.V2.ENT.QA.VID.REGRESSION_GUARD.001

## [M] PURPOSE
Гард от регрессии видео: новая итерация не должна ухудшать ключевые свойства относительно baseline.
Работает по notes/токенам (без анализа пикселей).

## [M] SCOPE
- TARGET_DOMAIN: VID
- APPLIES_TO: [BASELINE_NOTES, CURRENT_NOTES, VID_BRIEF?]
- NON_GOALS: [оценка художественного вкуса, распознавание лиц]

## [M] INPUTS / OUTPUTS
- Inputs:
  - BASELINE_NOTES?: что было хорошо/плохо в предыдущей версии
  - CURRENT_NOTES?: что стало в текущей версии
  - VID_BRIEF?: приоритеты (subject lock, стиль-свитчи, экспорт)
- Outputs:
  - QA_DECISION: PASS|WARN|ASK|FAIL
  - QA_FINDINGS: [findings]
  - REQUIRED_FIXES: [fixes]
  - ISSUES?: [issue tokens]
  - FAIL_CODE?: UE.FAIL.INPUT_ABSENT|UE.FAIL.GATE_FAIL

## [M] CHECKS
- C1: Есть baseline и current (Evidence: notes present).
- C2: Нет ухудшения по “жёстким” требованиям brief:
  - subject lock не стал хуже
  - артефактов/фликера не стало больше
  - читаемость/качество не ухудшились
- C3: Если ухудшение есть — фиксируем причину (что изменилось).

## [M] DECISION_MATRIX
- IF baseline или current отсутствуют -> ASK (V.VID.REG.NO_INPUT)
- IF регресс критичный по brief -> FAIL (UE.FAIL.GATE_FAIL; V.VID.REG.CRITICAL)
- IF регресс умеренный -> WARN (V.VID.REG.MODERATE)
- ELSE -> PASS

## [M] VIOLATIONS
- V.VID.REG.NO_INPUT — нет baseline/current notes
- V.VID.REG.CRITICAL — критический регресс относительно brief
- V.VID.REG.MODERATE — умеренный регресс, требует фиксов

## [M] FAIL_CODES
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.GATE_FAIL

## [M] KB SCOPE
- KB Inputs: [baseline/current notes, brief]
- KB Outputs: [regression findings + fixes]
- KB Boundaries: [не выдумывать качество без notes]
- KB RAW refs: []

## [M] GATES
- PASS if: нет регресса по приоритетам brief
- FAIL if: регресс критичен и ломает цель

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, CTL_ENT, VAL_ENT]
- Handoff rules:
  - ASK -> запросить baseline/current notes
  - WARN -> вернуть REQUIRED_FIXES и сделать recheck
  - FAIL -> стоп до исправления
