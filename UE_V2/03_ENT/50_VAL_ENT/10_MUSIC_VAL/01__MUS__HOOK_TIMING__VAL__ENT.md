FILE: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/01__MUS__HOOK_TIMING__VAL__ENT.md
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT / 10_MUSIC_VAL
DOC_TYPE: VAL_ENTITY
DOMAIN: MUS_VAL_ENT
UID: UE.V2.ENT.VAL.MUS.HOOK_TIMING.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: VAL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_HOOK_TIMING_VAL
- ENTITY_CLASS: VAL
- UID: UE.V2.ENT.VAL.MUS.HOOK_TIMING.001

## [M] PURPOSE
Проверяет, что хук появляется в нужном тайм-окне, если цель shortform/ugc это требует.

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [TRACK_PLAN, QA_HOOK_PANEL_TOKEN?, STRUCTURE_NOTES?]
- NON_GOALS: [оценка качества звучания]

## [M] INPUTS / OUTPUTS
- Inputs: [MUS_BRIEF, TRACK_PLAN?, QA_HOOK_PANEL_TOKEN?]
- Outputs: [VAL_DECISION, VAL_FINDINGS, REQUIRED_FIXES, VIOLATIONS, FAIL_CODE?]

## [M] CHECKS
- C1: UGC/shortform применим? (Evidence: MUS_BRIEF target)
- C2: Хук тайминг определён? (Evidence: TRACK_PLAN or QA_HOOK_PANEL_TOKEN)
- C3: Хук <= 10s (для shortform принцип) (Evidence: timestamp note)

## [M] EVIDENCE_REQUIREMENTS
- E1: Для PASS нужен явный timestamp или структура, где видно хук.
- E2: Если evidence отсутствует -> ASK, а не PASS.
- E3: Если хук поздно при ugc -> WARN.

## [M] DECISION_MATRIX
- IF brief не ugc -> PASS
- IF нет плана/тайминга -> ASK
- IF hook_time > 10s -> WARN
- ELSE -> PASS

## [M] VIOLATIONS
- V.HOOK.NO_EVIDENCE
- V.HOOK.LATE

## [M] FAIL_CODES
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.GATE_FAIL

## [M] KB SCOPE
- KB Inputs: [brief, plan, hook panel token]
- KB Outputs: [validation notes]
- KB Boundaries: [не угадывать время хука]
- KB RAW refs: []

## [M] GATES
- PASS if: либо не ugc, либо evidence подтверждает ранний хук
- FAIL if: ugc обязателен и хук системно поздний без пути фикса

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, CTL_ENT, QA_ENT]
- Handoff rules: WARN -> hook loop; ASK -> request plan/timing
