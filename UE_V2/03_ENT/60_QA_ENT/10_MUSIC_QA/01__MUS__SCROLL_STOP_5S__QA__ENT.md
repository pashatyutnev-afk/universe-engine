FILE: UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/01__MUS__SCROLL_STOP_5S__QA__ENT.md
SCOPE: UE_V2 / 03_ENT / 60_QA_ENT / 10_MUSIC_QA
DOC_TYPE: QA_ENTITY
DOMAIN: MUS_QA_ENT
UID: UE.V2.ENT.QA.MUS.SCROLL_STOP_5S.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: QA_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_SCROLL_STOP_5S_QA
- ENTITY_CLASS: QA
- UID: UE.V2.ENT.QA.MUS.SCROLL_STOP_5S.001

## [M] PURPOSE
Тест “остановки скролла”: первые 5 секунд должны зацепить.
Оценивает интро/вход, энергию, ясность хука или мотива.

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [AUDIO_CLIP_0_5S?, TRACK_TOKEN?, QA_NOTES?]
- NON_GOALS: [микс-мастеринг как проф-стандарт]

## [M] INPUTS / OUTPUTS
- Inputs: [TRACK_TOKEN?, QA_NOTES?]
- Outputs: [QA_DECISION, QA_FINDINGS, REQUIRED_FIXES, ISSUES?]

## [M] CHECKS
- C1: Есть “hook hint” или интересный мотив в 0–5с.
- C2: Нет пустого/вялого старта без причины (если не задумано).
- C3: Вокал/лид читаемы (если присутствуют).

## [M] DECISION_MATRIX
- IF нет track token/notes -> ASK
- IF старт провальный для цели shortform -> WARN
- ELSE -> PASS

## [M] REQUIRED_FIXES (examples)
- Сократить интро, сделать вход “сразу в тему”.
- Поднять энергию/ритм в первых секундах.
- Добавить ясный мотив/хук раннее.

## [M] KB SCOPE
- KB Inputs: [track token, notes]
- KB Outputs: [scroll-stop findings]
- KB Boundaries: [не выдумывать аудио]
- KB RAW refs: []

## [M] GATES
- PASS if: первые 5 секунд несут “крючок”
- FAIL if: релиз shortform и старт пустой без фикса
