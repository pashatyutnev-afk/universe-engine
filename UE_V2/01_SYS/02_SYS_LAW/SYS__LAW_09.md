# FILE: UE_V2/01_LAW/LAW_09.md
SCOPE: UE_V2
LAYER: 01_LAW
DOC_TYPE: LAW
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.LAW.09.001
OWNER: SYSTEM
TITLE: READABILITY BOUNDARY (RI)

## MARKERS
- [M] INTENT
- [M] DEFINITIONS
- [M] METRIC
- [M] DEFAULT_GATE
- [M] CONFLICT_WITH_WEAR
- [M] GATES

## [M] INTENT
Граница между “читаемостью” и “текстурой” задаётся метрикой RI.
RI защищает вокал, смысл, ритм-опорные элементы.

## [M] DEFINITIONS
Readability = способность слушателя распознать:
- слова (вокал/основной посыл)
- ритм-структуру
- ключевые переходы (дроп/припев/бридж)

## [M] METRIC
RI_t ∈ [0..1]
0 = неразборчиво, 1 = идеально читабельно

## [M] DEFAULT_GATE
Группа/релиз: RI_t ≥ 0.62 (если домен не переопределил)

## [M] CONFLICT_WITH_WEAR
Если WTI растёт, RI не имеет права провалиться ниже порога.
Износ “ниже RI” считается браком.

## [M] GATES
- G.RI.LOW = FAIL если RI_t < 0.62 без явно разрешённого режима
- G.RI.MASKING = REWORK_REQUIRED если провал вызван 250–500Гц или 8–16к проблемой
