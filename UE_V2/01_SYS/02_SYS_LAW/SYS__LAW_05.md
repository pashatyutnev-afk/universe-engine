# FILE: UE_V2/01_LAW/LAW_05.md
SCOPE: UE_V2
LAYER: 01_LAW
DOC_TYPE: LAW
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.LAW.05.001
OWNER: SYSTEM
TITLE: MINIMALITY

## MARKERS
- [M] INTENT
- [M] RULES
- [M] LIMITS
- [M] GATES

## [M] INTENT
Максимум полезного смысла на минимум текста и сущностей.

## [M] RULES
- 1 документ = 1 работа
- Шапка короткая, без истории “для человека”
- Подключать только минимально-достаточные сущности

## [M] LIMITS
- NOISE_BUDGET: шапка ≤ 12 строк, вводные ≤ 5 строк, остальное по делу

## [M] GATES
- G.NOISE.OVER = REWORK_REQUIRED если превышен NOISE_BUDGET
- G.ENT.OVER = REWORK_REQUIRED если подключены лишние сущности без гейта
