# ENG ENGINES INDEX
00__INDEX_ALL_ENGINES.md

SCOPE: Universe Engine  
ENTITY_GROUP: ENGINES (ENG)  
INDEX_TYPE: GLOBAL_ENGINE_REGISTRY  
LEVEL: L1  
STATUS: ACTIVE  
VERSION: 2.0  
ROLE: Canonical navigation point for all ENG engine families and instances

---

## PURPOSE

Этот INDEX является **единым навигационным законом** для всех **ENG-движков** Universe Engine.

Он фиксирует:
- список семейств (папок) внутри `01_SYSTEM_ENTITIES/00_ENG__ENGINES/`
- порядок движков внутри каждого семейства
- обязательную нумерацию движков

Правило:
> Если движка нет в этом INDEX —  
> он не существует для ENG слоя системы.

---

## SCOPE NOTE (IMPORTANT)

Этот INDEX описывает **только ENG-движки**.

Другие классы сущностей (ORC / SPC / CTL / VAL / QA) имеют свои реестры
в соответствующих корневых папках:
- `01_ORC__ORCHESTRATORS/`
- `02_SPC__SPECIALISTS/`
- `03_CTL__CONTROLLERS/`
- `04_VAL__VALIDATORS/`
- `05_QA__QUALITY/`

---

## NUMBERING RULE (ENGINES)

- Нумерация обязательна для всех Engine-файлов.
- Формат имени файла движка: `NN__<ENGINE_NAME>_ENG.md`
- `NN` начинается с `01` внутри каждого семейства.
- Номер в INDEX и номер в имени файла **обязаны совпадать**.
- README не является движком и всегда имеет номер `00`.

---

# ENGINE MAP (ENG)

---

## 01_CORE_ENGINES  
**CLASS:** CORE (L1)  
🔗 **REALM FILE:** https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/01_CORE_ENGINES/00__README__CORE_ENGINES.md  
**Family Path:** `01_CORE_ENGINES/`

01 — Core Identity Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/01_CORE_ENGINES/01__CORE_IDENTITY_ENG.md  
02 — Core State Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/01_CORE_ENGINES/02__CORE_STATE_ENG.md  
03 — Core Lifecycle Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/01_CORE_ENGINES/03__CORE_LIFECYCLE_ENG.md  

---

## 02_DOMAIN_NARRATIVE_ENGINES  
**CLASS:** DOMAIN (L2)  
🔗 **REALM FILE:** https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/00__README__DOMAIN_NARRATIVE_ENGINES.md  
**Family Path:** `02_DOMAIN_NARRATIVE_ENGINES/`

01 — Narrative Logic Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/01__NARRATIVE_LOGIC_ENG.md  
02 — Story Structure Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/02__STORY_STRUCTURE_ENG.md  
03 — Dramatic Arc Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/03__DRAMATIC_ARC_ENG.md  
04 — Scene Construction Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/04__SCENE_CONSTRUCTION_ENG.md  
05 — Pacing & Rhythm Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/05__PACING_RHYTHM_ENG.md  
06 — Tension & Stakes Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/06__TENSION_STAKES_ENG.md  
07 — Foreshadowing Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/07__FORESHADOWING_ENG.md  
08 — Twist & Reveal Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/08__TWIST_REVEAL_ENG.md  
09 — Narrative Continuity Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/09__NARRATIVE_CONTINUITY_ENG.md  
10 — Theme & Meaning Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/10__THEME_MEANING_ENG.md  

---

## 03_DOMAIN_CHARACTER_ENGINES  
**CLASS:** DOMAIN (L2)  
🔗 **REALM FILE:** https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/00__README__DOMAIN_CHARACTER_ENGINES.md  
**Family Path:** `03_DOMAIN_CHARACTER_ENGINES/`

01 — Character Core Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/01__CHARACTER_CORE_ENG.md  
02 — Motivation & Desire Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/02__MOTIVATION_DESIRE_ENG.md  
03 — Moral & Value Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/03__MORAL_VALUE_ENG.md  
04 — Character Psychology Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/04__CHARACTER_PSYCHOLOGY_ENG.md  
05 — Character Behavior Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/05__CHARACTER_BEHAVIOR_ENG.md  
06 — Relationship Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/06__RELATIONSHIP_ENG.md  
07 — Dialogue Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/07__DIALOGUE_ENG.md  
08 — Speech Naturalization Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/08__SPEECH_NATURALIZATION_ENG.md  
09 — Growth & Trauma Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/09__GROWTH_TRAUMA_ENG.md  
10 — Character Evolution Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/10__CHARACTER_EVOLUTION_ENG.md  

---

## 04_DOMAIN_WORLD_ENGINES  
**CLASS:** DOMAIN (L2)  
🔗 **REALM FILE:** https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/00__README__DOMAIN_WORLD_ENGINES.md  
**Family Path:** `04_DOMAIN_WORLD_ENGINES/`

