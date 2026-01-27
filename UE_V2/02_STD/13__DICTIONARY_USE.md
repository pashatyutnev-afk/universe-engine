# FILE: UE_V2/02_STD/13__DICTIONARY_USE.md
SCOPE: UE_V2
LAYER: 02_STD
DOC_TYPE: STANDARD
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.STD.DICT_USE.001
OWNER: STANDARDS_OWNER
TITLE: DICTIONARY / CODES USAGE

## MARKERS
- [M] INTENT
- [M] WHEN_TO_USE
- [M] HOW_TO_WRITE
- [M] COLLISION_RULES
- [M] GATES

## [M] INTENT
Словарь (LEX) нужен, чтобы “большие смыслы” жили в коротких кодах.

## [M] WHEN_TO_USE
Использовать коды:
- в отчётах (короче)
- в пайплайнах/статусах (детерминированно)
- в визуал-состояниях (VIS_STATE)
- в гейтах

## [M] HOW_TO_WRITE
Формат:
`CODE = 1-line meaning`
Примеры:
- RI = Readability Index
- WTI = Wear Texture Index
- ZP = Zero Point visual state
- REWORK = requires rework

## [M] COLLISION_RULES
- Один код = один смысл
- Новый код → добавить в LEX и зафиксировать CHANGE

## [M] GATES
- G.LEX.CODE_UNDEFINED = REWORK_REQUIRED если код использован без определения в LEX
- G.LEX.COLLISION = FAIL если код имеет 2 смысла
