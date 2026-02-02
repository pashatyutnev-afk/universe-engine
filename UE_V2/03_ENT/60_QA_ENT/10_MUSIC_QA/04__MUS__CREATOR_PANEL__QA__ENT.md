FILE: UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/04__MUS__CREATOR_PANEL__QA__ENT.md
SCOPE: UE_V2 / 03_ENT / 60_QA_ENT / 10_MUSIC_QA
DOC_TYPE: QA_ENTITY
DOMAIN: MUS_QA_ENT
UID: UE.V2.ENT.QA.MUS.CREATOR_PANEL.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: QA_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_CREATOR_PANEL_QA
- ENTITY_CLASS: QA
- UID: UE.V2.ENT.QA.MUS.CREATOR_PANEL.001

## [M] PURPOSE
Чеклист “creator panel”: структура, вокал, энергия, ясность, соответствие brief.

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [CREATOR_PANEL_NOTES?, MUS_BRIEF?]
- NON_GOALS: [финальный мастеринг]

## [M] INPUTS / OUTPUTS
- Inputs: [CREATOR_PANEL_NOTES?, MUS_BRIEF?]
- Outputs: [QA_DECISION, QA_FINDINGS, REQUIRED_FIXES]

## [M] CHECKS
- C1: Соответствие жанра/настроения brief (по notes).
- C2: Структура читаема (интро/хук/части).
- C3: Вокал/лид не “плывут” (если есть).
- C4: Нет явных артефактов (клиппинг/ломаные слова) по notes.

## [M] DECISION_MATRIX
- IF notes отсутствуют -> ASK
- IF есть критические проблемы -> WARN
- ELSE -> PASS

## [M] REQUIRED_FIXES
- Уточнить структуру/части.
- Снизить артефакты вокала, поправить дикцию.
- Подтянуть энергию/динамику.

## [M] KB SCOPE
- KB Inputs: [notes/brief]
- KB Outputs: [creator panel findings]
- KB Boundaries: [не выдумывать notes]
- KB RAW refs: []

## [M] GATES
- PASS if: по notes всё ок
- FAIL if: релиз заявлен и есть критические артефакты
