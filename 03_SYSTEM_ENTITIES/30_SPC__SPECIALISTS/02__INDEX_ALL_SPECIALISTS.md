# SPC SPECIALISTS INDEX — GLOBAL REGISTRY (CANON ROADMAP)
CANON FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02__INDEX_ALL_SPECIALISTS.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: SPECIALISTS (SPC)
DOC_TYPE: INDEX
INDEX_TYPE: GLOBAL_SPECIALIST_REGISTRY
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.2
UID: UE.SPC.IDX.ALL.001
OWNER: SYSTEM
ROLE: Canonical navigation law + existence registry for all SPC specialist families and instances (RAW-ONLY NAV)

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: PATCH
- SUMMARY: "Extended 06_SOUND_MUSIC family in SPC index: registered specialists 12..20 (prompt/UGC/earworm/genre-fusion/trends/PD-juice/mosaic/album showrunning/group creative direction). No new entities created."
- REASON: "Music system rollout requires canon-visible specialist roles for viral hook control, platform moments, and public-domain text pipeline."
- IMPACT: "SPC music family becomes complete for production pipeline; existence registry updated."
- CHANGE_ID: UE.CHG.2026-01-11.SPC.IDX.ALL.003

---

## ROOT FILES (SPC LAYER) — RAW ONLY
00 — SPC Layer Realm (README)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00__README__SPC_REALM.md

01 — SPC Layer Rules (Ruleset)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/01__RULES__SPC.md

02 — SPC INDEX_ALL_SPECIALISTS (THIS FILE)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02__INDEX_ALL_SPECIALISTS.md

03 — SPC Create Flow  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/03__CREATE_FLOW__SPC.md

---

## 0) PURPOSE (LAW)
Этот INDEX — единая точка истины для слоя `30_SPC__SPECIALISTS`.

Он фиксирует:
- состав папок (семейств) внутри `03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/`
- строгий порядок специалистов внутри каждого семейства
- единый стандарт нумерации/именования
- навигацию по прямым RAW ссылкам

---

## 1) EXISTENCE RULE (ABSOLUTE)
- Если файла/README/Template нет в CANON MAP ниже — он **не существует** для слоя SPC.
- Если файл есть в репо, но не зарегистрирован здесь — **NON-CANON / ignored**.
- NAV работает **только по RAW** (PATH — метка, не механизм навигации).

---

## 2) BASE PATH
PATH: `03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/`

---

## 3) HOW TO USE (ROADMAP)
1) Выбираешь FAMILY (папку) по задаче.
2) Открываешь `00__README__...` этой FAMILY — это рамки, роли и границы.
3) Внутри FAMILY идёшь по специалистам строго по номеру.
4) Новый специалист:
   - сначала регистрируется здесь (FAMILY + номер),
   - затем создаётся файл,
   - затем обновляется README семьи (если нужно).

---

## 4) FAMILY BLOCK STANDARD (MANDATORY)
Каждое семейство обязано иметь единый блок:
1) `## <FAMILY_NAME>`
2) `REALM FILE:` (RAW)
3) `Family Path:`
4) `TEMPLATES:` (если применимо)
5) список специалистов по номерам (RAW)

---

# CANON MAP — 30_SPC__SPECIALISTS (RAW-ONLY NAV)

---

## 00__TEMPLATES
REALM FILE:
- (Templates folder; realm is implied by templates themselves)

Family Path: `00__TEMPLATES/`

00 — TEMPLATE: README (SPC)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00__TEMPLATES/00__TEMPLATE__README__SPC.md

01 — TEMPLATE: SPC ENTITY  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00__TEMPLATES/00__TEMPLATE__SPC_ENTITY.md

02 — TEMPLATE: SPC OUTPUT PACK  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00__TEMPLATES/00__TEMPLATE__SPC_OUTPUT_PACK.md

---

## 00_TOP_GOVERNANCE
REALM FILE:
- 00 — README: TOP  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/00__README__TOP.md

Family Path: `00_TOP_GOVERNANCE/`

01 — MACHINE ARCHITECT  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/01__MACHINE_ARCHITECT_SPC.md

