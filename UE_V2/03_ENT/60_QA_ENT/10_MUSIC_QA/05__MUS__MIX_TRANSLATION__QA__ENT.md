FILE: UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/05__MUS__MIX_TRANSLATION__QA__ENT.md
SCOPE: UE_V2 / 03_ENT / 60_QA_ENT / 10_MUSIC_QA
DOC_TYPE: QA_ENTITY
DOMAIN: MUS_QA_ENT
UID: UE.V2.ENT.QA.MUS.MIX_TRANSLATION.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: QA_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_MIX_TRANSLATION_QA
- ENTITY_CLASS: QA
- UID: UE.V2.ENT.QA.MUS.MIX_TRANSLATION.001

## [M] PURPOSE
Проверяет “переводимость” микса: телефон/наушники/авто — баланс и читаемость должны сохраняться.

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [MIX_NOTES?, QA_MIX_TRANSLATION_TOKEN?]
- NON_GOALS: [LUFS измерения]

## [M] INPUTS / OUTPUTS
- Inputs: [MIX_NOTES?, QA_MIX_TRANSLATION_TOKEN?]
- Outputs: [QA_DECISION, QA_FINDINGS, REQUIRED_FIXES]

## [M] CHECKS
- C1: В телефоне не исчезает основа (вокал/мотив).
- C2: Низ не превращается в кашу.
- C3: Верх не режет ухо (сибилянты).
- C4: Общий баланс не “проваливается”.

## [M] DECISION_MATRIX
- IF нет notes -> ASK
- IF переводимость слабая -> WARN
- ELSE -> PASS

## [M] REQUIRED_FIXES
- Подправить баланс: вокал вперед, убрать грязь низа.
- Смягчить верх/сибилянты.
- Добавить читаемость на маленьких динамиках.

## [M] KB SCOPE
- KB Inputs: [mix notes]
- KB Outputs: [translation findings]
- KB Boundaries: [не выдумывать прослушивание]
- KB RAW refs: []

## [M] GATES
- PASS if: переводимость приемлема
- FAIL if: релиз и переводимость критично плохая
