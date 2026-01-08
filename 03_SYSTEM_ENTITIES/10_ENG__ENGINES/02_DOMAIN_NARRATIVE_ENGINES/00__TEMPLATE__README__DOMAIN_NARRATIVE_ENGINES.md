# README TEMPLATE — DOMAIN NARRATIVE ENGINES (ENG FAMILY)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/00__TEMPLATE__README__DOMAIN_NARRATIVE_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
ENTITY_CLASS: ENG
ENGINE_FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.ENG.DOMAIN.NARRATIVE.FAMILY_README.001
OWNER: SYSTEM
ROLE: Canonical template for narrative-domain family README (scope, boundaries, list policy, gates)

---

## 0) FAMILY IDENTITY (REQUIRED)
FAMILY_NAME: 02_DOMAIN_NARRATIVE_ENGINES
FAMILY_CLASS: DOMAIN
FAMILY_DOMAIN: NARRATIVE
FAMILY_UID: UE.ENG.FAMILY.DOMAIN.NARRATIVE.001

---

## 1) PURPOSE (LAW)
Семейство narrative-domain движков задаёт:
- причинно-следственную логику и структуру истории
- правила построения сцен и арок
- напряжение/ставки/пэйоффы
- тему и смысловую целостность

---

## 2) BOUNDARIES (ANTI-DUP) — REQUIRED
OWNED HERE:
- plot logic, structure, beats, scenes, escalation, payoff, continuity, theme

NOT OWNED HERE:
- character psychology/motivation (03_DOMAIN_CHARACTER_ENGINES)
- world laws/economy/epochs (04_DOMAIN_WORLD_ENGINES)
- expression primitives (05_EXPRESSION_ENGINES)
- production/editing rhythm as media timing (08_KNOWLEDGE_PRODUCTION_ENGINES)

---

## 3) FAMILY QUALITY GATES (MANDATORY)
Все движки семейства обязаны иметь минимум 5 narrative gates:
- coherence
- escalation
- clarity
- payoff
- continuity

---

## 4) REQUIRED TEMPLATES
ENGINE TEMPLATE UID: UE.TPL.ENG.DOMAIN.NARRATIVE.ENGINE.001
FAMILY README TEMPLATE UID: UE.TPL.ENG.DOMAIN.NARRATIVE.FAMILY_README.001

---

## 5) ENGINE LIST POLICY (NUMBERING)
- Folder format: `02_DOMAIN_NARRATIVE_ENGINES`
- Engine files: `NN__<NAME>_ENG.md` (NN starts at 01)
- NN in filename MUST match NN in registry / index.
- README is always `00__README__DOMAIN_NARRATIVE_ENGINES.md`
- Templates are always `00__TEMPLATE__...`

---

## 6) REL / XREF (UID-FIRST)
REL:
- REL: <REL_TYPE> | TARGET: <UID> | WHY: <reason>

XREF:
- XREF: <UID> | WHY: <reason>

--- END.
