# README TEMPLATE — META EVOLUTION ENGINES (ENG FAMILY)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/10_META_EVOLUTION_ENGINES/00__TEMPLATE__README__META_EVOLUTION_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
ENTITY_CLASS: ENG
ENGINE_FAMILY: 10_META_EVOLUTION_ENGINES
LEVEL: L4
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.ENG.META.FAMILY_README.001
OWNER: SYSTEM
ROLE: Canonical template for meta-evolution family README (scope, boundary, gates, engine list policy)

---

## 0) FAMILY IDENTITY (REQUIRED)
FAMILY_NAME: 10_META_EVOLUTION_ENGINES
FAMILY_CLASS: META (SYSTEM EVOLUTION)
FAMILY_UID: UE.ENG.FAMILY.META.001

---

## 1) PURPOSE (LAW)
Семейство мета-движков отвечает за эволюцию системы:
- learning (обучение на истории/логах/результатах)
- pattern extraction (извлечение повторяемых паттернов)
- optimization (оптимизация правил/процессов/пайплайна)
- creative mutation (контролируемые эксперименты)
- future projection (прогнозы/сценарии/риски)

Цель: улучшать качество и скорость системы, не ломая канон.

---

## 2) CRITICAL BOUNDARY (ANTI-DUP) — ABSOLUTE
OWNED HERE:
- system-level improvements, proposals, experiments, forecasts

NOT OWNED HERE:
- domain final deliverables (scenes/characters/world/music/visual)
These belong to domain / expression / production families.

---

## 3) FAMILY GATES (MANDATORY)
Каждый мета-движок обязан иметь минимум 5 meta gates:
- evidence grounded
- scope safety
- reversibility
- impact clarity
- boundary compliance

---

## 4) REQUIRED TEMPLATES
ENGINE TEMPLATE UID: UE.TPL.ENG.META.ENGINE.001
FAMILY README TEMPLATE UID: UE.TPL.ENG.META.FAMILY_README.001

---

## 5) ENGINE LIST POLICY (NUMBERING)
- Engine files: `NN__<NAME>_ENG.md` (NN starts at 01)
- NN in filename MUST match NN in registry / index.
- README is always `00__README__META_EVOLUTION_ENGINES.md`
- Templates are always `00__TEMPLATE__...`

---

## 6) REL / XREF (UID-FIRST)
REL:
- REL: <REL_TYPE> | TARGET: <UID> | WHY: <reason>

XREF:
- XREF: <UID> | WHY: <reason>

--- END.
