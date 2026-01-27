# FILE: UE_V2/01_LAW/LAW_02.md
SCOPE: UE_V2
LAYER: 01_LAW
DOC_TYPE: LAW
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.LAW.02.001
OWNER: SYSTEM
TITLE: IDENTITY STABILITY

## MARKERS
- [M] INTENT
- [M] RULES
- [M] GATES

## [M] INTENT
UID/версии фиксируют, что является “тем же объектом”, а что “новым”.

## [M] RULES
- UID обязателен для артефакта и для сущности
- Изменение смысла/контракта = VERSION bump + CHANGE entry
- Если объект “другой” по функции/назначению → новый UID

## [M] GATES
- G.UID.MISSING = FAIL
- G.VERSION.MISSING = FAIL
- G.CHANGE.REQUIRED = REWORK_REQUIRED если смысл изменён без CHANGE записи
