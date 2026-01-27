# FILE: UE_V2/01_LAW/LAW_04.md
SCOPE: UE_V2
LAYER: 01_LAW
DOC_TYPE: LAW
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.LAW.04.001
OWNER: SYSTEM
TITLE: NAVIGATION INTEGRITY

## MARKERS
- [M] INTENT
- [M] RULES
- [M] GATES

## [M] INTENT
Навигация должна быть детерминированной. Никаких угадываний.

## [M] RULES
- RAW-only для внешнего репо
- Разрешены только ссылки пользователя или уже подтверждённые в рантайме
- Если ссылки не хватает → STOP (когда режим требует RAW) или GAP (когда строим V2_LOCAL)

## [M] GATES
- G.RAW.UNCONFIRMED = FAIL
- G.NO_GUESS = FAIL если присутствуют “предположительные” пути/ссылки
