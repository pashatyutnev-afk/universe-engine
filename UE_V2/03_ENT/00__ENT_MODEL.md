# FILE: UE_V2/03_ENT/00__ENT_MODEL.md
SCOPE: UE_V2
LAYER: 03_ENT
DOC_TYPE: MODEL
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.ENT.MODEL.001
OWNER: SYSTEM
TITLE: ENTITY MODEL (SPC/ORC/CTL/VAL/QA/XREF + REG/TPL)

## MARKERS
- [M] INTENT
- [M] ROLES
- [M] HIERARCHY
- [M] HANDOFF_RULES
- [M] MIN_SET_DEFAULT
- [M] GATES

## [M] INTENT
Определить типы сущностей и их обязанности. Никакой навигации, только роли/контракты.

## [M] ROLES
- SPC: владелец намерения/решений/упаковки результата
- ORC: пайплайн шагов и handoff
- CTL: ограничения/блокировки/стоп-условия/гейты
- VAL: проверки соответствия стандартам/метрикам
- QA: приёмка/скоринг/регресс
- XREF: карты соответствий/матрицы/маршрутизация
- REG: реестры (учёт сущностей, релизов, изменений)
- TPL: шаблоны (каркасы документов/артефактов)
- DOMAIN_PLUGIN: доменный модуль (AUD/VIS/LOR/…)

## [M] HIERARCHY
Top governance (управление рантаймом):
SPC (MACHINE_ARCHITECT) → CTL (READINESS) → VAL/QA (по задаче) → SPC (DOC_CONTROLLER) → SPC (MACHINE_ARCHITECT signoff)

## [M] HANDOFF_RULES
- Любой шаг ORC обязан иметь: INPUT → OUTPUT → NEXT OWNER
- CTL может остановить (STOP) только по runtime-stop условиям
- VAL/QA не принимают “голый контент” без артефакта

## [M] MIN_SET_DEFAULT
По умолчанию минимальный контур:
MACHINE_ARCHITECT_SPC + READINESS_CTL + DOC_CONTROLLER_SPC
Расширение добавляется только если нужен домен (AUD/VIS/LOR) или валидация/QA.

## [M] GATES
- G.ENT.MODEL.MISSING_ROLE = FAIL если тип роли не определён
- G.ENT.MODEL.NAV_INSIDE = REWORK_REQUIRED если внутри модели есть ссылки/навигация
