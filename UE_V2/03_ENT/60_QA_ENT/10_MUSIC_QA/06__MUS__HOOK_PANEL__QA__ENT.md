FILE: UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/06__MUS__HOOK_PANEL__QA__ENT.md
SCOPE: UE_V2 / 03_ENT / 60_QA_ENT / 10_MUSIC_QA
DOC_TYPE: QA_ENTITY
DOMAIN: MUS_QA_ENT
UID: UE.V2.ENT.QA.MUS.HOOK_PANEL.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: QA_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_HOOK_PANEL_QA
- ENTITY_CLASS: QA
- UID: UE.V2.ENT.QA.MUS.HOOK_PANEL.001

## [M] PURPOSE
Панель хука: ясность, цепкость, “петь хочется”, длина фразы, повторяемость без раздражения.

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [HOOK_NOTES?, LYRICS_FINAL?]
- NON_GOALS: [переписывание текста без запроса]

## [M] INPUTS / OUTPUTS
- Inputs: [HOOK_NOTES?, LYRICS_FINAL?]
- Outputs: [QA_DECISION, QA_FINDINGS, REQUIRED_FIXES]

## [M] CHECKS
- C1: Хук понятен (слова/мотив читаемы).
- C2: Фраза не слишком длинная, есть “крючок”.
- C3: Повтор не раздражает.
- C4: Есть “re-listen pull” — хочется включить снова.

## [M] DECISION_MATRIX
- IF нет notes/lyrics -> ASK
- IF хук слабый -> WARN
- ELSE -> PASS

## [M] REQUIRED_FIXES
- Укоротить хук-фразу.
- Усилить ритмический рисунок/мотив.
- Убрать лишние слова, сделать “ударные” строки.

## [M] KB SCOPE
- KB Inputs: [hook notes/lyrics]
- KB Outputs: [hook findings]
- KB Boundaries: [не придумывать хук без входа]
- KB RAW refs: []

## [M] GATES
- PASS if: хук работает
- FAIL if: релиз shortform и хук не работает
