FILE: UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS_CTL_ENT/16__MUS__FOCUS_LOOP_STOP_RULES__CTL__ENT.md
SCOPE: UE_V2 / 03_ENT / 40_CTL_ENT / 10_MUSIC_CONTROLLERS_CTL_ENT
DOC_TYPE: CTL_ENTITY
DOMAIN: MUS_CTL_ENT
UID: UE.V2.ENT.CTL.MUS.FOCUS_LOOP_STOP_RULES.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: CTL_ENT
NAV_RULE: No RAW in entity docs
---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_FOCUS_LOOP_STOP_RULES_CTL
- ENTITY_CLASS: CTL
- UID: UE.V2.ENT.CTL.MUS.FOCUS_LOOP_STOP_RULES.001

## [M] PURPOSE
Останавливает focus loops, если нет прогресса или начался дрейф ограничений.

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [HOOK_LOOP_NOTES, MIX_LOOP_NOTES, LYRICS_LOOP_NOTES]
- NON_GOALS: [определение бюджета шагов]

## [M] INPUTS / OUTPUTS
- Inputs: [CONSTRAINTS_LOCK?, LOOP_HISTORY?]
- Outputs: [CTL_DECISION, CTL_FINDINGS, REQUIRED_FIXES]

## [M] RULESET
- R1: Если 2 итерации подряд без улучшения -> WARN.
- R2: Если изменение нарушает CONSTRAINTS_LOCK -> FAIL.
- R3: Если неясно что улучшать -> ASK на уточнение критерия.

## [M] DECISION_MATRIX
- IF drift detected -> FAIL
- IF no progress -> WARN
- IF criterion missing -> ASK
- ELSE -> PASS

## [M] VIOLATIONS
- V.LOOP.DRIFT
- V.LOOP.NO_PROGRESS
- V.LOOP.NO_CRITERION

## [M] FAIL_CODES
- UE.FAIL.RULE_VIOLATION
- UE.FAIL.GATE_FAIL

## [M] KB SCOPE
- KB Inputs: [loop notes, constraints lock]
- KB Outputs: [stop decision]
- KB Boundaries: [не менять ограничения без входа]
- KB RAW refs: []

## [M] GATES
- PASS if: loops улучшают и не дрейфуют
- FAIL if: дрейф ограничений

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT]
- Handoff rules: FAIL -> stop; ASK -> clarify; PASS -> continue
