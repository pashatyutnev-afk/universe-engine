# FILE: UE_V2/00_BOOT/06__TRACE.md
SCOPE: UE_V2
LAYER: 00_BOOT
DOC_TYPE: STANDARD (TRACE)
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.BOOT.TRACE.001
OWNER: SYSTEM

## MARKERS
- [M] BOOT_TRACE
- [M] RUN_TRACE
- [M] TRACE_FIELDS
- [M] TRACE_MINIMALISM

## [M] BOOT_TRACE
BOOT TRACE формируется в ответе ассистента:
- список документов, использованных в BOOT
- для каждого MARKER FOUND

## [M] RUN_TRACE
RUN TRACE = краткая трасса выполнения:
- что было принято как INPUTS
- какие решения маршрутизации приняты
- какие гейты применены
- какой артефакт выпущен

## [M] TRACE_FIELDS
Минимальные поля RUN TRACE:
- RUN_ID (может быть дата-время или UID задачи)
- TASK_UID (если есть)
- ENTITIES_USED (реально использованные)
- GATES (PASS/FAIL)
- OUTPUT_UID (артефакт)

## [M] TRACE_MINIMALISM
Трасса не должна пересказывать весь контент.
Трасса фиксирует только решения и проверки.
