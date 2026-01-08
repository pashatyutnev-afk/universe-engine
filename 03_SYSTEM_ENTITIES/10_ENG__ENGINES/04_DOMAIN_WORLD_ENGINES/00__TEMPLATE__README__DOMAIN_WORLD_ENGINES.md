# README TEMPLATE — DOMAIN WORLD ENGINES (ENG FAMILY)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/00__TEMPLATE__README__DOMAIN_WORLD_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
ENTITY_CLASS: ENG
ENGINE_FAMILY: 04_DOMAIN_WORLD_ENGINES
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.ENG.DOMAIN.WORLD.FAMILY_README.001
OWNER: SYSTEM
ROLE: Canonical template for world-domain family README (scope, invariants, gates, engine list policy)

---

## 0) FAMILY IDENTITY (REQUIRED)
FAMILY_NAME: 04_DOMAIN_WORLD_ENGINES
FAMILY_CLASS: DOMAIN
FAMILY_DOMAIN: WORLD
FAMILY_UID: UE.ENG.FAMILY.DOMAIN.WORLD.001

---

## 1) PURPOSE (LAW)
Семейство world-domain движков задаёт:
- структуру мира и уровни масштаба
- законы мира и ограничения
- эпохи и хронологию
- цивилизации/институты/культуру
- конфликты и центры власти
- экономику/ресурсы/логистику
- технологию/магию и ограничения
- экологию/среду и устойчивость

---

## 2) BOUNDARIES (ANTI-DUP) — REQUIRED
OWNED HERE:
- world laws, epochs, civ structures, economy/resources, tech/magic, ecology

NOT OWNED HERE:
- narrative structure/scenes (02_DOMAIN_NARRATIVE_ENGINES)
- character psychology/voice (03_DOMAIN_CHARACTER_ENGINES)
- expression primitives (05_EXPRESSION_ENGINES)
- production/media pipeline (08_KNOWLEDGE_PRODUCTION_ENGINES)

---

## 3) FAMILY GATES (MANDATORY)
Каждый движок семейства обязан иметь минимум 5 world gates:
- internal consistency
- causality
- scalability
- narrative usability
- timeline coherence

---

## 4) REQUIRED TEMPLATES
ENGINE TEMPLATE UID: UE.TPL.ENG.DOMAIN.WORLD.ENGINE.001
FAMILY README TEMPLATE UID: UE.TPL.ENG.DOMAIN.WORLD.FAMILY_README.001

---

## 5) ENGINE LIST POLICY (NUMBERING)
- Engine files: `NN__<NAME>_ENG.md` (NN starts at 01)
- NN in filename MUST match NN in registry / index.
- README is always `00__README__DOMAIN_WORLD_ENGINES.md`
- Templates are always `00__TEMPLATE__...`

---

## 6) REL / XREF (UID-FIRST)
REL:
- REL: <REL_TYPE> | TARGET: <UID> | WHY: <reason>

XREF:
- XREF: <UID> | WHY: <reason>

--- END.
