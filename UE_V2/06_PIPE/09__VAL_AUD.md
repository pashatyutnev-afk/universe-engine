# FILE: UE_V2/06_PIPE/09__VAL_AUD.md
SCOPE: UE_V2
LAYER: 06_PIPE
DOC_TYPE: VALIDATOR
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.VAL.AUD.001
OWNER: SYSTEM
TITLE: VAL AUD

## MARKERS
- [M] INTENT
- [M] THRESHOLDS
- [M] CLONE_SAFETY
- [M] SPECIAL_MODES
- [M] FAIL_CODES

## [M] INTENT
Валидация аудио-метрик под DNA сущности/семьи: читаемость + энергия + вариативность.

## [M] THRESHOLDS
- RI_t >= 0.62 (THR.RI.MIN)
- CF_3s_P50 >= 11.5 (THR.CF.REL)
- ΔAIR% >= -18% (THR.DAIR.FLOOR) если профиль требует
- ΔLM% = +5…+8% (THR.DLM.MONO) если профиль требует
- LRA > 12 LU разрешено только при LAW-13

## [M] CLONE_SAFETY
Цель: “одна сущность” ≠ “частотные клоны”.
Правило:
- треки могут иметь общую базу (targets), но должны иметь отличия в Δ.
Минимальное отличие (рекоменд.):
- |ΔAIR_i - ΔAIR_j| >= 3%
- |ΔLM_i - ΔLM_j| >= 2%
Если меньше одновременно по обоим → REWORK_REQUIRED (clone risk).

## [M] SPECIAL_MODES
LAW-13:
- допускается резкий drop (RMS >= 12 dB) и высокий LRA
- при этом RI не обязан быть высоким внутри “silence section”, но должен быть в секциях текста.

## [M] FAIL_CODES
- REWORK.AUD.RI_LOW
- REWORK.AUD.CF_LOW
- REWORK.AUD.LRA_ILLEGAL
- REWORK.AUD.CLONE_RISK
