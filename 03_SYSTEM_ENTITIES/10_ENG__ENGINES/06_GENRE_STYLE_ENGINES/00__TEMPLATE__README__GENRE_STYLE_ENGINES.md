# README TEMPLATE — GENRE & STYLE ENGINES (ENG FAMILY)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/06_GENRE_STYLE_ENGINES/00__TEMPLATE__README__GENRE_STYLE_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
ENTITY_CLASS: ENG
ENGINE_FAMILY: 06_GENRE_STYLE_ENGINES
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.ENG.STYLE.FAMILY_README.001
OWNER: SYSTEM
ROLE: Canonical template for genre/style family README (scope, style pack policy, gates, engine list policy)

---

## 0) FAMILY IDENTITY (REQUIRED)
FAMILY_NAME: 06_GENRE_STYLE_ENGINES
FAMILY_CLASS: STYLE
FAMILY_UID: UE.ENG.FAMILY.STYLE.001

---

## 1) PURPOSE (LAW)
Семейство genre/style движков задаёт:
- тон и настроение
- атмосферу
- эмоциональный резонанс
- символизм и метафорические правила
- сенсорную палитру

Цель: стабильный “стилевой слой”, который можно применять к сценам/аркам/эпизодам как артефакт (Style Profile/Pack).

---

## 2) BOUNDARIES (ANTI-DUP) — REQUIRED
OWNED HERE:
- style constraints + style artifacts (profiles/packs)

NOT OWNED HERE:
- plot/scenes structure (02_DOMAIN_NARRATIVE_ENGINES)
- character psychology (03_DOMAIN_CHARACTER_ENGINES)
- world laws (04_DOMAIN_WORLD_ENGINES)
- production technical color/editing (08_KNOWLEDGE_PRODUCTION_ENGINES)

---

## 3) FAMILY GATES (MANDATORY)
Каждый движок семейства обязан иметь минимум 5 style gates:
- tone consistency
- atmosphere coherence
- motif continuity
- sensory palette stability
- narrative compatibility

---

## 4) REQUIRED TEMPLATES
ENGINE TEMPLATE UID: UE.TPL.ENG.STYLE.ENGINE.001
FAMILY README TEMPLATE UID: UE.TPL.ENG.STYLE.FAMILY_README.001

---

## 5) ENGINE LIST POLICY (NUMBERING)
- Engine files: `NN__<NAME>_ENG.md` (NN starts at 01)
- NN in filename MUST match NN in registry / index.
- README is always `00__README__GENRE_STYLE_ENGINES.md`
- Templates are always `00__TEMPLATE__...`

---

## 6) REL / XREF (UID-FIRST)
REL:
- REL: <REL_TYPE> | TARGET: <UID> | WHY: <reason>

XREF:
- XREF: <UID> | WHY: <reason>

--- END.
