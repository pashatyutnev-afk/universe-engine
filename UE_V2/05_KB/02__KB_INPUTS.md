# FILE: UE_V2/05_KB/02__KB_INPUTS.md
SCOPE: UE_V2
LAYER: 05_KB
DOC_TYPE: SPEC
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.KB.INPUTS.001
OWNER: SYSTEM
TITLE: KB INPUTS (ALLOWED)

## MARKERS
- [M] ALLOWED_INPUTS
- [M] INPUT_NORMALIZATION
- [M] REJECT_RULES

## [M] ALLOWED_INPUTS
KB принимает только:
- значения метрик (RI, WTI, CF, LRA, ΔAIR, ΔLM)
- диапазоны/пороги (THR)
- правила маппинга (MAP) аудио↔визуал↔лор
- коды/словарь (LEX codes)
- краткие определения терминов (DEF)

## [M] INPUT_NORMALIZATION
Единицы:
- dB, LU, Hz, % (проценты только как Δ относительно базы)
Обозначения:
- RI_t, WTI_t, CF_3s_P50, LRA, ΔAIR%, ΔLM%
Время окна:
- если метрика без окна → считается undefined → GAP (добавить)

## [M] REJECT_RULES
Отклонять как KB-вход:
- “общие советы”, “истории”, “лирика”
- ссылки на папки/структуры (это NAV)
- длинные справки без формализации (нет DEF/THR/MAP)
