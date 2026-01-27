# FILE: UE_V2/07_DOM_AUD/06__MET_LRA.md
SCOPE: UE_V2
LAYER: 07_DOM_AUD
DOC_TYPE: METRIC_SPEC
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.AUD.MET.LRA.001
OWNER: SYSTEM
TITLE: METRIC LRA (LOUDNESS RANGE)

## MARKERS
- [M] INTENT
- [M] DEFINITION
- [M] LEGALITY
- [M] TARGETS

## [M] INTENT
LRA фиксирует драму по громкости. Это главный триггер LAW-13 (Silence Point).

## [M] DEFINITION
LRA in LU. Чем выше — тем сильнее динамический разрыв.

## [M] LEGALITY
- LRA > 12 LU = разрешено только при declared LAW-13 / anomaly profile
- если LRA > 12 без LAW-13 маркера → REWORK_REQUIRED (неуправляемый разрыв)

## [M] TARGETS
- standard rock/alt: 6–10 LU
- erosion/contrast style: 9–12 LU
- silence point / point zero: >12 LU (extreme)
