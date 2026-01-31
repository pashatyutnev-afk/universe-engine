# GROUP CREATIVE DIRECTOR — SPC
FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/20__GROUP_CREATIVE_DIRECTOR_SPC.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: SPECIALISTS (SPC)
SPECIALIST_DOMAIN: SOUND_MUSIC
DOC_TYPE: SPECIALIST
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.SPC.SND.GROUP_CREATIVE_DIRECTOR.001
OWNER: SYSTEM
ROLE: Owns group-level creative direction and identity governance for music output:
locks the Group DNA intent, supervises style fingerprint coherence, approves fusion/trend decisions,
and ensures the group remains recognizable while scaling output across albums and releases.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Group Creative Director SPC: responsibilities, interfaces, outputs, and gates for group identity governance."
- REASON: "Without a top creative owner, groups drift, voices collapse into one, and catalog identity dissolves."
- IMPACT: "Stable group identity, controlled evolution, better differentiation and scalable production."
- CHANGE_ID: UE.CHG.2026-01-12.SPC.GROUP_CREATIVE_DIRECTOR.001

---

## 0) PURPOSE (LAW)
Group Creative Director ensures:
- the group’s identity promise is clear and stays consistent
- Style Fingerprint anchors remain locked across outputs
- trend/fusion choices do not break the group brand
- voice diversity is maintained (no “same vocalist everywhere” problem)
- releases feel like one catalog, not random generations

---

## 1) SCOPE
### In scope
- group identity governance (Group DNA intent + boundaries)
- approval of style fingerprint anchors/variables
- approval of fusion level (A/B/C) and evolution phases
- high-level hook/UGC direction alignment to group identity
- escalation decisions: when to run novelty injection vs keep stable
- cross-album cohesion and differentiation strategy

### Out of scope
- writing prompts line-by-line (Prompt Architect)
- designing hook stack details (Earworm Director)
- policy ownership and thresholds (CTL/VAL)
- final mix/master engineering (Mix/Master/QA roles)

---

## 2) INTERFACES (RAW)
### Primary engines consumed / governed
- Group Foundation ENG (Group DNA SoT)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/01__GROUP_FOUNDATION_ENG.md
- Artist Factory ENG (cast/voice roles)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/02__ARTIST_FACTORY_ENG.md
- Style Fingerprint ENG (identity anchors)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/03__STYLE_FINGERPRINT_ENG.md
- Album Blueprint ENG (album arc plan)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/03__ALBUM_BLUEPRINT_ENG.md
- Track Factory ENG (execution)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/04__TRACK_FACTORY_ENG.md
- Fusion Recipe ENG (controlled evolution)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/02__FUSION_RECIPE_ENG.md
- Catalog Collision ENG (sameness detection)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/07__CATALOG_COLLISION_ENG.md
- Novelty Injection ENG (controlled mutation)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/08__NOVELTY_INJECTION_ENG.md

### Orchestrators it leads / approves
- Group → Album ORC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/01__GROUP_TO_ALBUM_ORC.md
- Album → Track ORC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md
- Track TEST → DOC Gate ORC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/03__TRACK_TEST_DOC_GATE_ORC.md

### Controllers referenced (constraints)
- Catalog Memory CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md
- Fingerprint Collision Thresholds CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/06__FINGERPRINT_COLLISION_THRESHOLDS_CTL.md
- Release Variants CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/04__RELEASE_VARIANTS_CTL.md

### Validators / QA referenced
- Voice Diversity VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/10__VOICE_DIVERSITY_VAL.md
- Collision Blocker VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/05__COLLISION_BLOCKER_VAL.md
- Catalog Differentiation QA  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/07__CATALOG_DIFFERENTIATION_QA.md

---

## 3) KNOWLEDGE BASE (KB) SCOPE
### Inputs
- Group concept + identity promise
- audience segment target
- style fingerprint anchors/variables/forbiddens
- catalog memory (what was already done)
- collision risk signals and thresholds
- release goals (UGC-first vs album-first)

### Outputs
- GROUP IDENTITY DECISION LOG (high-level approvals)
- EVOLUTION PLAN (stable vs light novelty vs heavy novelty)
- SLOT BOUNDARIES (what must differ across tracks)
- APPROVAL NOTES for:
  - fusion level
  - trend direction
  - cast/vocal distribution

### Boundaries
- No policy invention: CTL is the source of rule thresholds.
- No micro-editing: this role approves/blocks and sets constraints.

RAW references: (see INTERFACES section)

---

## 4) OUTPUTS (MANDATORY)
### 4.1 GROUP IDENTITY APPROVAL NOTE (GIAN)
- GROUP_UID:
- DATE:
- IDENTITY_PROMISE (1–2 lines):
- CORE_ANCHORS_LOCKED:
- ALLOWED_VARIATION_BUDGET:
- FORBIDDENS (short):
- EVOLUTION_MODE: {STABLE | LIGHT_NOVELTY | HEAVY_NOVELTY}
- APPROVED_FUSION_LEVEL: {NONE | A/B | A/B/C}
- VOICE_DISTRIBUTION_RULE (high-level):
- NEXT_ACTION:

### 4.2 EVOLUTION PLAN (EP)
- PHASE:
- TRIGGERS (when to evolve):
- SAFE_KNOBS:
- DO_NOT_TOUCH_ANCHORS:

---

## 5) PROCESS (OPERATIONAL)
1) Lock Group DNA (what the group is and is not).
2) Approve Style Fingerprint anchors (2–5 core anchors).
3) Approve cast distribution intent:
   - ensure voice diversity and role separation
4) Approve trend direction:
   - must fit audience, but cannot break anchors
5) Approve fusion level:
   - default conservative; escalate only when novelty needed
6) Monitor catalog signals:
   - if collisions rising → trigger Novelty Injection plan
7) Sign off on album blueprint readiness and slot boundaries.
8) For PASS candidates:
   - approve what becomes “canon sound” for the group.

---

## 6) GATES (PASS/FAIL)
PASS when:
- identity promise is explicit and stable
- anchors are locked and reusable
- voice diversity risk is managed
- evolution plan exists (even if STABLE)
- collisions are monitored and have a response plan

FAIL when:
- group identity is vague or contradictory
- anchors missing or constantly changing
- cast collapses into same voice pattern
- trend/fusion overrides identity
- collision warnings ignored

---

## 7) SPC PEER ROLES (NON-ENG)
Leads / coordinates:
- Album Showrunner SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/19__ALBUM_SHOWRUNNER_SPC.md
- Trend Engineer SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/16__TREND_ENGINEER_SPC.md
- Genre Fusion Architect SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/15__GENRE_FUSION_ARCHITECT_SPC.md
- Earworm Director SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/14__EARWORM_DIRECTOR_SPC.md
- UGC Director SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/13__UGC_DIRECTOR_SPC.md
- Prompt Architect SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
