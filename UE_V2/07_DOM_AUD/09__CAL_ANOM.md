# FILE: UE_V2/07_DOM_AUD/09__CAL_ANOM.md
SCOPE: UE_V2
LAYER: 07_DOM_AUD
DOC_TYPE: CALIBRATION_PROFILE
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.AUD.CAL.ANOM.001
OWNER: SYSTEM
TITLE: ANOMALY CALIBRATION PROFILE (POINT ZERO CLASS)

## MARKERS
- [M] INTENT
- [M] ANOMALY_FLAGS
- [M] LEGAL_OVERRIDES
- [M] DETECTION
- [M] ACCEPTANCE

## [M] INTENT
Определить, что “провал в тишину/вакуум” — художественный режим, а не технический брак.

## [M] ANOMALY_FLAGS
- FLAG.LAW13 = true (silence point declared)
- FLAG.INV_CONTRAST = true (loud→quiet)
- FLAG.SUB_ANCHOR = true (30–60 Hz “rust pulse” удерживает внимание)

## [M] LEGAL_OVERRIDES
- допускается LRA > 12 LU
- допускается RMS drop >= 12 dB на припев/переход
- RI внутри silence-section не обязателен
НО:
- RI обязателен до/после silence-section, где есть текст

## [M] DETECTION
Система распознаёт “целевой silence point”, если одновременно:
- FLAG.LAW13 присутствует в задаче/профиле
- обнаружен резкий drop (RMS drop >= 12 dB) в declared section
- суб-якорь 30–60 Hz остаётся (не ноль), поддерживая “пульс”
- нет явных аудио-ошибок (клип, цифровой треск не как WTI)

## [M] ACCEPTANCE
- CF_3s_P50 target: 13.0–14.5 dB (в пиковых секциях)
- ΔAIR floor: -18% (claustro)
- ΔLM: +5…+8% (vocal monolith)
- решение: PASS если overrides корректно помечены и метрики в пределах
