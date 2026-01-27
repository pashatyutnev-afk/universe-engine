# FILE: UE_V2/02_STD/11__PACKAGING.md
SCOPE: UE_V2
LAYER: 02_STD
DOC_TYPE: STANDARD
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.STD.PACKAGING.001
OWNER: STANDARDS_OWNER
TITLE: PACKAGING STANDARD (RELEASE/PACK)

## MARKERS
- [M] INTENT
- [M] PACK_MIN
- [M] MANIFEST
- [M] NAMING
- [M] GATES

## [M] INTENT
Упаковка нужна для “конвейера”: один пакет = один запуск публикации/архивации.

## [M] PACK_MIN
Для релиза минимум:
- AUDIO (файлы)
- VIS (если есть)
- LOR (если есть)
- REPORT (acceptance output)
- MANIFEST (структура и ссылки)

## [M] MANIFEST
MANIFEST включает:
- UID объекта
- список файлов пакета
- версии
- статусы (PASS/REWORK/FAIL)
- дату сборки

## [M] NAMING
`REL_<UID>_<YYYYMMDD>_<SEQ>`
Файлы внутри: короткие, без воды.

## [M] GATES
- G.PACK.MANIFEST_MISSING = FAIL
- G.PACK.INCOMPLETE = REWORK_REQUIRED если не хватает обязательных частей
