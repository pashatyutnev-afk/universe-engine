# FILE: UE_V2/06_PIPE/05__PIPE_LOR.md
SCOPE: UE_V2
LAYER: 06_PIPE
DOC_TYPE: PIPELINE
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.PIPE.LOR.001
OWNER: SYSTEM
TITLE: PIPE LORE

## MARKERS
- [M] INTENT
- [M] REQUIRED_KB
- [M] STEPS
- [M] OUTPUTS

## [M] INTENT
Генерация лора детерминирована метриками: музыка диктует событие.

## [M] REQUIRED_KB
- LOR.RI_LANG, LOR.ARC
- MAP.RI.DECAY, MAP.LRA.COLLAPSE, MAP.CF.RAGE
Если нет → GAP (05_KB/07__KB_LOR).

## [M] STEPS
1) INPUT METRICS
   - принять RI/LRA/CF + флаги LAW-13/15
2) TRIGGER SELECT
   - выбрать канон-событие по MAP*
3) ARC GEN
   - построить дугу (alienation/rage/hope) если требуется
4) VALIDATE
   - проверить “детерминировано метриками”
5) PACK
   - lore trigger artifact + краткий текст

## [M] OUTPUTS
- LORE_TRIGGER (event + причина метрикой)
- ARC_NOTES (если делали дугу)
- ACCEPT_REPORT
