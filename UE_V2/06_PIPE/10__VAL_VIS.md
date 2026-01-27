# FILE: UE_V2/06_PIPE/10__VAL_VIS.md
SCOPE: UE_V2
LAYER: 06_PIPE
DOC_TYPE: VALIDATOR
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.VAL.VIS.001
OWNER: SYSTEM
TITLE: VAL VIS

## MARKERS
- [M] INTENT
- [M] REQUIRED_MAPS
- [M] CONTINUITY
- [M] FAIL_CODES

## [M] INTENT
Проверить, что LAW-15 маппинг реализован и визуал не ломает ограничения.

## [M] REQUIRED_MAPS
- CF>14 → glitch package present (если CF действительно >14)
- LAW-13 + RMS drop>=12 → ZP present
- 8–16k AIR mapping present (transparency/DOF)

## [M] CONTINUITY
- один персонаж/локация, если не указан сменный переход
- no readable text/logos/subtitles in environment
- no extra characters/weapons/explosions (если не разрешено явно)

## [M] FAIL_CODES
- REWORK.VIS.MAP_MISSING
- REWORK.VIS.CONTINUITY_BREAK
- REWORK.VIS.RESTRICTED_ELEMENTS
