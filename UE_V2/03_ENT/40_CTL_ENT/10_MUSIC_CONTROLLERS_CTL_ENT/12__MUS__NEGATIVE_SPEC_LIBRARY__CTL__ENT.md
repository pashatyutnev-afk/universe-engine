FILE: UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS_CTL_ENT/12__MUS__NEGATIVE_SPEC_LIBRARY__CTL__ENT.md
SCOPE: UE_V2 / 03_ENT / 40_CTL_ENT / 10_MUSIC_CONTROLLERS_CTL_ENT
DOC_TYPE: CTL_ENTITY
DOMAIN: MUS_CTL_ENT
UID: UE.V2.ENT.CTL.MUS.NEGATIVE_SPEC_LIBRARY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: CTL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_NEGATIVE_SPEC_LIBRARY_CTL
- ENTITY_CLASS: CTL
- UID: UE.V2.ENT.CTL.MUS.NEGATIVE_SPEC_LIBRARY.001

## [M] PURPOSE
Единая библиотека negative constraints для музыки и текстов.

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [NEGATIVE_PROMPT, LYRICS]
- NON_GOALS: [аудио анализ]

## [M] INPUTS / OUTPUTS
- Inputs: [PROMPT_PACK?]
- Outputs: [CTL_DECISION, CTL_FINDINGS, REQUIRED_FIXES]

## [M] RULESET
- R1: NEGATIVE должен включать запрет прямого копирования.
- R2: NEGATIVE должен включать запрет нежелательных артефактов (noise, clipping, unintelligible vocal) как принципы.
- R3: Для текстов запрещены прямые цитаты чужих строк.

## [M] DECISION_MATRIX
- IF NEGATIVE_PROMPT отсутствует -> WARN
- IF нет запрета копирования -> WARN
- IF найдены цитаты -> FAIL
- ELSE -> PASS

## [M] VIOLATIONS
- V.NEG.MISSING
- V.NEG.NO_COPY_BAN
- V.NEG.LYRICS_QUOTE

## [M] FAIL_CODES
- UE.FAIL.RULE_VIOLATION

## [M] KB SCOPE
- KB Inputs: [prompt/lyrics]
- KB Outputs: [negative fixes]
- KB Boundaries: [не добавлять запреты вне контекста]
- KB RAW refs: []

## [M] GATES
- PASS if: negative policy соблюдена
- FAIL if: прямые цитаты или копирование

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, QA_ENT]
- Handoff rules: WARN -> patch negative; FAIL -> rewrite lyrics