01 — World Structure Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/01__WORLD_STRUCTURE_ENG.md  
02 — World Law Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/02__WORLD_LAW_ENG.md  
03 — Timeline & Epoch Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/03__TIMELINE_EPOCH_ENG.md  
04 — Civilization Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/04__CIVILIZATION_ENG.md  
05 — Conflict & Power Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/05__CONFLICT_POWER_ENG.md  
06 — Geopolitics Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/06__GEOPOLITICS_ENG.md  
07 — Economy & Resource Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/07__ECONOMY_RESOURCE_ENG.md  
08 — Technology & Magic Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/08__TECHNOLOGY_MAGIC_ENG.md  
09 — Mythology & Belief Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/09__MYTHOLOGY_BELIEF_ENG.md  
10 — Environment & Ecology Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/10__ENVIRONMENT_ECOLOGY_ENG.md  

---

## 06_EXPRESSION_ENGINES  
**CLASS:** EXPRESSION (L3)  
🔗 **REALM FILE:** https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/06_EXPRESSION_ENGINES/00__README__EXPRESSION_ENGINES.md  
**Family Path:** `06_EXPRESSION_ENGINES/`

01 — Event Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/06_EXPRESSION_ENGINES/01__EVENT_ENG.md  
02 — Cause–Effect Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/06_EXPRESSION_ENGINES/02__CAUSE_EFFECT_ENG.md  
03 — Conflict Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/06_EXPRESSION_ENGINES/03__CONFLICT_ENG.md  
04 — Turning Point Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/06_EXPRESSION_ENGINES/04__TURNING_POINT_ENG.md  
05 — Climax Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/06_EXPRESSION_ENGINES/05__CLIMAX_ENG.md  
06 — Resolution Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/06_EXPRESSION_ENGINES/06__RESOLUTION_ENG.md  
07 — System Shock Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/06_EXPRESSION_ENGINES/07__SYSTEM_SHOCK_ENG.md  
08 — Event Scheduling Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/06_EXPRESSION_ENGINES/08__EVENT_SCHEDULING_ENG.md  
09 — Randomness & Chaos Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/06_EXPRESSION_ENGINES/09__RANDOMNESS_CHAOS_ENG.md  

---

## 07_GENRE_STYLE_ENGINES  
**CLASS:** STYLE (L3)  
🔗 **REALM FILE:** https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/07_GENRE_STYLE_ENGINES/00__README__GENRE_STYLE_ENGINES.md  
**Family Path:** `07_GENRE_STYLE_ENGINES/`

01 — Tone & Mood Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/07_GENRE_STYLE_ENGINES/01__TONE_MOOD_ENG.md  
02 — Atmosphere Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/07_GENRE_STYLE_ENGINES/02__ATMOSPHERE_ENG.md  
03 — Emotional Resonance Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/07_GENRE_STYLE_ENGINES/03__EMOTIONAL_RESONANCE_ENG.md  
04 — Symbolism Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/07_GENRE_STYLE_ENGINES/04__SYMBOLISM_ENG.md  
05 — Metaphor Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/07_GENRE_STYLE_ENGINES/05__METAPHOR_ENG.md  
06 — Sensory Detail Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/07_GENRE_STYLE_ENGINES/06__SENSORY_DETAIL_ENG.md  

---

## 08_PRODUCTION_FORMAT_ENGINES  
**CLASS:** PRODUCTION (L3)  
🔗 **REALM FILE:** https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/08_PRODUCTION_FORMAT_ENGINES/00__README__PRODUCTION_FORMAT_ENGINES.md  
**Family Path:** `08_PRODUCTION_FORMAT_ENGINES/`

01 — Genre Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/08_PRODUCTION_FORMAT_ENGINES/01__GENRE_ENG.md  
02 — Genre Blending Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/08_PRODUCTION_FORMAT_ENGINES/02__GENRE_BLENDING_ENG.md  
03 — Format Adaptation Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/08_PRODUCTION_FORMAT_ENGINES/03__FORMAT_ADAPTATION_ENG.md  
04 — Book Format Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/08_PRODUCTION_FORMAT_ENGINES/04__BOOK_FORMAT_ENG.md  
05 — Series & Episode Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/08_PRODUCTION_FORMAT_ENGINES/05__SERIES_EPISODE_ENG.md  
06 — Short Content Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/08_PRODUCTION_FORMAT_ENGINES/06__SHORT_CONTENT_ENG.md  
07 — YouTube Longform Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/08_PRODUCTION_FORMAT_ENGINES/07__YOUTUBE_LONGFORM_ENG.md  
08 — Game Narrative Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/08_PRODUCTION_FORMAT_ENGINES/08__GAME_NARRATIVE_ENG.md  

---

