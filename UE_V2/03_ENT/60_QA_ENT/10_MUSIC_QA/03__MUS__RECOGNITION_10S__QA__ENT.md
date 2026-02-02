FILE: UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/03__MUS__RECOGNITION_10S__QA__ENT.md
SCOPE: UE_V2 / 03_ENT / 60_QA_ENT / 10_MUSIC_QA
DOC_TYPE: QA_ENTITY
DOMAIN: MUS_QA_ENT
UID: UE.V2.ENT.QA.MUS.RECOGNITION_10S.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: QA_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_RECOGNITION_10S_QA
- ENTITY_CLASS: QA
- UID: UE.V2.ENT.QA.MUS.RECOGNITION_10S.001

## [M] PURPOSE
Тест узнаваемости за 10 секунд: должен появиться узнаваемый мотив/хук/тембровая фишка.

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [AUDIO_CLIP_0_10S?, TRACK_TOKEN?, QA_NOTES?]
- NON_GOALS: [жанровые споры]

## [M] INPUTS / OUTPUTS
- Inputs: [TRACK_TOKEN?, QA_NOTES?]
- Outputs: [QA_DECISION, QA_FINDINGS, REQUIRED_FIXES]

## [M] CHECKS
- C1: Есть “signature element” до 10с.
- C2: Не требует долгого вступления для понимания.
- C3: Хук/мотив читаем при типичном прослушивании.

## [M] DECISION_MATRIX
- IF нет входа -> ASK
- IF нет signature до 10с -> WARN
- ELSE -> PASS

## [M] REQUIRED_FIXES
- Вынести мотив/хук раньше.
- Сжать вступление.
- Усилить контраст/уникальную фишку.

## [M] KB SCOPE
- KB Inputs: [track token, notes]
- KB Outputs: [recognition findings]
- KB Boundaries: [не выдумывать аудио]
- KB RAW refs: []

## [M] GATES
- PASS if: узнаваемость есть
- FAIL if: shortform цель и нет узнаваемости без фикса
