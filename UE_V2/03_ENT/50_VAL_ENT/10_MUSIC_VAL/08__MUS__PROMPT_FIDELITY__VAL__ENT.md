FILE: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/08__MUS__PROMPT_FIDELITY__VAL__ENT.md
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT / 10_MUSIC_VAL
DOC_TYPE: VAL_ENTITY
DOMAIN: MUS_VAL_ENT
UID: UE.V2.ENT.VAL.MUS.PROMPT_FIDELITY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: VAL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_PROMPT_FIDELITY_VAL
- ENTITY_CLASS: VAL
- UID: UE.V2.ENT.VAL.MUS.PROMPT_FIDELITY.001

## [M] PURPOSE
Проверяет соответствие результата brief/style: нет дрейфа жанра/темпа/настроения относительно входа.

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [MUS_BRIEF, STYLE_ROUTE_TOKEN, QA_CREATOR_PANEL_TOKEN?]
- NON_GOALS: [“вкус” и субъективщина]

## [M] INPUTS / OUTPUTS
- Inputs: [MUS_BRIEF, STYLE_ROUTE_TOKEN?, QA_CREATOR_PANEL_TOKEN?]
- Outputs: [VAL_DECISION, REQUIRED_FIXES, VIOLATIONS]

## [M] CHECKS
- C1: Есть brief и хотя бы один style token (Evidence: tokens)
- C2: Нет явного дрейфа (Evidence: creator panel notes / summary)

## [M] DECISION_MATRIX
- IF нет brief -> ASK
- IF нет style token -> ASK
- IF дрейф подтверждён -> WARN
- ELSE -> PASS

## [M] VIOLATIONS
- V.FID.NO_INPUT
- V.FID.DRIFT

## [M] FAIL_CODES
- UE.FAIL.INPUT_ABSENT

## [M] KB SCOPE
- KB Inputs: [brief/style/qa notes]
- KB Outputs: [fidelity findings]
- KB Boundaries: [не придумывать стиль]
- KB RAW refs: []

## [M] GATES
- PASS if: нет дрейфа относительно заявленного
- FAIL if: дрейф критичен и ломает цель

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, CTL_ENT, QA_ENT]
- Handoff rules: WARN -> reroute style; ASK -> provide tokens
