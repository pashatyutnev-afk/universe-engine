# ENG FAMILY README — KNOWLEDGE_PRODUCTION_ENGINES (TEMPLATE v2)
FILE: 00__TEMPLATE__README__KNOWLEDGE_PRODUCTION_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_GROUP: ENGINES (ENG)
TEMPLATE_KIND: FAMILY_README_OVERLAY
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Family overlay for Knowledge Production realm README. Compatible with base family template v2 and base engine template v2. Defines production artifact laws, pipeline targets, and strict boundaries vs Narrative and Music.

LOCK: FIXED
OWNER: Universe Engine

---

## 0) PURPOSE (REALM LAW)

Семейство **KNOWLEDGE_PRODUCTION_ENGINES** отвечает за производство медиа-артефактов:
- визуальная композиция
- арт-стиль (реализация style intent)
- камера/кинематография
- свет
- генерация изображений
- генерация видео
- монтаж/ритм экрана
- звук/музыка (production layer: sync/design/clarity/placement)

EXISTENCE RULE:
> Production артефакт считается валидным, когда имеет: input specs + output file + provenance + QA gate.

---

## 1) FAMILY IDENTITY (MANDATORY)

FAMILY_NAME: KNOWLEDGE_PRODUCTION_ENGINES
FAMILY_CODE: PRD
FAMILY_CLASS: PRODUCTION
FAMILY_LEVEL: L3

FAMILY_PATH:
`03_SYSTEM_ENTITIES/10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/`

README_FILE:
`00__README__KNOWLEDGE_PRODUCTION_ENGINES.md`

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

### 2.1 OWNS
- реализацию style intent в технические и художественные решения
- монтаж как screen-time конструкцию
- артефакты: изображения/видео/монтажки/аудио-стемы/сабы/метаданные
- производственный звук (sync + clarity + placement)

### 2.2 DOES NOT OWN (hard boundaries)
- story-time pacing/rhythm (как сюжет ощущается в истории) → 02 Narrative
- композиция/гармония/аранжировка как создание музыки → 09 Music
- законы мира/персонажи/сюжетная логика → 04/03/02
Rule:
> Production не меняет канон истории, он его “исполняет”.

---

## 3) CRITICAL BOUNDARIES (MANDATORY)

### 3.1 Narrative Rhythm vs Editing Rhythm
- Story-time pacing/rhythm → `02_DOMAIN_NARRATIVE_ENGINES/05__PACING_RHYTHM_ENG.md`
- Screen-time rhythm/edit/montage → `08_KNOWLEDGE_PRODUCTION_ENGINES/07__EDITING_MONTAGE_ENG.md`

### 3.2 Production Audio vs Deep Music
- Production audio (sync/design/placement/clarity) → `08__SOUND_MUSIC_ENG.md`
- Deep music (composition/harmony/arrangement/vocal/mix) → `09_SOUND_MUSIC_ENGINES/*`

---

## 4) ROLE MAP (MANDATORY)

- FOUNDATION: composition/art-style/camera/lighting
- BUILDER: image/video generation + editing + production sound
- OUTPUT: final media deliverables for selected format

### 4.1 Canonical role map table
| Engine NN | Engine Name | ROLE_IN_FAMILY | PIPELINE_STAGE |
|---|---|---|---|
| 01 | Visual Composition Engine | FOUNDATION | DEFINE |
| 02 | Art Style Engine | FOUNDATION | DEFINE |
| 03 | Camera & Cinematography Engine | FOUNDATION | DEFINE |
| 04 | Lighting Engine | FOUNDATION | DEFINE |
| 05 | Image Generation Engine | BUILDER | BUILD |
| 06 | Video Generation Engine | BUILDER | BUILD |
| 07 | Editing & Montage Engine | BUILDER | BUILD |
| 08 | Sound & Music Engine (Production Layer) | BUILDER | BUILD |

---

## 5) FAMILY OUTPUT POLICY (WORKSHOP L0–L3) — MANDATORY

Default:
- Workshop planning (L2/L3 planning):
  `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/05_PROJECT__L2/PRODUCTION_SPECS/`
  `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/05_PROJECT__L3/PRODUCTION_RUNS/`

Final outputs:
- `05_PROJECTS/<PROJECT_ID>/02_OUTPUT/<FORMAT>/`

Intermediate artifacts:
- `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/05_PROJECT__L3/04_OUTPUT_L3/PRODUCTION/`

Rule:
> Production artifacts must be traceable: each output links back to inputs and engines via provenance.

---

## 6) REQUIRED REGISTRIES (MANDATORY)

Project-scoped:
- `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.OUTPUT_L3.md` (deliverables)
- `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.RUNS.md` (recommended: production runs)

---

## 7) REQUIRED XREF INDEXES (MANDATORY)

Project-scoped:
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md` (mandatory)
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DELIVERABLE_MAP.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`

Production-specific (recommended):
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__ASSET_GRAPH.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__SHOT_OR_SCENE_TO_ASSET.md` (if used)

---

## 8) TEMPLATES (MANDATORY BLOCK)

Base templates:
- ENGINE TEMPLATE (base) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00__TEMPLATE__ENGINE__ENG.md
- FAMILY README TEMPLATE (base) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00__TEMPLATE__README__FAMILY__ENG.md

Family overlays:
- ENGINE TEMPLATE (family) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/00__TEMPLATE__ENGINE__KNOWLEDGE_PRODUCTION_ENGINES.md
- README TEMPLATE (family) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/00__TEMPLATE__README__KNOWLEDGE_PRODUCTION_ENGINES.md

---

## 9) CANON ORDER (MANDATORY)

00 — README (Realm)  
01 — Visual Composition Engine  
02 — Art Style Engine  
03 — Camera & Cinematography Engine  
04 — Lighting Engine  
05 — Image Generation Engine  
06 — Video Generation Engine  
07 — Editing & Montage Engine  
08 — Sound & Music Engine (Production Layer)  

---

## 10) GOVERNANCE COMPATIBILITY (MANDATORY)

Governance required when:
- production outputs overwrite locked canon interpretations (visual retcon)
- output deliverable rules are changed midstream
- provenance rules are violated (untraceable assets)

---

## 11) RAW LINK (MANDATORY)

RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/00__TEMPLATE__README__KNOWLEDGE_PRODUCTION_ENGINES.md

---

## FINAL RULE (LOCK)

> Production executes canon into artifacts. It does not redefine canon.

LOCK: FIXED
