# FILE: UE_V2/03_ENT/09__DOMAIN_PLUGIN.md
SCOPE: UE_V2
LAYER: 03_ENT
DOC_TYPE: CONTRACT
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.ENT.DOMAIN.PLUGIN.001
OWNER: PIPELINE_ARCHITECT
TITLE: DOMAIN PLUGIN CONTRACT (AUD/VIS/LOR/...)

## MARKERS
- [M] PURPOSE
- [M] REQUIRED_MODULES
- [M] METRICS
- [M] OUTPUTS
- [M] GATES

## [M] PURPOSE
Доменный модуль подключает метрики + валидацию + правила упаковки.

## [M] REQUIRED_MODULES
Для любого домена:
- DOMAIN_INDEX
- METRICS (описание/пороги)
- VAL (валидатор домена)
- QA (приёмка домена)
- PACK (если домен выдаёт файлы/пакеты)

## [M] METRICS
Плагин обязан определить:
- метрики
- минимальные пороги
- fail/rework причины

## [M] OUTPUTS
- Domain Report (acceptance output)
- Domain Manifest (если применимо)

## [M] GATES
- G.DOM.PLUG.NO_MET = FAIL если домен без метрик
- G.DOM.PLUG.NO_VAL = GAP если нет валидатора для домена
