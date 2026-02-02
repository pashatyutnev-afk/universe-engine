FILE: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/04__MUS__PD_ONLY__VAL__ENT.md
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT / 10_MUSIC_VAL
DOC_TYPE: VAL_ENTITY
DOMAIN: MUS_VAL_ENT
UID: UE.V2.ENT.VAL.MUS.PD_ONLY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: VAL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_PD_ONLY_VAL
- ENTITY_CLASS: VAL
- UID: UE.V2.ENT.VAL.MUS.PD_ONLY.001

## [M] PURPOSE
Блокирует прямое копирование и небезопасные требования “сделай как у X”.
Это валидатор-блокер: при триггерах сразу FAIL.

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [TASK_TEXT, PROMPT_PACK?, LYRICS_FINAL?]
- NON_GOALS: [определять юридические статусы, кроме явных триггеров]

## [M] INPUTS / OUTPUTS
- Inputs: [TASK_TEXT, PROMPT_PACK?, LYRICS_FINAL?]
- Outputs: [VAL_DECISION, VAL_FINDINGS, REQUIRED_FIXES, VIOLATIONS, FAIL_CODE?]

## [M] CHECKS
- C1: Есть требование “один в один” (Evidence: task/prompt)
- C2: Есть прямые цитаты строк (Evidence: lyrics)
- C3: Есть инструкции клонировать мелодию/аранжировку (Evidence: task/prompt)

## [M] DECISION_MATRIX
- IF any trigger detected -> FAIL (UE.FAIL.RULE_VIOLATION)
- ELSE -> PASS

## [M] VIOLATIONS
- V.PD.DIRECT_COPY
- V.PD.LYRICS_QUOTE
- V.PD.MELODY_CLONE

## [M] FAIL_CODES
- UE.FAIL.RULE_VIOLATION

## [M] KB SCOPE
- KB Inputs: [task/prompt/lyrics]
- KB Outputs: [block decision + fixes]
- KB Boundaries: [не предлагать копируемый контент]
- KB RAW refs: []

## [M] GATES
- PASS if: триггеры отсутствуют
- FAIL if: любой триггер присутствует

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, CTL_ENT, QA_ENT]
- Handoff rules: FAIL -> stop + required fixes (переформулировать на принципы)
