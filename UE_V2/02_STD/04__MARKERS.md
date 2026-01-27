# FILE: UE_V2/02_STD/04__MARKERS.md
SCOPE: UE_V2
LAYER: 02_STD
DOC_TYPE: STANDARD
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.STD.MARKERS.001
OWNER: STANDARDS_OWNER
TITLE: MARKERS / ANCHORS STANDARD

## MARKERS
- [M] INTENT
- [M] SYNTAX
- [M] REQUIRED_MARKERS
- [M] MARKER_FOUND_RULE
- [M] GATES

## [M] INTENT
Маркеры — это “якоря” для детерминированной загрузки смысла.

## [M] SYNTAX
- Список маркеров: `## MARKERS`
- Секция: `## [M] NAME`
- NAME: CAPS, `_`, 3–24 символа

## [M] REQUIRED_MARKERS
Для документов-правил/стандартов минимум:
- [M] INTENT
- [M] RULES или эквивалент
- [M] GATES

## [M] MARKER_FOUND_RULE
В RESOURCES USED допускается “MARKER FOUND” только если маркер реально есть в документе.
Если маркер не указан → документ считается “не загружен”.

## [M] GATES
- G.MARKERS.LIST_MISSING = FAIL если нет списка MARKERS
- G.MARKERS.SECTION_MISSING = FAIL если нет секций [M]
- G.MARKERS.FALSE = FAIL если заявлен MARKER FOUND, но его нет
