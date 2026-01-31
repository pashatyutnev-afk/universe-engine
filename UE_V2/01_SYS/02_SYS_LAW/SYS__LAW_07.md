# FILE: UE_V2/01_LAW/LAW_07.md
SCOPE: UE_V2
LAYER: 01_LAW
DOC_TYPE: LAW
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.LAW.07.001
OWNER: SYSTEM
TITLE: WEAR TEXTURE (WTI)

## MARKERS
- [M] INTENT
- [M] DEFINITIONS
- [M] METRIC
- [M] BOUNDS
- [M] GATES

## [M] INTENT
Текстура износа разрешена и управляемая. Это “характер”, а не брак.

## [M] DEFINITIONS
- Wear Texture = контролируемые признаки распада/зерна/грязи, которые усиливают идею
- Не должна разрушать Readability (LAW_09)

## [M] METRIC
WTI_t ∈ [0..1]
Смысл: 0 = стерильно, 1 = максимальный износ.
(Расчёт конкретной формулы задаётся в домене AUD, но закон задаёт смысл и границы)

## [M] BOUNDS
- Default group DNA: WTI_t = 0.55…0.80
- Если WTI_t > 0.85 требуется усиленная проверка RI (LAW_09)

## [M] GATES
- G.WTI.UNCONTROLLED = FAIL если износ маскирует вокал/ритм и падает RI
- G.WTI.OVER = REWORK_REQUIRED если WTI_t > 0.85 и нет причины/режима