02 — GOVERNANCE OWNER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/02__GOVERNANCE_OWNER_SPC.md

03 — STANDARDS OWNER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/03__STANDARDS_OWNER_SPC.md

04 — DOC CONTROLLER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/04__DOC_CONTROLLER_SPC.md

05 — PIPELINE ARCHITECT  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/05__PIPELINE_ARCHITECT_SPC.md

06 — INTEGRATION PACKER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/06__INTEGRATION_PACKER_SPC.md

---

## 01_CREATIVE
REALM FILE:
- 00 — README: CREATIVE SPECIALISTS  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/01_CREATIVE/00__README_CREATIVE_SPECIALISTS.md

Family Path: `01_CREATIVE/`

01 — CREATIVE DIRECTOR  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/01_CREATIVE/01__CREATIVE_DIRECTOR_SPC.md

02 — VISUAL STYLE ARCHITECT  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/01_CREATIVE/02__VISUAL_STYLE_ARCHITECT_SPC.md

03 — WORLD AESTHETIC DESIGNER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/01_CREATIVE/03__WORLD_AESTHETIC_DESIGNER_SPC.md

04 — CONCEPT DESIGNER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/01_CREATIVE/04__CONCEPT_DESIGNER_SPC.md

05 — SYMBOLISM METAPHOR DESIGNER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/01_CREATIVE/05__SYMBOLISM_METAPHOR_DESIGNER_SPC.md

06 — MOOD ATMOSPHERE CURATOR  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/01_CREATIVE/06__MOOD_ATMOSPHERE_CURATOR_SPC.md

07 — ARTISTIC RISK DESIGNER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/01_CREATIVE/07__ARTISTIC_RISK_DESIGNER_SPC.md

08 — IDEA GENERATOR  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/01_CREATIVE/08__IDEA_GENERATOR_SPC.md

---

## 02_NARRATIVE
REALM FILE:
- 00 — README: NARRATIVE SPECIALISTS  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02_NARRATIVE/00__README_NARRATIVE_SPECIALISTS.md

Family Path: `02_NARRATIVE/`

01 — EPISODE SHOWRUNNER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02_NARRATIVE/01__EPISODE_SHOWRUNNER_SPC.md

02 — HEAD WRITER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02_NARRATIVE/02__HEAD_WRITER_SPC.md

03 — STORY ARCHITECT  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02_NARRATIVE/03__STORY_ARCHITECT_SPC.md

04 — DRAMATURG  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02_NARRATIVE/04__DRAMATURG_SPC.md

05 — SCREENWRITER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02_NARRATIVE/05__SCREENWRITER_SPC.md

06 — DIALOGUE WRITER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02_NARRATIVE/06__DIALOGUE_WRITER_SPC.md

07 — CLIFFHANGER SPECIALIST  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02_NARRATIVE/07__CLIFFHANGER_SPECIALIST_SPC.md

08 — EMOTIONAL ARC DESIGNER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02_NARRATIVE/08__EMOTIONAL_ARC_DESIGNER_SPC.md

09 — THEME MEANING CURATOR  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02_NARRATIVE/09__THEME_MEANING_CURATOR_SPC.md

10 — LORE MASTER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02_NARRATIVE/10__LORE_MASTER_SPC.md

11 — NOVELIST  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02_NARRATIVE/11__NOVELIST_SPC.md

---

## 03_CHARACTER
REALM FILE:
- 00 — README: CHARACTER SPECIALISTS  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/03_CHARACTER/00__README_CHARACTER_SPECIALISTS.md

Family Path: `03_CHARACTER/`

01 — CHARACTER ARCHITECT  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/03_CHARACTER/01__CHARACTER_ARCHITECT_SPC.md

02 — PERSONALITY PSYCHOLOGIST  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/03_CHARACTER/02__PERSONALITY_PSYCHOLOGIST_SPC.md

03 — TRAUMA MOTIVATION DESIGNER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/03_CHARACTER/03__TRAUMA_MOTIVATION_DESIGNER_SPC.md

