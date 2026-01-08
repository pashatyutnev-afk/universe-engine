# README TEMPLATE — KNOWLEDGE PRODUCTION ENGINES (ENG FAMILY)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/00__TEMPLATE__README__KNOWLEDGE_PRODUCTION_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
ENTITY_CLASS: ENG
ENGINE_FAMILY: 08_KNOWLEDGE_PRODUCTION_ENGINES
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.ENG.PROD.FAMILY_README.001
OWNER: SYSTEM
ROLE: Canonical template for production family README (scope, gates, deliverables, numbering policy)

---

## 0) FAMILY IDENTITY (REQUIRED)
FAMILY_NAME: 08_KNOWLEDGE_PRODUCTION_ENGINES
FAMILY_CLASS: PRODUCTION (MEDIA)
FAMILY_UID: UE.ENG.FAMILY.PROD.001

---

## 1) PURPOSE (LAW)
Семейство knowledge production движков отвечает за:
- визуальный язык, стиль, камеру, свет
- генерацию изображений/видео (как производство, не как сюжет)
- монтаж и ритм screen-time
- production audio (синк/чистота/плейсмент), без deep music

Цель: выдавать production packs, которые можно прямо использовать в проектах и output слоях.

---

## 2) BOUNDARIES (ANTI-DUP) — REQUIRED
OWNED HERE:
- production deliverables + gates
- continuity + technical viability for media outputs

NOT OWNED HERE:
- story logic / story-time pacing (02)
- characters (03)
- world law (04)
- deep music composition pipeline (09)

Critical boundary:
- Editing rhythm (screen-time) is here
- Narrative pacing (story-time) is in 02_DOMAIN_NARRATIVE_ENGINES

---

## 3) FAMILY GATES (MANDATORY)
Каждый движок семейства обязан иметь минимум:
- coherence gate
- continuity gate
- format compliance gate (07)
- technical viability gate
- anti-dup gate (audio vs deep music)

Severity policy (recommended):
- S0: breaks format compatibility or continuity
- S1: major coherence failure
- S2: technical suboptimal but usable
- S3: cosmetic

---

## 4) REQUIRED TEMPLATES
ENGINE TEMPLATE UID: UE.TPL.ENG.PROD.ENGINE.001
FAMILY README TEMPLATE UID: UE.TPL.ENG.PROD.FAMILY_README.001

---

## 5) ENGINE LIST POLICY (NUMBERING)
- Engine files: `NN__<NAME>_ENG.md` (NN starts at 01)
- NN in filename MUST match NN in registry / index.
- README is always `00__README__KNOWLEDGE_PRODUCTION_ENGINES.md`
- Templates are always `00__TEMPLATE__...`

---

## 6) STANDARD DELIVERABLE TYPES (DEFAULT SET)
- Style Bible / Art Bible
- Camera Grammar + Shot Plan
- Lighting Bible + Mood Map
- Generation Spec (prompt policy + constraints + seed rules)
- Edit Map (screen-time rhythm)
- Production Audio Plan (sync/clarity/placement)
- Continuity Report (what must stay consistent)

---

## 7) REL / XREF (UID-FIRST)
REL:
- REL: <REL_TYPE> | TARGET: <UID> | WHY: <reason>

XREF:
- XREF: <UID> | WHY: <reason>

--- END.
