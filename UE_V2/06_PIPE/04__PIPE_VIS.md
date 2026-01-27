# FILE: UE_V2/06_PIPE/04__PIPE_VIS.md
SCOPE: UE_V2
LAYER: 06_PIPE
DOC_TYPE: PIPELINE
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.PIPE.VIS.001
OWNER: SYSTEM
TITLE: PIPE VISUAL

## MARKERS
- [M] INTENT
- [M] REQUIRED_KB
- [M] STEPS
- [M] OUTPUTS

## [M] INTENT
Сгенерировать визуал по LAW-15: аудио-метрики управляют режимами кадра.

## [M] REQUIRED_KB
- VIS.ZP, VIS.GLT
- MAP.CF.GLITCH, MAP.LRA.ZP, MAP.AIR.DOF
Если нет → GAP (05_KB/06__KB_VIS).

## [M] STEPS
1) INPUT BIND
   - принять аудио-метрики или targets (CF/LRA/ΔAIR)
2) PROMPT BUILD
   - 5s chunks + continuity + negatives (02_STD + VIS prompt fmt)
3) SYNC MAP
   - CF>14 → GLT
   - LAW-13 + RMS drop>=12 → ZP
   - AIR 8–16k → transparency/DOF
4) VALIDATE
   - VAL_VIS
5) QA_ACCEPT
   - визуал PASS / REWORK_REQUIRED
6) PACK
   - пакет сцены/шотов/промптов

## [M] OUTPUTS
- VIS_PROMPTS (chunks)
- SYNC_NOTES (какая метрика что включила)
- ACCEPT_REPORT
