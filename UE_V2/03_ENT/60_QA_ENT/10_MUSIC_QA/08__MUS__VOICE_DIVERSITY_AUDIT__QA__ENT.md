FILE: UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/08__MUS__VOICE_DIVERSITY_AUDIT__QA__ENT.md
SCOPE: UE_V2 / 03_ENT / 60_QA_ENT / 10_MUSIC_QA
DOC_TYPE: QA_ENTITY
DOMAIN: MUS_QA_ENT
UID: UE.V2.ENT.QA.MUS.VOICE_DIVERSITY_AUDIT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: QA_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_VOICE_DIVERSITY_AUDIT_QA
- ENTITY_CLASS: QA
- UID: UE.V2.ENT.QA.MUS.VOICE_DIVERSITY_AUDIT.001

## [M] PURPOSE
Аудит разнообразия голосов в батче/портфеле. Работает только по notes/токенам, без “распознавания людей”.

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [PORTFOLIO_LIST?, QA_VOICE_NOTES?]
- NON_GOALS: [идентификация реальных людей]

## [M] INPUTS / OUTPUTS
- Inputs: [PORTFOLIO_LIST?, QA_VOICE_NOTES?]
- Outputs: [QA_DECISION, QA_FINDINGS, REQUIRED_FIXES]

## [M] CHECKS
- C1: Есть список треков/вариантов.
- C2: Есть заметки о голосовых профилях (условные метки).
- C3: Нет монотонии голосов, если diversity требуется.

## [M] DECISION_MATRIX
- IF нет входа -> ASK
- IF diversity проседает -> WARN
- ELSE -> PASS

## [M] REQUIRED_FIXES
- Сменить voice preset/тембр.
- Разнести партии (м/ж/хор/без вокала).
- Развести по жанрам/регистрам.

## [M] KB SCOPE
- KB Inputs: [portfolio notes]
- KB Outputs: [diversity audit findings]
- KB Boundaries: [не делать биометрию]
- KB RAW refs: []

## [M] GATES
- PASS if: diversity приемлем
- FAIL if: diversity критично провален под заданную цель
