# FILE: UE_V2/00_BOOT/07__FAIL_CODES.md
SCOPE: UE_V2
LAYER: 00_BOOT
DOC_TYPE: STANDARD (FAIL/RETURN CODES)
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.BOOT.FAILCODES.001
OWNER: SYSTEM

## MARKERS
- [M] CODES
- [M] RETURN_STATES
- [M] MAPPING_TO_GATES

## [M] CODES
CORE:
- FC.RAW.MISSING
- FC.MARKER.NOT_CONFIRMED
- FC.INPUT.ABSENT

QUALITY:
- FC.VAL.FAIL
- FC.QA.FAIL
- FC.REWORK.REQUIRED

PROCESS:
- FC.GAP.CREATED (не fail, а событие)
- FC.SIGNOFF.BLOCKED

## [M] RETURN_STATES
- PASS: гейты пройдены, артефакт выдан
- REWORK_REQUIRED: артефакт есть, но требует переработки
- STOP: выполнение прекращено по CORE причинам
- GAP_DONE: создано недостающее, пайплайн может продолжаться

## [M] MAPPING_TO_GATES
STOP всегда сопровождается:
- RAW missing: FAIL и FC.RAW.MISSING
или
- marker not confirmed: FAIL и FC.MARKER.NOT_CONFIRMED
или
- input absent: FAIL и FC.INPUT.ABSENT
