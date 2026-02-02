FILE: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/13__MUS__PROMPT_SPEC__VAL__ENT.md
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT / 10_MUSIC_VAL
DOC_TYPE: VAL_ENTITY
DOMAIN: MUS_VAL_ENT
UID: UE.V2.ENT.VAL.MUS.PROMPT_SPEC.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: VAL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_PROMPT_SPEC_VAL
- ENTITY_CLASS: VAL
- UID: UE.V2.ENT.VAL.MUS.PROMPT_SPEC.001

## [M] PURPOSE
Проверяет полноту PROMPT_PACK: есть обязательные поля и детерминированность структуры.

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [PROMPT_PACK, MAIN_PROMPT, NEGATIVE_PROMPT, PARAMS?]
- NON_GOALS: [фактическая оценка аудио]

## [M] INPUTS / OUTPUTS
- Inputs: [PROMPT_PACK?]
- Outputs: [VAL_DECISION, REQUIRED_FIXES, VIOLATIONS]

## [M] CHECKS
- C1: MAIN_PROMPT присутствует (Evidence: prompt pack)
- C2: NEGATIVE_PROMPT присутствует (Evidence: prompt pack)
- C3: Есть минимум структурных полей (genre/tempo/energy/vocal/structure hint) (Evidence: main prompt)

## [M] DECISION_MATRIX
- IF prompt pack отсутствует -> ASK
- IF missing MAIN/NEGATIVE -> FAIL
- IF missing structural fields -> WARN
- ELSE -> PASS

## [M] VIOLATIONS
- V.PSPEC.NO_PACK
- V.PSPEC.MISSING_MAIN_NEG
- V.PSPEC.MISSING_FIELDS

## [M] FAIL_CODES
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.GATE_FAIL

## [M] KB SCOPE
- KB Inputs: [prompt pack]
- KB Outputs: [spec findings]
- KB Boundaries: [не сочинять поля, если их нет]
- KB RAW refs: []

## [M] GATES
- PASS if: pack валиден
- FAIL if: отсутствуют базовые секции

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, CTL_ENT]
- Handoff rules: FAIL -> rebuild prompt pack; WARN -> add missing fields
