# FILE: UE_V2/01_LAW/LAW_06.md
SCOPE: UE_V2
LAYER: 01_LAW
DOC_TYPE: LAW
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.LAW.06.001
OWNER: SYSTEM
TITLE: TRACEABILITY

## MARKERS
- [M] INTENT
- [M] RULES
- [M] GATES

## [M] INTENT
Любое решение должно быть проверяемо: что использовано, где маркер, какие гейты.

## [M] RULES
- RESOURCES USED: только реально использованное + MARKER FOUND
- Любой спорный выбор = фиксировать как decision (в TRACE или LOG)
- Без маркера документ считается “не загружен”

## [M] GATES
- G.TRACE.MISSING = FAIL если нет RESOURCES USED или MARKER FOUND
- G.DECISION.UNLOGGED = REWORK_REQUIRED если критичное решение без фиксации
