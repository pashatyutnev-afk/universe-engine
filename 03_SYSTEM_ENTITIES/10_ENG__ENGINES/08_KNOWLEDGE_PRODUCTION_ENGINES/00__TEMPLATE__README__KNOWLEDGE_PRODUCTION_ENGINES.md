# ENG FAMILY README — KNOWLEDGE_PRODUCTION_ENGINES (TEMPLATE v2)
FILE: 00__TEMPLATE__README__KNOWLEDGE_PRODUCTION_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_KIND: PRD
PROJECT_SCOPE: GLOBAL
OUTPUT_LEVEL: N/A
ID: ENG.TPL.FAMILY.KNOWLEDGE_PRODUCTION.README
STATUS: ACTIVE
VERSION: 2.0
ROLE: Realm law + role map + interfaces + required REG/XREF + canon order for KNOWLEDGE_PRODUCTION family.

---

## 0) PURPOSE (REALM LAW)

Этот README — закон семейства **KNOWLEDGE_PRODUCTION_ENGINES**.
Семейство отвечает за производство медиа-артефактов:
- визуальная композиция
- арт-стиль (как арт-дирекшн)
- камера/кинематография
- свет
- генерация изображения
- генерация видео
- монтаж/склейка/тайминг (screen-time)
- production audio: синхра/ясность/раскладка, базовый sound design и placement (не deep music)

### EXISTENCE RULE (PRODUCTION)
> Любой выходной выпуск (L3) должен иметь production pipeline: план → артефакты → монтаж → финал-пак.

---

## 1) FAMILY IDENTITY (MANDATORY)

FAMILY_NAME: KNOWLEDGE_PRODUCTION_ENGINES  
FAMILY_CODE: PRD  
FAMILY_CLASS: PRODUCTION  
FAMILY_LEVEL: L3  

FAMILY_PATH: `10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/`  
README_FILE: `00__README__KNOWLEDGE_PRODUCTION_ENGINES.md`

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

### 2.1 OWNS
- Visual composition: кадр, композиционные решения
- Art style (production): визуальные правила рендера/изображения как арт-дирекшн
- Camera & cinematography: планы, движения, оптика как художественные правила
- Lighting: схема света
- Image generation: промптинг/процедуры/пайплайн генерации изображений
- Video generation: генерация видео клипов
- Editing & montage: ритм экрана (screen-time), темп склеек, тайминг
- Sound & music (production layer): sync, clarity, placement, sfx layering, basic music placement (не композиция)

### 2.2 DOES NOT OWN (hard boundaries)
- Story-time rhythm и драматургический темп истории → Narrative (02/05)
- Атомы событий/конфликта → Expression
- Психология/мотивация персонажа → Character
- Законы мира/эпохи → World
- Тон/атмосфера/символизм как закон ощущений → Style (06) (Production только применяет)
- Deep music: композиция/гармония/аранж/вокал/микс-мастер → 09_SOUND_MUSIC_ENGINES
- Governance решения → 00_GOVERNANCE_ENGINES

Boundary rule:
> Production делает экранный продукт. Он НЕ переписывает канон истории/мира/персонажей — он применяет constraints.

---

## 3) ROLE MAP (MANDATORY)

- FOUNDATION — композиция/арт-стиль/камера/свет (визуальный фундамент)
- BUILDER — генерация кадров/видео как производство ассетов
- VALIDATOR — монтажная связность и тех-валидность
- BRIDGE — сборка output packs и handoff в финал
- OUTPUT — production pack (assets + edit plan + final export spec)

### 3.1 Canonical role map table
| Engine NN | Engine Name | ROLE_IN_FAMILY | PIPELINE_STAGE |
|---|---|---|---|
| 01 | Visual Composition Engine | FOUNDATION | DEFINE |
| 02 | Art Style Engine | FOUNDATION | DEFINE |
| 03 | Camera & Cinematography Engine | FOUNDATION | DEFINE |
| 04 | Lighting Engine | FOUNDATION | DEFINE |
| 05 | Image Generation Engine | BUILDER | BUILD |
| 06 | Video Generation Engine | BUILDER | BUILD |
| 07 | Editing & Montage Engine | VALIDATOR | CHECK |
| 08 | Sound & Music Engine (Production Layer) | BRIDGE | PACKAGE |

