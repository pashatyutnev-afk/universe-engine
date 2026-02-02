FILE: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/09__MUS__CREDITS_RIGHTS__VAL__ENT.md
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT / 10_MUSIC_VAL
DOC_TYPE: VAL_ENTITY
DOMAIN: MUS_VAL_ENT
UID: UE.V2.ENT.VAL.MUS.CREDITS_RIGHTS.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: VAL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_CREDITS_RIGHTS_VAL
- ENTITY_CLASS: VAL
- UID: UE.V2.ENT.VAL.MUS.CREDITS_RIGHTS.001

## [M] PURPOSE
Валидирует метаданные и кредитные поля: консистентность и отсутствие неподтверждённых утверждений.

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [METADATA_PACK, CREDITS_TOKEN?]
- NON_GOALS: [юридические гарантии]

## [M] INPUTS / OUTPUTS
- Inputs: [METADATA_PACK?, CREDITS_TOKEN?]
- Outputs: [VAL_DECISION, REQUIRED_FIXES, VIOLATIONS]

## [M] CHECKS
- C1: Artist/Title/Version присутствуют (Evidence: metadata)
- C2: Нет “опасных” credit claims без входа (Evidence: credits token)
- C3: Нет явного “copy” описания в метаданных (Evidence: metadata)

## [M] DECISION_MATRIX
- IF metadata отсутствует -> ASK
- IF есть неподтверждённые claims -> WARN
- IF есть признаки копирования -> FAIL
- ELSE -> PASS

## [M] VIOLATIONS
- V.CRED.MISSING_METADATA
- V.CRED.UNSUPPORTED_CLAIM
- V.CRED.COPY_RISK

## [M] FAIL_CODES
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.GATE_FAIL
- UE.FAIL.RULE_VIOLATION

## [M] KB SCOPE
- KB Inputs: [metadata/credits]
- KB Outputs: [credits findings]
- KB Boundaries: [не добавлять кредиты “от себя”]
- KB RAW refs: []

## [M] GATES
- PASS if: метаданные консистентны и без риска
- FAIL if: признаки копирования/нарушения политики

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, CTL_ENT]
- Handoff rules: FAIL -> stop; WARN -> fix metadata
