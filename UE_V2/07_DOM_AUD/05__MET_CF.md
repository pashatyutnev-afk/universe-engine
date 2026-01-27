# FILE: UE_V2/07_DOM_AUD/05__MET_CF.md
SCOPE: UE_V2
LAYER: 07_DOM_AUD
DOC_TYPE: METRIC_SPEC
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.AUD.MET.CF.001
OWNER: SYSTEM
TITLE: METRIC CF_3s_P50 (CREST FACTOR)

## MARKERS
- [M] INTENT
- [M] DEFINITION
- [M] THRESHOLDS
- [M] FAILURE_LOGIC

## [M] INTENT
CF — ключ к “энергетической годности”. LUFS может быть идеальным, но при низком CF трек ощущается мёртвым.

## [M] DEFINITION
CF_3s_P50 — crest factor, измеренный окнами 3s, берём медиану (P50).
Единицы: dB. Чем выше — тем больше “удар/дыхание/транзиенты”.

## [M] THRESHOLDS
- THR.CF.REL = 11.5 dB (минимум для релизной готовности)
- common “big chorus” target: 12.5–14.0 dB
- anomaly (Point Zero): 13.0–14.5 dB

## [M] FAILURE_LOGIC
- если CF < THR.CF.REL → REWORK_REQUIRED (энергетический брак)
- если CF слишком высок и ломает тональный баланс/слушабельность → REWORK (перекус транзиентов)
