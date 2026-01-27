# FILE: UE_V2/02_STD/03__VER_CHG.md
SCOPE: UE_V2
LAYER: 02_STD
DOC_TYPE: STANDARD
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.STD.VER_CHG.001
OWNER: STANDARDS_OWNER
TITLE: VERSION + CHANGE STANDARD

## MARKERS
- [M] INTENT
- [M] CHANGE_BLOCK
- [M] BUMP_POLICY
- [M] COMPAT
- [M] GATES

## [M] INTENT
Любое изменение фиксируем минимально, но достаточно для аудита.

## [M] CHANGE_BLOCK
Если документ менялся — добавлять блок (кратко):
CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR
- SUMMARY: 1 строка
- REASON: 1 строка
- IMPACT: 1 строка
- CHANGE_ID: UE.V2.CHG.<YYYY-MM-DD>.<DOC>.<SEQ>

## [M] BUMP_POLICY
- PATCH: исправления текста, орфографии, ясности
- MINOR: новый маркер/гейт/поле без ломания
- MAJOR: меняется контракт, формат, обязательность

## [M] COMPAT
MAJOR требует:
- указать что ломается
- указать путь миграции или “BREAKING”

## [M] GATES
- G.CHG.MISSING = REWORK_REQUIRED если есть смысловая правка без CHANGE_NOTE
- G.MAJOR.NO_MIG = FAIL если MAJOR без миграции/описания ломания
