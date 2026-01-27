# FILE: UE_V2/07_DOM_AUD/03__MET_RI.md
SCOPE: UE_V2
LAYER: 07_DOM_AUD
DOC_TYPE: METRIC_SPEC
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.AUD.MET.RI.001
OWNER: SYSTEM
TITLE: METRIC RI_t (READABILITY INDEX)

## MARKERS
- [M] INTENT
- [M] DEFINITION
- [M] THRESHOLDS
- [M] NOTES

## [M] INTENT
RI_t фиксирует “читабельность” текста: текст слышен как смысл, не как шум.

## [M] DEFINITION
RI_t ∈ [0..1]. Чем выше — тем меньше маскировка и выше разборчивость.
Практическая интерпретация:
- 0.80–1.00: эталонная читаемость
- 0.62–0.79: приемлемо/коммерчески ок
- <0.62: риск “грязь съела смысл” (REWORK)

## [M] THRESHOLDS
- THR.RI.MIN = 0.62 (default gate)
- RI_t must be checked in all sections containing lyrics
- in LAW-13 silence sections RI not required, but surrounding sections must pass

## [M] NOTES
Основной враг: 250–500 Hz (mud) + неконтролируемая сатурация/реверб на вокале.
