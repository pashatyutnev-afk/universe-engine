FILE: UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/02__MUS__LOOP_15S__QA__ENT.md
SCOPE: UE_V2 / 03_ENT / 60_QA_ENT / 10_MUSIC_QA
DOC_TYPE: QA_ENTITY
DOMAIN: MUS_QA_ENT
UID: UE.V2.ENT.QA.MUS.LOOP_15S.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: QA_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_LOOP_15S_QA
- ENTITY_CLASS: QA
- UID: UE.V2.ENT.QA.MUS.LOOP_15S.001

## [M] PURPOSE
Тест 15 секунд лупа: должен крутиться без ощущения “обрыва” и без раздражающего повторения.

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [LOOP_CLIP_15S?, TRACK_TOKEN?, QA_NOTES?]
- NON_GOALS: [точные измерения loudness]

## [M] INPUTS / OUTPUTS
- Inputs: [TRACK_TOKEN?, LOOP_NOTES?]
- Outputs: [QA_DECISION, QA_FINDINGS, REQUIRED_FIXES]

## [M] CHECKS
- C1: Луп звучит бесшовно (end->start).
- C2: Не раздражает при 3–5 повторах.
- C3: Нет “провала энергии” на стыке.

## [M] DECISION_MATRIX
- IF нет входа -> ASK
- IF стык слышен/ломает -> WARN
- ELSE -> PASS

## [M] REQUIRED_FIXES
- Исправить стык (tail/head), убрать щелчки/провал.
- Сделать микро-вариацию, чтобы не надоедало.

## [M] KB SCOPE
- KB Inputs: [track token, notes]
- KB Outputs: [loop findings]
- KB Boundaries: [не выдумывать аудио]
- KB RAW refs: []

## [M] GATES
- PASS if: луп бесшовный и не бесит
- FAIL if: цель shortform loop и стык критично слышен
