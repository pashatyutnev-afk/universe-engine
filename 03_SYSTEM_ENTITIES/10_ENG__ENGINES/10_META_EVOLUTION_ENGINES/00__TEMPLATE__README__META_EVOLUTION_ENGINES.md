# README TEMPLATE — META EVOLUTION ENGINES (ENG FAMILY)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/10_META_EVOLUTION_ENGINES/00__TEMPLATE__README__META_EVOLUTION_ENGINES.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
ENGINE_FAMILY: 10_META_EVOLUTION_ENGINES
LEVEL: L4
STATUS: ACTIVE
VERSION: 1.0.1
ROLE: Canonical template for META family README (scope, boundary, gates, roster policy)

LOCK: FIXED
UID: <UE.TPL.ENG.META.FAMILY_README.###>       # MUST follow UID_RULES

---

## 0) FAMILY IDENTITY (REQUIRED)
FAMILY_NAME: 10_META_EVOLUTION_ENGINES
CLASS: META (L4)
FAMILY_UID: <UE.ENG.FAMILY.META.###>

---

## 1) PURPOSE (LAW)
Семейство мета-движков улучшает систему поверх всех слоёв:
- learning (обучение на истории/логах/результатах)
- pattern extraction (извлечение повторяемых паттернов)
- optimization (оптимизация правил/процессов/пайплайна)
- creative mutation (контролируемые эксперименты)
- future projection (прогнозы/сценарии/риски)

Цель: ускорять и улучшать систему без разрушения канона.

---

## 2) CRITICAL BOUNDARY (ANTI-DUP) — ABSOLUTE
OWNED HERE:
- system-level improvements, proposals, experiments, forecasts

NOT OWNED HERE:
- финальные доменные артефакты (сюжет/сцены/персы/мир/музыка/визуал)
Они принадлежат DOMAIN / EXPRESSION / PRODUCTION семействам.

---

## 3) FAMILY GATES (MANDATORY)
Каждый engine в этом семействе обязан иметь минимум:
- evidence grounded
- scope safety
- reversibility
- impact clarity
- boundary compliance

---

## 4) TEMPLATE LINKS (POLICY)
RAW links хранятся в:
- 02__INDEX_ALL_ENGINES.md (канонично)
- реестрах/индексах (канонично)

Внутри README/engine-файлов предпочитаем UID-first, чтобы не плодить “второй индекс”.

---

## 5) ROSTER (NON-CANON MIRROR) — OPTIONAL
Этот список НЕ является каноном.
Канонный состав/порядок движков хранится только в 02__INDEX_ALL_ENGINES.md.

- 01 — Learning Engine (UID: <...>)
- 02 — Pattern Extraction Engine (UID: <...>)
- 03 — Optimization Engine (UID: <...>)
- 04 — Creative Mutation Engine (UID: <...>)
- 05 — Future Projection Engine (UID: <...>)

---

## 6) NUMBERING POLICY
- Engine files: `NN__<NAME>_ENG.md` (NN starts at 01)
- README: `00__README__META_EVOLUTION_ENGINES.md`
- Templates: `00__TEMPLATE__...`

---

## 7) REL / XREF (UID-FIRST)
REL:
- REL: <REL_TYPE> | TARGET_UID: <UID> | WHY: <reason>

XREF:
- XREF_UID: <UID> | WHY: <reason>

--- END.
