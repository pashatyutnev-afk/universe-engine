# FILE: UE_V2/04_NAV/00__NAV_ROOT.md
SCOPE: UE_V2
LAYER: 04_NAV
DOC_TYPE: NAV_ROOT
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.NAV.ROOT.001
OWNER: SYSTEM
TITLE: NAV ROOT (SMALL)

## MARKERS
- [M] INTENT
- [M] NAV_RULES
- [M] ENTRYPOINTS
- [M] ROUTE_MAP
- [M] STOP_CONDITIONS

## [M] INTENT
Единственный корневой нав-узел V2. Содержит только “малые” индексы.

## [M] NAV_RULES
- Навигация только через 04_NAV/* (малые индексы)
- Индексы не содержат правил/контента, только ссылки + 1 строка назначения
- Запрещены “гигантские” общие индексы (BLOAT)
- Если нужной ссылки нет → GAP (запросить/создать индекс семьи)

## [M] ENTRYPOINTS
- BOOT: 04_NAV/01__IDX_BOOT.md
- ENT:  04_NAV/02__IDX_ENT.md
- PIPE: 04_NAV/03__IDX_PIPE.md
- KB:   04_NAV/04__IDX_KB.md
- AUD:  04_NAV/05__IDX_AUD.md
- VIS:  04_NAV/06__IDX_VIS.md
- LEX:  04_NAV/07__IDX_LEX.md

## [M] ROUTE_MAP
- если задача про запуск/форматы/гейты → IDX_BOOT
- если про сущности/контракты/шаблоны → IDX_ENT
- если про пайплайны/контроль/валидации/QA → IDX_PIPE
- если про определения/границы знаний → IDX_KB
- если про аудио-метрики/ORUM → IDX_AUD
- если про визуал/Law15/промпты → IDX_VIS
- если про коды/словарь → IDX_LEX

## [M] STOP_CONDITIONS
STOP только если:
- RAW missing
- marker not confirmed
- input absent
