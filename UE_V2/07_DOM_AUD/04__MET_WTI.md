# FILE: UE_V2/07_DOM_AUD/04__MET_WTI.md
SCOPE: UE_V2
LAYER: 07_DOM_AUD
DOC_TYPE: METRIC_SPEC
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.AUD.MET.WTI.001
OWNER: SYSTEM
TITLE: METRIC WTI_t (WEAR TEXTURE INDEX)

## MARKERS
- [M] INTENT
- [M] DEFINITION
- [M] TARGET_ZONES
- [M] SAFETY

## [M] INTENT
WTI_t описывает “текстуру износа”: контролируемая шероховатость, ржавчина, пыль, глитч — не превращая микс в кашу.

## [M] DEFINITION
WTI_t ∈ [0..1].
- 0.00–0.30: чисто/полировано
- 0.31–0.60: умеренный износ (радио-допустимо)
- 0.61–0.85: высокий износ (индастриал/альт/метал)
- 0.86–1.00: экстремум (только если declared anomaly)

## [M] TARGET_ZONES
- verses/rap: WTI_t can be higher (пример: >=0.75 как в задании)
- chorus/melodic: WTI_t ниже, чтобы “надежда/воздух” раскрылась

## [M] SAFETY
WTI не имеет права убивать RI:
- если WTI растёт и RI падает ниже 0.62 в текстовых секциях → REWORK
