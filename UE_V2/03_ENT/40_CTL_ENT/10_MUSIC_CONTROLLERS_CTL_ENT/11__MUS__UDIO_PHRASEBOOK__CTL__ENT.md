FILE: UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS_CTL_ENT/11__MUS__UDIO_PHRASEBOOK__CTL__ENT.md
SCOPE: UE_V2 / 03_ENT / 40_CTL_ENT / 10_MUSIC_CONTROLLERS_CTL_ENT
DOC_TYPE: CTL_ENTITY
DOMAIN: MUS_CTL_ENT
UID: UE.V2.ENT.CTL.MUS.UDIO_PHRASEBOOK.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: CTL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_UDIO_PHRASEBOOK_CTL
- ENTITY_CLASS: CTL
- UID: UE.V2.ENT.CTL.MUS.UDIO_PHRASEBOOK.001

## [M] PURPOSE
Библиотека фраз для UDIO. Делает промпты детерминированными и безопасными.

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [MAIN_PROMPT, NEGATIVE_PROMPT]
- NON_GOALS: [контроль прав]

## [M] INPUTS / OUTPUTS
- Inputs: [PROMPT_PACK?]
- Outputs: [CTL_DECISION, CTL_FINDINGS, REQUIRED_FIXES]

## [M] RULESET
- R1: Описывать референсы как принципы, без копирования конкретных работ.
- R2: Фиксировать: tempo band, energy, vocal, structure.
- R3: NEGATIVE должен запрещать прямое копирование.

## [M] DECISION_MATRIX
- IF PROMPT_PACK отсутствует -> PASS
- IF missing structure -> WARN
- IF direct copy intent -> FAIL
- ELSE -> PASS

## [M] VIOLATIONS
- V.UDIO.MISSING_STRUCTURE
- V.UDIO.DIRECT_COPY

## [M] FAIL_CODES
- UE.FAIL.RULE_VIOLATION

## [M] KB SCOPE
- KB Inputs: [prompt pack]
- KB Outputs: [phrase fixes]
- KB Boundaries: [не выдумывать стиль без входа]
- KB RAW refs: []

## [M] GATES
- PASS if: структура ясна и безопасна
- FAIL if: копирование

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT]
- Handoff rules: WARN -> add structure; PASS -> continue
