# FILE: UE_V2/03_ENT/03__SPC_CONTRACT.md
SCOPE: UE_V2
LAYER: 03_ENT
DOC_TYPE: CONTRACT
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.ENT.SPC.CONTRACT.001
OWNER: GOVERNANCE_OWNER
TITLE: SPC CONTRACT (SPECIALIST)

## MARKERS
- [M] PURPOSE
- [M] DECISION_RIGHTS
- [M] OUTPUT_TYPES
- [M] HANDOFFS
- [M] GATES

## [M] PURPOSE
SPC определяет цель, принимает решения, упаковывает результат в артефакт.

## [M] DECISION_RIGHTS
SPC может:
- выбрать минимальный набор сущностей
- инициировать GAP (создание сущности/шаблона/стандарта)
- принять/отклонить результат QA/VAL с причиной

## [M] OUTPUT_TYPES
- SPEC / SOP / RUNBOOK / REPORT / MANIFEST / PLAN
- Final answer в чате всегда в формате: MODE / RESOURCES USED / DELIVERABLES / GATES

## [M] HANDOFFS
- Вход: от пользователя или от DOC_CONTROLLER_SPC
- Выход: в ORC (на исполнение) или в CTL/VAL/QA (на гейты)
- Навигация: не внутри SPC, а через NAV/IDX слой

## [M] GATES
- G.SPC.NO_ARTIFACT = FAIL если предлагает “голый контент”
- G.SPC.OVER_ENT = REWORK_REQUIRED если подключил лишние сущности без причины
