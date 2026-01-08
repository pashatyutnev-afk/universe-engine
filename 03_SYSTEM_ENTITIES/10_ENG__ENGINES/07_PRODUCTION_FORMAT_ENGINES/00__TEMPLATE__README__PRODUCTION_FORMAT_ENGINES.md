# README TEMPLATE — PRODUCTION FORMAT ENGINES (ENG FAMILY)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/07_PRODUCTION_FORMAT_ENGINES/00__TEMPLATE__README__PRODUCTION_FORMAT_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
ENTITY_CLASS: ENG
ENGINE_FAMILY: 07_PRODUCTION_FORMAT_ENGINES
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.ENG.FORMAT.FAMILY_README.001
OWNER: SYSTEM
ROLE: Canonical template for production format family README (scope, gates, deliverables, numbering policy)

---

## 0) FAMILY IDENTITY (REQUIRED)
FAMILY_NAME: 07_PRODUCTION_FORMAT_ENGINES
FAMILY_CLASS: PRODUCTION (FORMAT)
FAMILY_UID: UE.ENG.FAMILY.FORMAT.001

---

## 1) PURPOSE (LAW)
Семейство production format движков задаёт:
- форму выпуска (book/series/short/youtube/game)
- структуру единицы (chapter/episode/video/quest)
- длительности и ограничения носителя
- релизный ритм (cadence) и упаковку
- правила адаптации между форматами

Цель: любой проект может выбрать формат и получить формальный контракт, совместимый с downstream производством.

---

## 2) BOUNDARIES (ANTI-DUP) — REQUIRED
OWNED HERE:
- format contracts + deliverables definitions
- adaptation rules between formats

NOT OWNED HERE:
- story logic/scenes as content (02_DOMAIN_NARRATIVE_ENGINES)
- character internal design (03_DOMAIN_CHARACTER_ENGINES)
- world laws (04_DOMAIN_WORLD_ENGINES)
- technical production (08_KNOWLEDGE_PRODUCTION_ENGINES)

---

## 3) FAMILY GATES (MANDATORY)
Каждый движок семейства обязан иметь минимум 5 format gates:
- structure coherence
- duration compliance
- cadence compliance
- narrative compatibility
- production compatibility

---

## 4) REQUIRED TEMPLATES
ENGINE TEMPLATE UID: UE.TPL.ENG.FORMAT.ENGINE.001
FAMILY README TEMPLATE UID: UE.TPL.ENG.FORMAT.FAMILY_README.001

---

## 5) ENGINE LIST POLICY (NUMBERING)
- Engine files: `NN__<NAME>_ENG.md` (NN starts at 01)
- NN in filename MUST match NN in registry / index.
- README is always `00__README__PRODUCTION_FORMAT_ENGINES.md`
- Templates are always `00__TEMPLATE__...`

---

## 6) DELIVERABLE TYPES (DEFAULT SET)
This family outputs (minimum):
- Format Contract
- Unit Blueprint (chapter/episode/video/quest)
- Release Plan / Cadence Plan
- Adaptation Map (if transforming format)

---

## 7) REL / XREF (UID-FIRST)
REL:
- REL: <REL_TYPE> | TARGET: <UID> | WHY: <reason>

XREF:
- XREF: <UID> | WHY: <reason>

--- END.
