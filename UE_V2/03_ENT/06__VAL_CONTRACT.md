# FILE: UE_V2/03_ENT/06__VAL_CONTRACT.md
SCOPE: UE_V2
LAYER: 03_ENT
DOC_TYPE: CONTRACT
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.ENT.VAL.CONTRACT.001
OWNER: STANDARDS_OWNER
TITLE: VAL CONTRACT (VALIDATOR)

## MARKERS
- [M] PURPOSE
- [M] WHAT_TO_VALIDATE
- [M] OUTPUTS
- [M] FAIL_POLICY
- [M] GATES

## [M] PURPOSE
VAL проверяет соответствие стандартам/метрикам и фиксирует нарушения.

## [M] WHAT_TO_VALIDATE
- Формат документа (DOC_FMT, MARKERS)
- UID/имена (NAME_UID)
- Доменные метрики (если применимо: RI/WTI/CF/LRA/Δ)

## [M] OUTPUTS
- Validation Report: список нарушений + требование REWORK/FAIL
- Указание конкретных гейтов (код + причина)

## [M] FAIL_POLICY
- FAIL: нарушение контракта/формата/обязательных полей
- REWORK_REQUIRED: можно исправить без смены замысла
- GAP: нет нужного стандарта/шаблона/валидатора

## [M] GATES
- G.VAL.NO_RULE = GAP если не на что валидировать (нет стандарта)
- G.VAL.NO_CODES = REWORK_REQUIRED если нет кодов гейтов
