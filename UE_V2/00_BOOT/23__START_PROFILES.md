# 23__START_PROFILES
SCOPE: Universe Engine (UE_V2)
DOC_TYPE: STANDARD
UID: UE.V2.STD.START_PROFILE.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)

## [M] PURPOSE
Фиксированные профили старта для детерминированности.

## [M] PROFILES
### FAST
- TRACE_LEVEL: MIN
- GATES: базовые
- OUTPUT: быстрое, допускает GAP, но без фантазии по правилам

### RELEASE_READY
- TRACE_LEVEL: STD
- GATES: доменные + compliance + UID checks
- OUTPUT: готово к публикации/канону

### MASTERPIECE
- TRACE_LEVEL: MAX
- GATES: расширенные + QA loop
- OUTPUT: максимально вылизано, но только по протоколам

## [M] LAW
- MODE_HINT пользователя маппится в START_PROFILE.
- START_PROFILE влияет только на TRACE и GATES, но не отменяет STOP/GAP.