04 — RELATIONSHIP DYNAMICS DESIGNER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/03_CHARACTER/04__RELATIONSHIP_DYNAMICS_DESIGNER_SPC.md

05 — DIALOGUE BEHAVIOR ANALYST  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/03_CHARACTER/05__DIALOGUE_BEHAVIOR_ANALYST_SPC.md

06 — CHARACTER EVOLUTION SUPERVISOR  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/03_CHARACTER/06__CHARACTER_EVOLUTION_SUPERVISOR_SPC.md

---

## 04_WORLD
REALM FILE:
- 00 — README: WORLD SPECIALISTS  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/04_WORLD/00__README_WORLD_SPECIALISTS.md

Family Path: `04_WORLD/`

01 — WORLD BUILDER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/04_WORLD/01__WORLD_BUILDER_SPC.md

02 — CULTURE SOCIETY ARCHITECT  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/04_WORLD/02__CULTURE_SOCIETY_ARCHITECT_SPC.md

03 — CIVILIZATION DESIGNER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/04_WORLD/03__CIVILIZATION_DESIGNER_SPC.md

04 — GEOGRAPHY LOCATION DESIGNER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/04_WORLD/04__GEOGRAPHY_LOCATION_DESIGNER_SPC.md

05 — ECONOMY POWER SYSTEMS DESIGNER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/04_WORLD/05__ECONOMY_POWER_SYSTEMS_DESIGNER_SPC.md

06 — RELIGION MYTHOLOGY DESIGNER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/04_WORLD/06__RELIGION_MYTHOLOGY_DESIGNER_SPC.md

07 — ECOLOGY SURVIVAL DESIGNER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/04_WORLD/07__ECOLOGY_SURVIVAL_DESIGNER_SPC.md

---

## 05_VISUAL
REALM FILE:
- 00 — README: VISUAL SPECIALISTS  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/05_VISUAL/00__README_VISUAL_SPECIALISTS.md

Family Path: `05_VISUAL/`

01 — VISUAL DIRECTOR  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/05_VISUAL/01__VISUAL_DIRECTOR_SPC.md

02 — PRODUCTION DESIGNER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/05_VISUAL/02__PRODUCTION_DESIGNER_SPC.md

03 — SCENE VISUALIZATION SPECIALIST  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/05_VISUAL/03__SCENE_VISUALIZATION_SPECIALIST_SPC.md

04 — STORYBOARD ARTIST  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/05_VISUAL/04__STORYBOARD_ARTIST_SPC.md

05 — CINEMATOGRAPHER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/05_VISUAL/05__CINEMATOGRAPHER_SPC.md

06 — CAMERA MOVEMENT SPECIALIST  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/05_VISUAL/06__CAMERA_MOVEMENT_SPECIALIST_SPC.md

---

## 06_SOUND_MUSIC
REALM FILE:
- 00 — README: SOUND MUSIC SPECIALISTS  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/00__README_SOUND_MUSIC_SPECIALISTS.md

Family Path: `06_SOUND_MUSIC/`

01 — MUSIC SUPERVISOR  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/01__MUSIC_SUPERVISOR_SPC.md

02 — MUSIC PRODUCER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/02__MUSIC_PRODUCER_SPC.md

03 — COMPOSER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/03__COMPOSER_SPC.md

04 — SONGWRITER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/04__SONGWRITER_SPC.md

05 — LYRICIST  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/05__LYRICIST_SPC.md

06 — ARRANGER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/06__ARRANGER_SPC.md

07 — VOCAL DIRECTOR  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC.md

08 — SOUND DESIGNER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/08__SOUND_DESIGNER_SPC.md

09 — MIX ENGINEER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/09__MIX_ENGINEER_SPC.md

10 — MASTERING ENGINEER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/10__MASTERING_ENGINEER_SPC.md

11 — AUDIO QA  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/11__AUDIO_QA_SPC.md

12 — PROMPT ARCHITECT  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC.md

13 — UGC DIRECTOR  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/13__UGC_DIRECTOR_SPC.md

14 — EARWORM DIRECTOR  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/14__EARWORM_DIRECTOR_SPC.md

