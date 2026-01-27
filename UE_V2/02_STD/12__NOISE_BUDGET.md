# FILE: UE_V2/02_STD/12__NOISE_BUDGET.md
SCOPE: UE_V2
LAYER: 02_STD
DOC_TYPE: STANDARD
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.STD.NOISE_BUDGET.001
OWNER: STANDARDS_OWNER
TITLE: NOISE BUDGET (ANTI-BLOAT)

## MARKERS
- [M] INTENT
- [M] LIMITS
- [M] RULES
- [M] GATES

## [M] INTENT
Чтобы система “дышала”, мы режем шум и оставляем место под смысл/контракты.

## [M] LIMITS
- Header: ≤ 12 строк (включая TITLE/UID/версию)
- Вводные: ≤ 5 строк
- Индексы: ≤ 120 строк
- Описание элемента в индексе: ≤ 1 строка
- Любая “история/философия” запрещена в стандартах и сущностях

## [M] RULES
- Всё, что не помогает действиям системы, вырезать
- Навигацию держать в NAV/IDX, а не в сущностях
- Термины уплотнять через LEX коды

## [M] GATES
- G.NOISE.HEADER = REWORK_REQUIRED если header > лимита
- G.NOISE.PROLOG = REWORK_REQUIRED если вводные > лимита
- G.NOISE.IDX = REWORK_REQUIRED если индекс > лимита