## 09_KNOWLEDGE_PRODUCTION_ENGINES  
**CLASS:** PRODUCTION (L3)  
🔗 **REALM FILE:** https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/09_KNOWLEDGE_PRODUCTION_ENGINES/00__README__KNOWLEDGE_PRODUCTION_ENGINES.md  
**Family Path:** `09_KNOWLEDGE_PRODUCTION_ENGINES/`

01 — Visual Composition Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/09_KNOWLEDGE_PRODUCTION_ENGINES/01__VISUAL_COMPOSITION_ENG.md  
02 — Art Style Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/09_KNOWLEDGE_PRODUCTION_ENGINES/02__ART_STYLE_ENG.md  
03 — Camera & Cinematography Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/09_KNOWLEDGE_PRODUCTION_ENGINES/03__CAMERA_CINEMATOGRAPHY_ENG.md  
04 — Lighting Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/09_KNOWLEDGE_PRODUCTION_ENGINES/04__LIGHTING_ENG.md  
05 — Image Generation Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/09_KNOWLEDGE_PRODUCTION_ENGINES/05__IMAGE_GENERATION_ENG.md  
06 — Video Generation Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/09_KNOWLEDGE_PRODUCTION_ENGINES/06__VIDEO_GENERATION_ENG.md  
07 — Editing & Montage Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/09_KNOWLEDGE_PRODUCTION_ENGINES/07__EDITING_MONTAGE_ENG.md  
08 — Sound & Music Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/09_KNOWLEDGE_PRODUCTION_ENGINES/08__SOUND_MUSIC_ENG.md  

---

## 10_SOUND_MUSIC_ENGINES  
**CLASS:** PRODUCTION (L3)  
🔗 **REALM FILE:** https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/10_SOUND_MUSIC_ENGINES/00__README__SOUND_MUSIC_ENGINES.md  
**Family Path:** `10_SOUND_MUSIC_ENGINES/`

01 — Music Composition Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/10_SOUND_MUSIC_ENGINES/01__MUSIC_COMPOSITION_ENG.md  
02 — Song Structure Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/10_SOUND_MUSIC_ENGINES/02__SONG_STRUCTURE_ENG.md  
03 — Harmony & Chord Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/10_SOUND_MUSIC_ENGINES/03__HARMONY_CHORD_ENG.md  
04 — Melody Hook Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/10_SOUND_MUSIC_ENGINES/04__MELODY_HOOK_ENG.md  
05 — Rhythm & Groove Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/10_SOUND_MUSIC_ENGINES/05__RHYTHM_GROOVE_ENG.md  
06 — Rhyme & Meter Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/10_SOUND_MUSIC_ENGINES/06__RHYME_METER_ENG.md  
07 — Lyrics Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/10_SOUND_MUSIC_ENGINES/07__LYRICS_ENG.md  
08 — Arrangement & Instrumentation Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/10_SOUND_MUSIC_ENGINES/08__ARRANGEMENT_INSTRUMENTATION_ENG.md  
09 — Vocal Performance Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/10_SOUND_MUSIC_ENGINES/09__VOCAL_PERFORMANCE_ENG.md  
10 — Sound Design Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/10_SOUND_MUSIC_ENGINES/10__SOUND_DESIGN_ENG.md  
11 — Music Style Consistency Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/10_SOUND_MUSIC_ENGINES/11__MUSIC_STYLE_CONSISTENCY_ENG.md  
12 — Music to Scene Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/10_SOUND_MUSIC_ENGINES/12__MUSIC_TO_SCENE_ENG.md  
13 — Mix & Master Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/10_SOUND_MUSIC_ENGINES/13__MIX_MASTER_ENG.md  

---

## 11_META_EVOLUTION_ENGINES  
**CLASS:** META (L4)  
🔗 **REALM FILE:** https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/11_META_EVOLUTION_ENGINES/00__README__META_EVOLUTION_ENGINES.md  
**Family Path:** `11_META_EVOLUTION_ENGINES/`

01 — Learning Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/11_META_EVOLUTION_ENGINES/01__LEARNING_ENG.md  
02 — Pattern Extraction Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/11_META_EVOLUTION_ENGINES/02__PATTERN_EXTRACTION_ENG.md  
03 — Optimization Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/11_META_EVOLUTION_ENGINES/03__OPTIMIZATION_ENG.md  
04 — Creative Mutation Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/11_META_EVOLUTION_ENGINES/04__CREATIVE_MUTATION_ENG.md  
05 — Future Projection Engine — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_ENTITIES/00_ENG__ENGINES/11_META_EVOLUTION_ENGINES/05__FUTURE_PROJECTION_ENG.md  

---

## FINAL RULE

> Этот INDEX — единственная точка истины  
> о составе и порядке ENG-движков системы.

OWNER: Universe Engine  
STATUS: FIXED
