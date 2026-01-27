# FILE: UE_V2/02_STD/10__REPORTS.md
SCOPE: UE_V2
LAYER: 02_STD
DOC_TYPE: STANDARD
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.STD.REPORTS.001
OWNER: STANDARDS_OWNER
TITLE: REPORTS STANDARD (ACCEPTANCE OUTPUT)

## MARKERS
- [M] INTENT
- [M] REPORT_MIN
- [M] METRICS_BLOCK
- [M] COMPARISON_BLOCK
- [M] GATES

## [M] INTENT
Отчёт нужен, чтобы фиксировать: что получилось, прошло ли, и почему.

## [M] REPORT_MIN
Отчёт обязан содержать:
- FINAL_VALUES (итоговые метрики)
- DECISIONS (что решили/почему)
- DIFFERENCES (чем отличается от референса/семьи, если нужно)
- GATES (полная таблица гейтов)

## [M] METRICS_BLOCK
Если домен AUDIO:
- RI_t, WTI_t, CF_3s_P50, LRA, ΔAIR%, ΔLM%, Low-End anchors

## [M] COMPARISON_BLOCK
Если есть “не клоны” проверка:
- указать: что именно различается (ΔAIR/ΔLM/аранж/плотность)

## [M] GATES
- G.REPORT.MIN_MISSING = FAIL
- G.REPORT.NO_GATES = FAIL
