# MAP — ORC → SPC (CANON)
FILE: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/02__MAP__ORC_to_SPC.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: CROSSREF (XREF)
DOC_TYPE: MAP
MAP_TYPE: ORC_TO_SPC
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.XREF.MAP.ORC_SPC.001
OWNER: SYSTEM
ROLE: Canonical dependency map: which ORCHESTRATORS (ORC) are allowed/expected to call which SPECIALISTS (SPC).
RAW-only navigation. No guessing links.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created ORC→SPC canonical map with initial coverage: CORE_ORCHESTRATORS + MUSIC_ORCHESTRATORS (+ SOUND_MUSIC SPC set)."
- REASON: "Deterministic orchestration requires explicit specialist involvement; prevents random role mixing."
- IMPACT: "Cleaner pipelines, consistent responsibilities, and audit-friendly role usage."
- CHANGE_ID: UE.CHG.2026-01-12.XREF.MAP.ORC_SPC.001

---

## 0) PURPOSE (LAW)
This MAP defines canonical links:
- ORC → uses/requests SPC (dependency set)
- It does NOT define engine calls (that is ENG→ORC MAP).
- It does NOT define sequence (that is PIPELINES MAP).

---

## 1) FORMAT (MANDATORY)
Each CANON RECORD:

RECORD:
- ORC_RAW:
- ORC_ROLE:
- USES_SPC (RAW list):
- NOTES (optional)

RULE:
- If an ORC uses an SPC not listed here → NON-CANON until registered.

---

# 2) CANON RECORDS — ORC → SPC

## 2.1 CORE ORCHESTRATORS (general universe work)

### ORC: Narrative Orchestrator
- ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/01_CORE_ORCHESTRATORS/01__NARRATIVE_ORCHESTRATOR_ENG.md
- ORC_ROLE: Coordinates narrative outputs and requests narrative specialists when producing story assets.
- USES_SPC:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02_NARRATIVE/03__STORY_ARCHITECT_SPC.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02_NARRATIVE/04__DRAMATURG_SPC.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02_NARRATIVE/05__SCREENWRITER_SPC.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02_NARRATIVE/06__DIALOGUE_WRITER_SPC.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02_NARRATIVE/10__LORE_MASTER_SPC.md

### ORC: Character Orchestrator
- ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/01_CORE_ORCHESTRATORS/02__CHARACTER_ORCHESTRATOR_ENG.md
- ORC_ROLE: Coordinates character outputs and requests character specialists for profiles, arcs, dialogue behavior.
- USES_SPC:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/03_CHARACTER/01__CHARACTER_ARCHITECT_SPC.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/03_CHARACTER/02__PERSONALITY_PSYCHOLOGIST_SPC.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/03_CHARACTER/04__RELATIONSHIP_DYNAMICS_DESIGNER_SPC.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/03_CHARACTER/05__DIALOGUE_BEHAVIOR_ANALYST_SPC.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/03_CHARACTER/06__CHARACTER_EVOLUTION_SUPERVISOR_SPC.md

### ORC: World Orchestrator
- ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/01_CORE_ORCHESTRATORS/03__WORLD_ORCHESTRATOR_ENG.md
- ORC_ROLE: Coordinates worldbuilding outputs and requests world specialists for culture, geo, ecology, systems.
- USES_SPC:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/04_WORLD/01__WORLD_BUILDER_SPC.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/04_WORLD/02__CULTURE_SOCIETY_ARCHITECT_SPC.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/04_WORLD/04__GEOGRAPHY_LOCATION_DESIGNER_SPC.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/04_WORLD/07__ECOLOGY_SURVIVAL_DESIGNER_SPC.md

### ORC: Production Orchestrator
- ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/01_CORE_ORCHESTRATORS/04__PRODUCTION_ORCHESTRATOR_ENG.md
- ORC_ROLE: Coordinates production outputs and requests production specialists for format + packaging.
- USES_SPC:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/07_PRODUCTION/01__EXECUTIVE_PRODUCER_SPC.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/07_PRODUCTION/03__CONTENT_PRODUCER_SPC.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/07_PRODUCTION/08__RELEASE_MANAGER_SPC.md

### ORC: Pipeline Orchestrator
- ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/01_CORE_ORCHESTRATORS/05__PIPELINE_ORCHESTRATOR_ENG.md
- ORC_ROLE: Runs multi-step pipelines and requests top governance/packaging specialists as needed.
- USES_SPC:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/05__PIPELINE_ARCHITECT_SPC.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/06__INTEGRATION_PACKER_SPC.md

---

## 2.2 MUSIC ORCHESTRATORS (music factory)

### ORC: Group → Album
- ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/01__GROUP_TO_ALBUM_ORC.md
- ORC_ROLE: Builds Album Blueprint from Group DNA; requests group-level direction and roster planning.
- USES_SPC:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/19__ALBUM_SHOWRUNNER_SPC.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/20__GROUP_CREATIVE_DIRECTOR_SPC.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/02__MUSIC_PRODUCER_SPC.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC.md

### ORC: Album → Track
- ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md
- ORC_ROLE: Converts album slot to track plan + prompt packs; requests prompt/hook/trend/fusion specialists.
- USES_SPC:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/14__EARWORM_DIRECTOR_SPC.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/13__UGC_DIRECTOR_SPC.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/15__GENRE_FUSION_ARCHITECT_SPC.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/16__TREND_ENGINEER_SPC.md

### ORC: Track TEST → DOC Gate
- ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/03__TRACK_TEST_DOC_GATE_ORC.md
- ORC_ROLE: Runs QA/VAL checks and selects winners; requests QA specialists only as check definitions (not as content authors).
- USES_SPC:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/04__DOC_CONTROLLER_SPC.md

### ORC: Release Pack
- ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/04__RELEASE_PACK_ORC.md
- ORC_ROLE: Packages variants + metadata + titles; requests metadata/packaging support.
- USES_SPC:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/07_PRODUCTION/08__RELEASE_MANAGER_SPC.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/10_MARKETING/04__CONTENT_PACKAGING_SPECIALIST_SPC.md

### ORC: Portfolio Planner
- ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/05__PORTFOLIO_PLANNER_ORC.md
- ORC_ROLE: Plans coverage and novelty injection; requests trend and differentiation specialists.
- USES_SPC:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/16__TREND_ENGINEER_SPC.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/15__GENRE_FUSION_ARCHITECT_SPC.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/20__GROUP_CREATIVE_DIRECTOR_SPC.md

### ORC: Poet Pack (PD pipeline)
- ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/06__POET_PACK_ORC.md
- ORC_ROLE: Runs PD corpus fit→juice→mosaic; requests PD specialists.
- USES_SPC:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/17__POET_JUICE_EDITOR_SPC.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/18__MOSAIC_EDITOR_SPC.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
