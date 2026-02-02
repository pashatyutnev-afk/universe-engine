FILE: UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/07__MUS__CATALOG_DIFFERENTIATION__QA__ENT.md
SCOPE: UE_V2 / 03_ENT / 60_QA_ENT / 10_MUSIC_QA
DOC_TYPE: QA_ENTITY
DOMAIN: MUS_QA_ENT
UID: UE.V2.ENT.QA.MUS.CATALOG_DIFFERENTIATION.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: QA_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_CATALOG_DIFFERENTIATION_QA
- ENTITY_CLASS: QA
- UID: UE.V2.ENT.QA.MUS.CATALOG_DIFFERENTIATION.001

## [M] PURPOSE
Проверяет различимость от внутреннего каталога по notes/evidence.
Не делает внешние проверки.

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [CATALOG_NOTES?, HOOK_NOTES?, METADATA_PACK?]
- NON_GOALS: [интернет-поиск совпадений]

## [M] INPUTS / OUTPUTS
- Inputs: [CATALOG_NOTES?]
- Outputs: [QA_DECISION, REQUIRED_FIXES, ISSUES?]

## [M] CHECKS
- C1: Есть evidence/notes сравнения.
- C2: Если найдено подозрение на повтор — фикс план.

## [M] DECISION_MATRIX
- IF нет catalog notes -> ASK
- IF есть риск сходства -> WARN
- ELSE -> PASS

## [M] REQUIRED_FIXES
- Изменить хук-мотив или ритмический рисунок.
- Изменить тембр/вокальный подход.
- Сместить гармонию/бас-линию.

## [M] KB SCOPE
- KB Inputs: [internal notes]
- KB Outputs: [differentiation findings]
- KB Boundaries: [не утверждать “уникально” без evidence]
- KB RAW refs: []

## [M] GATES
- PASS if: нет evidence совпадения
- FAIL if: совпадение подтверждено и релиз заявлен
