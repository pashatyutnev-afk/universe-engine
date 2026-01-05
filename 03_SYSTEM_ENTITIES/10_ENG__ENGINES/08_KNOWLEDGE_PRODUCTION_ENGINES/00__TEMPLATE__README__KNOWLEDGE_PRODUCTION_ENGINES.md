# ENG KNOWLEDGE PRODUCTION ENGINES — REALM (FAMILY README)
FILE: 00__README__KNOWLEDGE_PRODUCTION_ENGINES.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 08_KNOWLEDGE_PRODUCTION_ENGINES
CLASS: PRODUCTION (L3)
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
ROLE: Realm rules + boundaries + interfaces for producing visual/video/editing/sound artifacts (production layer)

---

## 0) PURPOSE (REALM LAW)

Эта FAMILY отвечает за **производство медиа-артефактов** (production layer):
- визуальная композиция
- художественный стиль исполнения (как продакшн-стайл)
- камера/кинематография
- свет
- генерация изображений
- генерация видео
- монтаж/редактирование
- звук в продакшн-слое (sync/design/placement/clarity)

Здесь делается не “что в истории”, а **как это реально произведено** и оформлено как медиа.

---

## 1) OWNERSHIP (BOUNDARIES)

### THIS FAMILY OWNS
- Shot/scene visual composition rules for output
- Visual execution style guide for production assets
- Camera language (shots, lenses, movement, framing)
- Lighting design rules for scenes/shots
- Image generation prompts/specs/pipelines
- Video generation prompts/specs/pipelines
- Editing/montage rules (screen-time rhythm, transitions, pacing in cut)
- Production audio layer (sync, clarity, placement, basic sound design integration)

### THIS FAMILY DOES NOT OWN
- Story laws / narrative logic / arcs / scenes as narrative units → `02_DOMAIN_NARRATIVE_ENGINES`
- Event mechanics / cause-effect / conflict as story mechanics → `05_EXPRESSION_ENGINES`
- Tone/atmosphere/symbolism as authorial language → `06_GENRE_STYLE_ENGINES`
- Characters psychology/dialogue content → `03_DOMAIN_CHARACTER_ENGINES`
- World laws/economy/tech/ecology → `04_DOMAIN_WORLD_ENGINES`
- Deep music (composition/harmony/arrangement/vocal/mix/master) → `09_SOUND_MUSIC_ENGINES`

---

## 2) CRITICAL BOUNDARIES (ANTI-DUPLICATION)

### Narrative Rhythm vs Editing Rhythm
- Story-time rhythm (как история “чувствуется” в тексте/сценах) → `02_DOMAIN_NARRATIVE_ENGINES/05__PACING_RHYTHM_ENG.md`
- Screen-time rhythm (как резать/монтажить, темп в кадре) → `08_KNOWLEDGE_PRODUCTION_ENGINES/07__EDITING_MONTAGE_ENG.md`

### Production Sound vs Deep Music
- Production sound (sync/design/placement/clarity, звук для сцены) → `08__SOUND_MUSIC_ENG.md`
- Deep music (композиция/гармония/аранж/вокал/микс-мастер) → `09_SOUND_MUSIC_ENGINES/*`

### Art Style vs Genre/Style
- Art style здесь = **визуальный продакшн-стайл исполнения**
- Авторский стиль/атмосфера/символизм → `06_GENRE_STYLE_ENGINES`

---

## 3) CANON ORDER (MANDATORY)

01 — Visual Composition Engine  
02 — Art Style Engine  
03 — Camera & Cinematography Engine  
04 — Lighting Engine  
05 — Image Generation Engine  
06 — Video Generation Engine  
07 — Editing & Montage Engine  
08 — Sound & Music Engine (Production Layer)  

---

## 4) PRODUCTION INTERFACES (INPUT/OUTPUT TYPES)

### INPUT TYPES (typical)
- NARRATIVE_MATERIAL (сцены/события/биты) — read-only
- STYLE_PROFILE (тон/атмосфера) — read-only
- WORLD_CONSTRAINTS (законы мира) — read-only
- FORMAT_SPEC (требования формата) — read-only
- ASSET_REQUIREMENTS (что надо произвести)
- PRODUCTION_CONSTRAINTS (время/ресурсы/инструменты)

### OUTPUT TYPES (typical)
- VISUAL_STYLE_GUIDE (для продакшна)
- SHOTLIST / STORYBOARD / SCENE_VISUAL_PLAN
- CAMERA_PLAN
- LIGHTING_PLAN
- IMAGE_PROMPT_SPEC / IMAGE_ASSET_PACK
- VIDEO_PROMPT_SPEC / VIDEO_ASSET_PACK
- EDITING_BLUEPRINT / TIMELINE_RULESET
- PRODUCTION_AUDIO_PLAN (SFX/ambience/clarity placements)

OUTPUT_TARGET (recommended):
- `04_PROJECTS/<project>/01_PRODUCTION/ASSETS/`
- `04_PROJECTS/<project>/01_PRODUCTION/EDIT/`
- `04_PROJECTS/<project>/01_PRODUCTION/AUDIO/`
- `04_PROJECTS/<project>/01_PRODUCTION/VISUAL/`

---

## 5) GOVERNANCE RULES (MANDATORY)

- Любые изменения production-пайплайна (особенно генерация/монтаж/звук) фиксируются как change request.
- Итоговые style-guides и pipeline rules — артефакты, которые должны быть воспроизводимы.

---

## 6) REQUIRED LINKS

- Global index: `../02__INDEX_ALL_ENGINES.md`
- Change Control: `../00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md`
- Narrative family: `../02_DOMAIN_NARRATIVE_ENGINES/`
- Style family: `../06_GENRE_STYLE_ENGINES/`
- Deep music family: `../09_SOUND_MUSIC_ENGINES/`

---

## 7) AUTHOR RULES (MANDATORY)

- У каждого движка обязателен mini-contract.
- Каждый движок обязан выдавать **проверяемый производственный артефакт** (гайд/план/спеки/пак).
- В каждом движке явно указать: что read-only вход (канон), а что производится (выход).

---

OWNER: Universe Engine
LOCK: OPEN
