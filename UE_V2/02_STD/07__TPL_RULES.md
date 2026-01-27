# FILE: UE_V2/02_STD/07__TPL_RULES.md
SCOPE: UE_V2
LAYER: 02_STD
DOC_TYPE: STANDARD
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.STD.TPL_RULES.001
OWNER: STANDARDS_OWNER
TITLE: TEMPLATE STANDARD

## MARKERS
- [M] INTENT
- [M] TEMPLATE_MIN
- [M] TEMPLATE_TYPES
- [M] GATES

## [M] INTENT
Шаблон — это минимальный “каркас”, без навигации и без воды.

## [M] TEMPLATE_MIN
Любой шаблон обязан содержать:
- HEADER_MIN (см. DOC_FMT)
- MARKERS
- обязательные поля тела (по типу)

## [M] TEMPLATE_TYPES
- TPL.LAW — шаблон закона
- TPL.STD — шаблон стандарта
- TPL.ENT — шаблон сущности (паспорт/контракт)
- TPL.REPORT — шаблон отчёта
- TPL.PACK — шаблон упаковки/манифеста

## [M] GATES
- G.TPL.MISSING_FIELDS = FAIL
- G.TPL.OVERNOISE = REWORK_REQUIRED если шаблон содержит длинные объяснения