15 — GENRE FUSION ARCHITECT  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/15__GENRE_FUSION_ARCHITECT_SPC.md

16 — TREND ENGINEER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/16__TREND_ENGINEER_SPC.md

17 — POET JUICE EDITOR  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/17__POET_JUICE_EDITOR_SPC.md

18 — MOSAIC EDITOR  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/18__MOSAIC_EDITOR_SPC.md

19 — ALBUM SHOWRUNNER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/19__ALBUM_SHOWRUNNER_SPC.md

20 — GROUP CREATIVE DIRECTOR  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/20__GROUP_CREATIVE_DIRECTOR_SPC.md

---

## 07_PRODUCTION
REALM FILE:
- 00 — README: PRODUCTION SPECIALISTS  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/07_PRODUCTION/00__README_PRODUCTION_SPECIALISTS.md

Family Path: `07_PRODUCTION/`

01 — EXECUTIVE PRODUCER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/07_PRODUCTION/01__EXECUTIVE_PRODUCER_SPC.md

02 — DIRECTOR  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/07_PRODUCTION/02__DIRECTOR_SPC.md

03 — CONTENT PRODUCER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/07_PRODUCTION/03__CONTENT_PRODUCER_SPC.md

04 — TRANSMEDIA PRODUCER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/07_PRODUCTION/04__TRANSMEDIA_PRODUCER_SPC.md

05 — EPISODE CHAPTER PLANNER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/07_PRODUCTION/05__EPISODE_CHAPTER_PLANNER_SPC.md

06 — PLATFORM ADAPTATION SPECIALIST  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/07_PRODUCTION/06__PLATFORM_ADAPTATION_SPECIALIST_SPC.md

07 — LOCALIZATION MANAGER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/07_PRODUCTION/07__LOCALIZATION_MANAGER_SPC.md

08 — RELEASE MANAGER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/07_PRODUCTION/08__RELEASE_MANAGER_SPC.md

09 — SCHEDULE COORDINATOR  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/07_PRODUCTION/09__SCHEDULE_COORDINATOR_SPC.md

---

## 08_PSYCHOLOGY
REALM FILE:
- 00 — README: PSYCHOLOGY SPECIALISTS  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/08_PSYCHOLOGY/00__README_PSYCHOLOGY_SPECIALISTS.md

Family Path: `08_PSYCHOLOGY/`

01 — VIEWER PSYCHOLOGY ANALYST  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/08_PSYCHOLOGY/01__VIEWER_PSYCHOLOGY_ANALYST_SPC.md

02 — EMPATHY IDENTIFICATION SPECIALIST  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/08_PSYCHOLOGY/02__EMPATHY_IDENTIFICATION_SPECIALIST_SPC.md

03 — EMOTIONAL IMPACT DESIGNER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/08_PSYCHOLOGY/03__EMOTIONAL_IMPACT_DESIGNER_SPC.md

04 — NONVERBAL BEHAVIOR ANALYST  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/08_PSYCHOLOGY/04__NONVERBAL_BEHAVIOR_ANALYST_SPC.md

05 — BEHAVIORAL CONSISTENCY SPECIALIST  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/08_PSYCHOLOGY/05__BEHAVIORAL_CONSISTENCY_SPECIALIST_SPC.md

---

## 09_RESEARCH
REALM FILE:
- 00 — README: RESEARCH SPECIALISTS  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/09_RESEARCH/00__README_RESEARCH_SPECIALISTS.md

Family Path: `09_RESEARCH/`

01 — RESEARCH DIRECTOR  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/09_RESEARCH/01__RESEARCH_DIRECTOR_SPC.md

02 — SCIENTIFIC RESEARCHER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/09_RESEARCH/02__SCIENTIFIC_RESEARCHER_SPC.md

03 — HISTORICAL RESEARCHER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/09_RESEARCH/03__HISTORICAL_RESEARCHER_SPC.md

04 — CULTURAL ANTHROPOLOGIST  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/09_RESEARCH/04__CULTURAL_ANTHROPOLOGIST_SPC.md

05 — KNOWLEDGE CURATOR  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/09_RESEARCH/05__KNOWLEDGE_CURATOR_SPC.md