---

## 4) PRODUCTION PACK STANDARD (MANDATORY)

Production artifacts must be structured into packs:
- PROD_PACK_ID
- INPUT_CANON_REFS (narrative/character/world/style/format)
- SHOTLIST / SCENE_BREAKDOWN (derived, not canon)
- ASSET_LIST (images/clips/audio)
- EDIT_PLAN (screen-time rhythm)
- EXPORT_SPEC (deliverables)
- PROVENANCE (what derived from what)
- XREF pointers

Rule:
> Production pack без CANON_REF на narrative/world/style/format считается “оторванным”.

---

## 5) FAMILY OUTPUT POLICY (WORKSHOP L0–L3) — MANDATORY

DEFAULT_PROJECT_OUTPUT_ROOT:
- `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`

Primary categories:
- `12_PRODUCTION/`
  - `01_PLANS/`
  - `02_ASSETS/`
  - `03_EDITS/`
  - `04_EXPORTS/`

Recommended:
- L0: черновые идеи визуала
- L1: планы/референсы/первые тесты
- L2: production canon plan (если фиксируете)
- L3: output packs и финальные экспорты

---

## 6) REQUIRED REGISTRIES (MANDATORY)

REQUIRED_REGISTRIES (project-scoped):
- `REG.PRJ.<PROJECT_ID>.OUTPUT_L3` (exports)
- `REG.PRJ.<PROJECT_ID>.ASSETS` (если есть отдельный assets registry)
- `REG.PRJ.<PROJECT_ID>.CANON_L2` (если production plan фиксируется как канон)

---

## 7) REQUIRED XREF INDEXES (MANDATORY)

REQUIRED_XREF (project-scoped):
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__ASSET_GRAPH.md` (recommended)
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__EDIT_DECISIONS.md` (recommended)

Hard rule:
> Любой монтажный план обязан ссылаться на narrative outline (CANON_REF) и format delivery spec (DEPENDS_ON).

---

## 8) INTERFACES (INPUT / OUTPUT ARTIFACT TYPES)

### 8.1 INPUT TYPES
- NARRATIVE_OUTPUT_PACK (L3) or L2 outline
- STYLE_CONSTRAINTS_PACK
- FORMAT_CONSTRAINTS_PACK + DELIVERY_SPEC
- WORLD_CONSTRAINTS_PACK
- CHARACTER_CANON (если влияет на поведение/облик)
- EXPRESSION_ATOMS (как “что должно произойти”, но не как монтаж)

### 8.2 OUTPUT TYPES
- SHOTLIST
- STORYBOARD (optional)
- ASSET_SET (images/clips)
- EDIT_PLAN (screen-time)
- SOUND_PLAN (production)
- EXPORT_SPEC + FINAL_EXPORTS
- PRODUCTION_PACK

---

## 9) TEMPLATES (MANDATORY BLOCK)

Base templates:
- FAMILY README TEMPLATE (base) — `10_ENG__ENGINES/00__TEMPLATE__README__FAMILY__ENG.md`
- ENGINE TEMPLATE (base) — `10_ENG__ENGINES/00__TEMPLATE__ENGINE__ENG.md`

Family overlays:
- README TEMPLATE (this file) — `10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/00__TEMPLATE__README__KNOWLEDGE_PRODUCTION_ENGINES.md`
- ENGINE TEMPLATE (family) — `10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/00__TEMPLATE__ENGINE__KNOWLEDGE_PRODUCTION_ENGINES.md`

---

## 10) CANON ORDER (MANDATORY)

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

## FINAL RULE (LOCK)

> Production family производит экранный продукт.  
> Он обязан быть привязан к канону через CANON_REF/DEPENDS_ON и не должен “сам менять” историю/мир/персонажей.

OWNER: Universe Engine  
LOCK: FIXED
