FILE: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/02__MUS__UGC_READY__VAL__ENT.md
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT / 10_MUSIC_VAL
DOC_TYPE: VAL_ENTITY
DOMAIN: MUS_VAL_ENT
UID: UE.V2.ENT.VAL.MUS.UGC_READY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: VAL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_UGC_READY_VAL
- ENTITY_CLASS: VAL
- UID: UE.V2.ENT.VAL.MUS.UGC_READY.001

## [M] PURPOSE
Валидирует “ugc-ready”: структура короткого формата не расползается, есть ясный мотив и читаемость.

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [MUS_BRIEF, TRACK_PLAN, LYRICS_FINAL?]
- NON_GOALS: [правовые выводы]

## [M] INPUTS / OUTPUTS
- Inputs: [MUS_BRIEF, TRACK_PLAN?]
- Outputs: [VAL_DECISION, VAL_FINDINGS, REQUIRED_FIXES, VIOLATIONS]

## [M] CHECKS
- C1: Контроллер применим? (Evidence: brief target)
- C2: Есть один доминирующий мотив/хук (Evidence: plan notes)
- C3: Нет перегруза текста для shortform (Evidence: lyrics density note)

## [M] DECISION_MATRIX
- IF brief не ugc -> PASS
- IF нет плана -> ASK
- IF перегруз/хаос -> WARN
- ELSE -> PASS

## [M] VIOLATIONS
- V.UGC.NO_PLAN
- V.UGC.CLUTTER

## [M] FAIL_CODES
- UE.FAIL.INPUT_ABSENT

## [M] KB SCOPE
- KB Inputs: [brief/plan]
- KB Outputs: [ugc validation]
- KB Boundaries: [не навязывать ugc]
- KB RAW refs: []

## [M] GATES
- PASS if: ugc требования соблюдены или не применимы
- FAIL if: ugc обязателен и нарушение критично

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, CTL_ENT]
- Handoff rules: WARN -> restructure; ASK -> provide plan
