FILE: UE_V2/03_ENT/50_VAL_ENT/11_VALIDATION_ENGINES/06__VAL_ENG__SCIENTIFIC_PLAUSIBILITY__ENG__VAL__ENT.md
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT / 11_VALIDATION_ENGINES
DOC_TYPE: VAL_ENTITY
DOMAIN: VAL_ENG_VAL_ENT
UID: UE.V2.ENT.VAL_ENG.SCIENTIFIC_PLAUSIBILITY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: VAL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: VAL_ENG_SCIENTIFIC_PLAUSIBILITY
- ENTITY_CLASS: VAL_ENG
- UID: UE.V2.ENT.VAL_ENG.SCIENTIFIC_PLAUSIBILITY.001

## [M] PURPOSE
Проверяет научную правдоподобность на уровне принципов: базовые физические ограничения, невозможные утверждения, логика причин/следствий.

## [M] SCOPE
- TARGET_DOMAIN: MULTI
- APPLIES_TO: [SCI_TEXT, TECH_SPEC, WORLD_SCIENCE_NOTES]
- NON_GOALS: [точные расчёты, внешняя верификация]

## [M] INPUTS / OUTPUTS
- Inputs: [ARTIFACT_TEXT?]
- Outputs: [VAL_DECISION, VAL_FINDINGS, REQUIRED_FIXES]

## [M] CHECKS
- C1: Нет явных физических противоречий (например, “энергия из ничего” без объяснения).
- C2: Причина/следствие описаны логично.
- C3: Ограничения признаются как ограничения (если заявлено “hard sci”).

## [M] DECISION_MATRIX
- IF text отсутствует -> ASK
- IF явные противоречия -> WARN
- IF противоречие критично и ломает заявленный стиль -> FAIL
- ELSE -> PASS

## [M] VIOLATIONS
- V.SCI.NO_INPUT
- V.SCI.IMPOSSIBLE_CLAIM
- V.SCI.CAUSALITY_BREAK

## [M] FAIL_CODES
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.GATE_FAIL

## [M] KB SCOPE
- KB Inputs: [artifact text]
- KB Outputs: [plausibility findings]
- KB Boundaries: [без внешних источников, без точных формул]
- KB RAW refs: []

## [M] GATES
- PASS if: claims plausibility acceptable for declared style
- FAIL if: critical impossibility contradicts declared constraints

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, QA_ENT]
- Handoff rules: WARN -> adjust claims; FAIL -> rewrite constraints
