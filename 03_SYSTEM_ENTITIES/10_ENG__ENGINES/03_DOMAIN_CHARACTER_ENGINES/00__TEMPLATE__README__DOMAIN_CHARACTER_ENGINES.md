# README TEMPLATE — DOMAIN CHARACTER ENGINES (ENG FAMILY)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/00__TEMPLATE__README__DOMAIN_CHARACTER_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
ENTITY_CLASS: ENG
ENGINE_FAMILY: 03_DOMAIN_CHARACTER_ENGINES
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.ENG.DOMAIN.CHARACTER.FAMILY_README.001
OWNER: SYSTEM
ROLE: Canonical template for character-domain family README (scope, boundaries, gate policy, engine list policy)

---

## 0) FAMILY IDENTITY (REQUIRED)
FAMILY_NAME: 03_DOMAIN_CHARACTER_ENGINES
FAMILY_CLASS: DOMAIN
FAMILY_DOMAIN: CHARACTER
FAMILY_UID: UE.ENG.FAMILY.DOMAIN.CHARACTER.001

---

## 1) PURPOSE (LAW)
Семейство character-domain движков задаёт:
- ядро личности и идентичность персонажа
- мотивации/желания/страхи
- мораль/ценности и границы
- психо-логику и причинность поведения
- отношения и динамики
- голос/диалог/естественность речи
- рост/травму/эволюцию персонажа

---

## 2) BOUNDARIES (ANTI-DUP) — REQUIRED
OWNED HERE:
- identity, motivation, morals, psychology, behavior, relationships, dialogue, growth

NOT OWNED HERE:
- plot/structure/scenes (02_DOMAIN_NARRATIVE_ENGINES)
- world rules/economy/epochs (04_DOMAIN_WORLD_ENGINES)
- production editing/shot timing (08_KNOWLEDGE_PRODUCTION_ENGINES)

---

## 3) FAMILY QUALITY GATES (MANDATORY)
Каждый движок семейства обязан иметь минимум 5 character gates:
- consistency (motive/value/action alignment)
- believability (psychological causality)
- continuity (no contradictions)
- voice stability (dialogue voice holds)
- growth logic (change has cause + cost)

---

## 4) REQUIRED TEMPLATES
ENGINE TEMPLATE UID: UE.TPL.ENG.DOMAIN.CHARACTER.ENGINE.001
FAMILY README TEMPLATE UID: UE.TPL.ENG.DOMAIN.CHARACTER.FAMILY_README.001

---

## 5) ENGINE LIST POLICY (NUMBERING)
- Engine files: `NN__<NAME>_ENG.md` (NN starts at 01)
- NN in filename MUST match NN in registry / index.
- README is always `00__README__DOMAIN_CHARACTER_ENGINES.md`
- Templates are always `00__TEMPLATE__...`

---

## 6) REL / XREF (UID-FIRST)
REL:
- REL: <REL_TYPE> | TARGET: <UID> | WHY: <reason>

XREF:
- XREF: <UID> | WHY: <reason>

--- END.
