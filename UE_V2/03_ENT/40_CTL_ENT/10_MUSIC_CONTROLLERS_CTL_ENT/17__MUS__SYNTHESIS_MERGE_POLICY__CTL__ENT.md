FILE: UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS_CTL_ENT/17__MUS__SYNTHESIS_MERGE_POLICY__CTL__ENT.md
SCOPE: UE_V2 / 03_ENT / 40_CTL_ENT / 10_MUSIC_CONTROLLERS_CTL_ENT
DOC_TYPE: CTL_ENTITY
DOMAIN: MUS_CTL_ENT
UID: UE.V2.ENT.CTL.MUS.SYNTHESIS_MERGE_POLICY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: CTL_ENT
NAV_RULE: No RAW in entity docs
---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_SYNTHESIS_MERGE_POLICY_CTL
- ENTITY_CLASS: CTL
- UID: UE.V2.ENT.CTL.MUS.SYNTHESIS_MERGE_POLICY.001

## [M] PURPOSE
Политика merge: как соединять лучшие элементы вариантов в один релизный кандидат без потери консистентности.

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [MERGE_TOKEN?, VARIANT_NOTES, RELEASE_ASSET_TOKEN?]
- NON_GOALS: [создание вариантов]

## [M] INPUTS / OUTPUTS
- Inputs: [VARIANT_NOTES?, ACCEPT_CRITERIA?]
- Outputs: [CTL_DECISION, CTL_FINDINGS, REQUIRED_FIXES]

## [M] RULESET
- R1: Merge допускается только при наличии критериев выбора.
- R2: Нельзя смешивать несовместимые тональности вайба без причины.
- R3: Итог должен иметь один главный хук и одну структуру.
- R4: Merge notes должны фиксировать что взято и почему.

## [M] DECISION_MATRIX
- IF merge не требуется -> PASS
- IF criteria отсутствуют -> ASK
- IF merge создаёт конфликт консистентности -> WARN
- ELSE -> PASS

## [M] VIOLATIONS
- V.MERGE.NO_CRITERIA
- V.MERGE.INCOHERENT
- V.MERGE.NO_NOTES

## [M] FAIL_CODES
- UE.FAIL.GATE_FAIL
- UE.FAIL.INPUT_ABSENT

## [M] KB SCOPE
- KB Inputs: [variant notes, criteria]
- KB Outputs: [merge guidance]
- KB Boundaries: [не выдумывать критерии]
- KB RAW refs: []

## [M] GATES
- PASS if: merge обоснован и консистентен
- FAIL if: merge ломает консистентность без пути фикса

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, QA_ENT]
- Handoff rules: ASK -> provide criteria; PASS -> continue
