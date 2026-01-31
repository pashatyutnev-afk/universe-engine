# FILE: UE_V2/01_LAW/LAW_12.md
SCOPE: UE_V2
LAYER: 01_LAW
DOC_TYPE: LAW
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.LAW.12.001
OWNER: SYSTEM
TITLE: IMPACT PREDICT (NEURO RESPONSE)

## MARKERS
- [M] INTENT
- [M] OUTPUTS
- [M] REQUIRED_AXES
- [M] GATES

## [M] INTENT
Система обязана выдавать прогноз эмоционального воздействия на базе метрик и законов.

## [M] OUTPUTS
Impact Predictor возвращает проценты:
- Alienation%
- Rage%
- Hope/Resonance%

## [M] REQUIRED_AXES
Минимальные оси влияния:
- RI (LAW_09)
- WTI (LAW_07)
- CF/LRA (доменные метрики)
- ΔAIR/ΔLM (баланс)

## [M] GATES
- G.IMPACT.MISSING = REWORK_REQUIRED если для релиза нет прогноза
- G.IMPACT.UNEXPLAINED = REWORK_REQUIRED если прогноз без опоры на метрики
