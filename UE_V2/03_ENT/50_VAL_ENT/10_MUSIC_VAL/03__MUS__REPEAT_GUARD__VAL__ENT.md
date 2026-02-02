FILE: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/03__MUS__REPEAT_GUARD__VAL__ENT.md
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT / 10_MUSIC_VAL
DOC_TYPE: VAL_ENTITY
DOMAIN: MUS_VAL_ENT
UID: UE.V2.ENT.VAL.MUS.REPEAT_GUARD.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: VAL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_REPEAT_GUARD_VAL
- ENTITY_CLASS: VAL
- UID: UE.V2.ENT.VAL.MUS.REPEAT_GUARD.001

## [M] PURPOSE
Ловит “слишком много повтора”: одинаковые строки/хуки/паттерны без развития.

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [LYRICS_FINAL?, HOOK_NOTES?, TRACK_STRUCTURE?]
- NON_GOALS: [художественный вкус]

## [M] INPUTS / OUTPUTS
- Inputs: [LYRICS_FINAL?, TRACK_STRUCTURE?]
- Outputs: [VAL_DECISION, VAL_FINDINGS, REQUIRED_FIXES, VIOLATIONS]

## [M] CHECKS
- C1: Есть признаки бесконечного повторения (Evidence: lyrics/structure)
- C2: Повтор оправдан (hook) vs “каша” (Evidence: structure note)

## [M] DECISION_MATRIX
- IF нет lyrics/structure -> ASK
- IF повтор критичный без развития -> WARN
- ELSE -> PASS

## [M] VIOLATIONS
- V.REP.NO_EVIDENCE
- V.REP.EXCESSIVE

## [M] FAIL_CODES
- UE.FAIL.INPUT_ABSENT

## [M] KB SCOPE
- KB Inputs: [lyrics/structure]
- KB Outputs: [repeat findings]
- KB Boundaries: [не переписывать тексты без запроса]
- KB RAW refs: []

## [M] GATES
- PASS if: повтор контролируем
- FAIL if: повтор делает трек непригодным под цель и не фиксится без смены входа

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, CTL_ENT]
- Handoff rules: WARN -> rewrite hook/verses; ASK -> provide lyrics/structure
