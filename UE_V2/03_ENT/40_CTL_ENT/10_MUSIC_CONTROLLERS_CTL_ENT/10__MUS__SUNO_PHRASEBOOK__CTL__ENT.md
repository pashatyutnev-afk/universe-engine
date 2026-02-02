FILE: UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS_CTL_ENT/10__MUS__SUNO_PHRASEBOOK__CTL__ENT.md
SCOPE: UE_V2 / 03_ENT / 40_CTL_ENT / 10_MUSIC_CONTROLLERS_CTL_ENT
DOC_TYPE: CTL_ENTITY
DOMAIN: MUS_CTL_ENT
UID: UE.V2.ENT.CTL.MUS.SUNO_PHRASEBOOK.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: CTL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_SUNO_PHRASEBOOK_CTL
- ENTITY_CLASS: CTL
- UID: UE.V2.ENT.CTL.MUS.SUNO_PHRASEBOOK.001

## [M] PURPOSE
Библиотека фраз и паттернов для SUNO. Запрещает восклицательные знаки и командные междометия.

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [MAIN_PROMPT, NEGATIVE_PROMPT, LYRICS]
- NON_GOALS: [жанровая аналитика]

## [M] INPUTS / OUTPUTS
- Inputs: [PROMPT_PACK?]
- Outputs: [CTL_DECISION, CTL_FINDINGS, REQUIRED_FIXES]

## [M] RULESET
- R1: В текстах и промптах не использовать восклицательные знаки.
- R2: Не начинать строки с командных междометий.
- R3: Паттерны описывать как принципы: mood, instrumentation, structure.
- R4: Не использовать имена реальных исполнителей как требование копирования.

## [M] DECISION_MATRIX
- IF PROMPT_PACK отсутствует -> PASS
- IF нарушена пунктуация -> WARN
- IF есть запрет на копирование -> FAIL (UE.FAIL.RULE_VIOLATION)
- ELSE -> PASS

## [M] VIOLATIONS
- V.SUNO.PUNCT
- V.SUNO.DIRECT_COPY

## [M] FAIL_CODES
- UE.FAIL.RULE_VIOLATION

## [M] KB SCOPE
- KB Inputs: [prompt pack]
- KB Outputs: [phrase fixes]
- KB Boundaries: [без внешних ссылок]
- KB RAW refs: []

## [M] GATES
- PASS if: соблюдены запреты
- FAIL if: прямое копирование

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT]
- Handoff rules: WARN -> normalize punctuation; PASS -> continue
