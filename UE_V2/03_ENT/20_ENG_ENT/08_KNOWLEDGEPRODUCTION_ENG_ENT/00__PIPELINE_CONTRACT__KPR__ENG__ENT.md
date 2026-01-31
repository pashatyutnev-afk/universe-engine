# 08_KNOWLEDGE_PRODUCTION_ENGINES — REALM README (CANON)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/00__README__KNOWLEDGE_PRODUCTION_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: README
FAMILY: 08_KNOWLEDGE_PRODUCTION_ENGINES
CLASS: PRODUCTION (L3)
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ENG.FAM.08.README.001
OWNER: SYSTEM
ROLE: Realm definition for Knowledge Production engines: visual/audio production implementation layer, boundaries, canonical order, usage pipelines, and template contracts.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Family README created: defines scope/boundaries/order for Knowledge Production engines."
- REASON: "Stamping media artifacts needs deterministic production layer ownership."
- IMPACT: "Visual/video/audio production becomes reproducible and separated from narrative canon and deep music."
- CHANGE_ID: UE.CHG.2026-01-08.PROD.KP.README.001

---

## 0) PURPOSE (LAW)
This FAMILY owns **PRODUCTION IMPLEMENTATION** for media artifacts:
- composition / style / camera / lighting (visual implementation)
- image generation spec + video generation spec (generator-ready artifacts)
- editing & montage (screen-time rhythm owner)
- production audio placement/design/clarity (sync/placement layer)

Hard rule:
- This family implements production plans/specs. It does NOT own story content or deep music composition.

---

## 1) BOUNDARIES (STRICT)
IN SCOPE:
- VISUAL implementation constraints and plans:
  - composition (frame hierarchy, focal routing) — constraints
  - art style (render language, palette policies) — constraints
  - camera & cinematography (lens/move grammar) — implementation plan
  - lighting (key/fill/rim policies) — implementation plan
- GENERATION specs:
  - image generation prompt blueprint + batch plan
  - video generation clip blueprint + continuity constraints + batch plan
- EDITING:
  - editing/montage (screen-time sequencing + cut rhythm + patterns)
- PRODUCTION AUDIO:
  - sync/design/placement/clarity guardrails (dialogue priority, layers, cue map)

OUT OF SCOPE:
- story logic / plot / pacing in story-time (02 family narrative engines)
- characters/world canon (03/04 domain engines)
- tone/mood/atmosphere ownership (06 style family owns those primitives; here only consumption)
- deep music composition/harmony/arrangement/vocal/mix-master (09 sound music family)
- marketing/distribution (KB/other layers)

CRITICAL BOUNDARIES (from your law):
- Story-time rhythm → `02_DOMAIN_NARRATIVE_ENGINES/05__PACING_RHYTHM_ENG.md`
- Screen-time rhythm → `08_KNOWLEDGE_PRODUCTION_ENGINES/07__EDITING_MONTAGE_ENG.md`
- Production audio (sync/placement/clarity) → `08__SOUND_MUSIC_ENG.md`
- Deep music (composition/harmony/arrangement/vocal/mix-master) → `09_SOUND_MUSIC_ENGINES/*`

---

## 2) CANON ORDER (MANDATORY)
Engines in this family should be executed in strict order when building production artifacts:

01 — Visual Composition Engine  
02 — Art Style Engine  
03 — Camera & Cinematography Engine  
04 — Lighting Engine  
05 — Image Generation Engine  
06 — Video Generation Engine  
07 — Editing & Montage Engine  
08 — Sound & Music Engine (Production Layer)

Rule:
- Editing (07) consumes clip/shot outputs from 03/06; it does not own story-time pacing.
- Production sound (08) consumes EDL and builds layer plans/cue maps; it does not compose music.

---

## 3) TEMPLATES (MANDATORY)
ENGINE TEMPLATE:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/00__TEMPLATE__ENGINE__KNOWLEDGE_PRODUCTION_ENGINES.md

README TEMPLATE:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/00__TEMPLATE__README__KNOWLEDGE_PRODUCTION_ENGINES.md

---

## 4) CANON MAP (RAW-ONLY NAV)
01 — Visual Composition Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/01__VISUAL_COMPOSITION_ENG.md

02 — Art Style Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/02__ART_STYLE_ENG.md

03 — Camera & Cinematography Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/03__CAMERA_CINEMATOGRAPHY_ENG.md

04 — Lighting Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/04__LIGHTING_ENG.md

05 — Image Generation Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/05__IMAGE_GENERATION_ENG.md

06 — Video Generation Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/06__VIDEO_GENERATION_ENG.md

07 — Editing & Montage Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/07__EDITING_MONTAGE_ENG.md

08 — Sound & Music Engine (Production Layer)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/08__SOUND_MUSIC_ENG.md

---

## 5) OUTPUT TARGETS (DEFAULT)
Default storage (recommended):
- PROJECT_ARTIFACTS/<project>/PRODUCTION/VISUAL/COMPOSITION/
- PROJECT_ARTIFACTS/<project>/PRODUCTION/VISUAL/ART_STYLE/
- PROJECT_ARTIFACTS/<project>/PRODUCTION/VISUAL/CAMERA/
- PROJECT_ARTIFACTS/<project>/PRODUCTION/VISUAL/LIGHTING/
- PROJECT_ARTIFACTS/<project>/PRODUCTION/VISUAL/IMAGE_GEN/
- PROJECT_ARTIFACTS/<project>/PRODUCTION/VIDEO/VIDEO_GEN/
- PROJECT_ARTIFACTS/<project>/PRODUCTION/VIDEO/EDITING/
- PROJECT_ARTIFACTS/<project>/PRODUCTION/AUDIO/

---

## 6) USAGE PIPELINE (DETERMINISTIC)
1) Establish visual intent:
   - composition (01) → style (02) → camera (03) → lighting (04)
2) Generate specs:
   - image specs (05) and/or video specs (06)
3) Assemble screen-time:
   - editing/montage (07) produces EDL + rhythm + patterns
4) Place production audio:
   - production sound (08) produces layer plan + sync cue map + gates

Validation:
- Each engine emits a gates report. Any S0 fail = STOP.

---

## 7) HARD BOUNDARY NOTES (CRITICAL)
- Do not put “tone/mood” ownership into art style; tone/mood lives in 06 family.
- Do not put “story pacing” into editing; story pacing lives in narrative pacing engine.
- Do not compose music in production sound; compose in 09 family.

--- END.

LOCK: FIXED
