# FILE: UE_V2/09_DOM_LOR/01__LORE_TRIGGER.md
SCOPE: UE_V2
LAYER: 09_DOM_LOR
DOC_TYPE: SPEC
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.LOR.TRIG.001
OWNER: SYSTEM
TITLE: LORE TRIGGER MAP (METRICS → CANON EVENTS)

## MARKERS
- [M] INTENT
- [M] INPUTS
- [M] OUTPUTS
- [M] TRIGGER_TABLE
- [M] PRIORITIES
- [M] LEGALITY

## [M] INTENT
Лор реагирует на “энергетический отпечаток” музыки. Метрики — это не отчёт, это переключатели канона.

## [M] INPUTS
- RI_t (readability)
- WTI_t (wear/erosion texture)
- CF_3s_P50 (energy crest)
- LRA (dynamic rupture)
- ΔAIR, ΔLM (spectral balance deltas)
- LAW-13 flag (Silence Point)
- LAW-15 state (visual sync)

## [M] OUTPUTS
- LORE_EVENT_ID (код события)
- LORE_STATE (режим мира)
- TRIGGER_NOTE (1–2 строки, почему сработало)
- LOCK_IMPACT (что теперь запрещено менять)

## [M] TRIGGER_TABLE
T1: LANGUAGE_FRACTURE
- condition: RI_t < 0.62 for ≥ 2 sections
- meaning: распад языка/понимания, коммуникация в каноне деградирует
- output: LOR.STATE=LANG_FRACTURE

T2: SYSTEM_EROSION
- condition: WTI_t ≥ 0.75 sustained
- meaning: износ системы, мир “ржавеет”
- output: LOR.STATE=EROSION

T3: HALL_OF_FEAR
- condition: CF_3s_P50 ≥ 13.5 and LRA ≥ 10
- meaning: страх становится пространством (зал/цех/холл)
- output: LOR.EVENT=HALL_FORMATION

T4: ZERO_POINT
- condition: LAW-13 true AND RMS drop ≥ 12 dB (declared)
- meaning: Точка Ноль, вакуум смысла
- output: LOR.STATE=ZERO_POINT_LOCK

T5: FALSE_STABILITY (anti-trigger)
- condition: RI_t ≥ 0.70 AND WTI_t ≤ 0.55 for whole track
- meaning: слишком “ровно”, нет эрозии → канон не сдвигается
- output: LOR.EVENT=NO_CANON_SHIFT

## [M] PRIORITIES
- LAW-13 trigger has higher priority than others (ZP overrides)
- language fracture has priority over erosion (если оба, сначала язык)

## [M] LEGALITY
- trigger must be explainable by input metrics (no “random lore”)
- if trigger not supported by metrics → REWORK.LOR.UNGROUNDED