06 — SOURCE VALIDATION SPECIALIST  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/09_RESEARCH/06__SOURCE_VALIDATION_SPECIALIST_SPC.md

07 — FACT CHECKING SPECIALIST  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/09_RESEARCH/07__FACT_CHECKING_SPECIALIST_SPC.md

08 — SPECULATIVE PLAUSIBILITY ANALYST  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/09_RESEARCH/08__SPECULATIVE_PLAUSIBILITY_ANALYST_SPC.md

---

## 10_MARKETING
REALM FILE:
- 00 — README: MARKETING SPECIALISTS  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/10_MARKETING/00__README_MARKETING_SPECIALISTS.md

Family Path: `10_MARKETING/`

01 — BRAND ARCHITECT  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/10_MARKETING/01__BRAND_ARCHITECT_SPC.md

02 — AUDIENCE ANALYST  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/10_MARKETING/02__AUDIENCE_ANALYST_SPC.md

03 — AUDIENCE RESEARCH SPECIALIST  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/10_MARKETING/03__AUDIENCE_RESEARCH_SPECIALIST_SPC.md

04 — CONTENT PACKAGING SPECIALIST  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/10_MARKETING/04__CONTENT_PACKAGING_SPECIALIST_SPC.md

05 — PLATFORM DISTRIBUTION SPECIALIST  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/10_MARKETING/05__PLATFORM_DISTRIBUTION_SPECIALIST_SPC.md

06 — SEO DISCOVERY SPECIALIST  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/10_MARKETING/06__SEO_DISCOVERY_SPECIALIST_SPC.md

07 — TRAILER TEASER SPECIALIST  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/10_MARKETING/07__TRAILER_TEASER_SPECIALIST_SPC.md

08 — COMMUNITY MANAGER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/10_MARKETING/08__COMMUNITY_MANAGER_SPC.md

09 — ENGAGEMENT STRATEGIST  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/10_MARKETING/09__ENGAGEMENT_STRATEGIST_SPC.md

10 — GROWTH HACKER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/10_MARKETING/10__GROWTH_HACKER_SPC.md

11 — MONETIZATION STRATEGIST  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/10_MARKETING/11__MONETIZATION_STRATEGIST_SPC.md

---

## 11_META
REALM FILE:
- 00 — README: META SPECIALISTS  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/11_META/00__README_META_SPECIALISTS.md

Family Path: `11_META/`

01 — UNIVERSE CURATOR  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/11_META/01__UNIVERSE_CURATOR_SPC.md

02 — SYSTEM ARCHITECT  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/11_META/02__SYSTEM_ARCHITECT_SPC.md

03 — RULE SYSTEM DESIGNER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/11_META/03__RULE_SYSTEM_DESIGNER_SPC.md

04 — DEPENDENCY SUPERVISOR  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/11_META/04__DEPENDENCY_SUPERVISOR_SPC.md

05 — KNOWLEDGE INTEGRATOR  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/11_META/05__KNOWLEDGE_INTEGRATOR_SPC.md

06 — META ANALYST  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/11_META/06__META_ANALYST_SPC.md

07 — LONG TERM STRATEGY PLANNER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/11_META/07__LONG_TERM_STRATEGY_PLANNER_SPC.md

08 — EVOLUTION SCALING PLANNER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/11_META/08__EVOLUTION_SCALING_PLANNER_SPC.md

---

## 99) ALIAS RULE (STRICT)
Любые дубли entrypoint/индекса вида:
- `03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00__INDEX_ALL_SPECIALISTS.md`
- любые другие `*INDEX*_SPECIALISTS*.md`, кроме CANON FILE выше
должны быть либо удалены, либо превращены в чистый POINTER на:
`03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02__INDEX_ALL_SPECIALISTS.md`

---

## FINAL RULE (LOCK)
Этот INDEX — единственная точка истины о составе и порядке SPC-специалистов.  
Любая правка структуры/порядка должна фиксироваться как изменение канона слоя SPC.

OWNER: SYSTEM  
LOCK: FIXED

--- END.
