FILE: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/10__MUS__VOICE_DIVERSITY__VAL__ENT.md
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT / 10_MUSIC_VAL
DOC_TYPE: VAL_ENTITY
DOMAIN: MUS_VAL_ENT
UID: UE.V2.ENT.VAL.MUS.VOICE_DIVERSITY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: VAL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_VOICE_DIVERSITY_VAL
- ENTITY_CLASS: VAL
- UID: UE.V2.ENT.VAL.MUS.VOICE_DIVERSITY.001

## [M] PURPOSE
Проверяет, что в портфеле/серии нет “одного и того же голоса” постоянно (если заявлено разнообразие).

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [PORTFOLIO_PLAN_TOKEN?, CATALOG_NOTES?, QA_VOICE_AUDIT_TOKEN?]
- NON_GOALS: [идентификация реальных людей]

## [M] INPUTS / OUTPUTS
- Inputs: [PORTFOLIO_PLAN_TOKEN?, CATALOG_NOTES?, QA_VOICE_AUDIT_TOKEN?]
- Outputs: [VAL_DECISION, REQUIRED_FIXES, VIOLATIONS]

## [M] CHECKS
- C1: Разнообразие требуется? (Evidence: portfolio plan)
- C2: Есть evidence повторов? (Evidence: catalog/voice audit notes)

## [M] DECISION_MATRIX
- IF diversity не требуется -> PASS
- IF нет evidence -> ASK
- IF повторов много -> WARN
- ELSE -> PASS

## [M] VIOLATIONS
- V.VOICE.NO_EVIDENCE
- V.VOICE.LOW_DIVERSITY

## [M] FAIL_CODES
- UE.FAIL.INPUT_ABSENT

## [M] KB SCOPE
- KB Inputs: [internal notes]
- KB Outputs: [diversity findings]
- KB Boundaries: [не “опознавать” личности; только внутренние признаки/заметки]
- KB RAW refs: []

## [M] GATES
- PASS if: разнообразие соблюдено или не требуется
- FAIL if: разнообразие критично и системно нарушено

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, QA_ENT]
- Handoff rules: WARN -> change voice settings/brief
