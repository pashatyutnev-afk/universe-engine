# FILE: UE_V2/02_STD/01__DOC_FMT.md
SCOPE: UE_V2
LAYER: 02_STD
DOC_TYPE: STANDARD
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.STD.DOC_FMT.001
OWNER: STANDARDS_OWNER
TITLE: DOCUMENT FORMAT STANDARD

## MARKERS
- [M] INTENT
- [M] HEADER_MIN
- [M] STRUCTURE_MIN
- [M] BODY_RULES
- [M] FORBIDDEN
- [M] GATES

## [M] INTENT
Единый машинно-читаемый формат всех документов V2.

## [M] HEADER_MIN
Обязательные поля (строки):
SCOPE, LAYER, DOC_TYPE, MODE, STATUS, LOCK, VERSION, UID, OWNER, TITLE(если применимо)

## [M] STRUCTURE_MIN
- MARKERS: список маркеров документа
- Тело: секции строго с маркерами вида `## [M] NAME`

## [M] BODY_RULES
- 1 документ = 1 функция (не мешать темы)
- Текст: короткие правила, без “эссе”
- Ссылки/навигация: только где нужно (см. NAV_RULES)
- Любая таблица/список допустим, если это “данные”, а не вода

## [M] FORBIDDEN
- Длинные прологи/мотивационные тексты
- Дублирование индексов внутри документов
- “Ссылки на индекс в индексах” (NAV замыкается в циклы)

## [M] GATES
- G.DOC.HEADER = FAIL если нет HEADER_MIN
- G.DOC.MARKERS = FAIL если нет MARKERS или маркеров в теле
- G.DOC.MULTIWORK = REWORK_REQUIRED если документ делает >1 работу
