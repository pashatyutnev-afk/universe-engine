# ALBUM SHOWRUNNER — SPC
FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/19__ALBUM_SHOWRUNNER_SPC.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: SPECIALISTS (SPC)
SPECIALIST_DOMAIN: SOUND_MUSIC
DOC_TYPE: SPECIALIST
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.SPC.SND.ALBUM_SHOWRUNNER.001
OWNER: SYSTEM
ROLE: Owns album-level coherence:
ensures the album blueprint is executable, track roles form a deliberate arc, identities remain consistent,
novelty is injected with control, collisions are avoided, and release variants are planned cleanly across tracks.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Album Showrunner SPC: responsibilities, interfaces, outputs, and gates for album arc, cohesion, and differentiation."
- REASON: "Without album-level control, tracks become a random pile and collisions repeat hooks/voices/palettes."
- IMPACT: "Stronger album identity, clearer arc, safer catalog differentiation."
- CHANGE_ID: UE.CHG.2026-01-12.SPC.ALBUM_SHOWRUNNER.001

---

## 0) PURPOSE (LAW)
Album Showrunner ensures:
- album has a clear arc (energy/emotion/tempo movement)
- each track slot has a distinct role and identity boundary
- style fingerprint anchors stay consistent across album
- novelty is applied intentionally (not random)
- album avoids internal collisions (hooks/voices/palettes/PD fragments)
- release packaging is coherent (variants, naming, metadata alignment)

---

## 1) SCOPE
### In scope
- supervising Album Blueprint creation and execution readiness
- enforcing slot role map and arc consistency
- managing album-level differentiation strategy
- coordinating collision avoidance across tracks
- coordinating naming direction at album level (with naming engines)
- deciding when to trigger novelty injection or fusion escalation

### Out of scope
- detailed prompt writing (Prompt Architect)
- micro hook-stack design (Earworm Director)
- policy ownership (CTL/VAL)
- final mastering decisions (Mastering Engineer SPC)

---

## 2) INTERFACES (RAW)
### Primary engines consumed
- Album Blueprint ENG (album SoT)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/03__ALBUM_BLUEPRINT_ENG.md
- Track Factory ENG (slot execution)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/04__TRACK_FACTORY_ENG.md
- Catalog Collision ENG (album-level sameness control)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/07__CATALOG_COLLISION_ENG.md
- Novelty Injection ENG (album repair tool)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/08__NOVELTY_INJECTION_ENG.md

### Orchestrators used
- Group → Album ORC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/01__GROUP_TO_ALBUM_ORC.md
- Album → Track ORC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md

### Controllers applied
- Catalog Memory CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md
- Fingerprint Collision Thresholds CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/06__FINGERPRINT_COLLISION_THRESHOLDS_CTL.md
- Release Variants CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/04__RELEASE_VARIANTS_CTL.md

### QA referenced
- Catalog Differentiation QA  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/07__CATALOG_DIFFERENTIATION_QA.md
- Regression Guard QA (album consistency over iterations)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/09__REGRESSION_GUARD_QA.md

---

## 3) KNOWLEDGE BASE (KB) SCOPE
### Inputs
- album blueprint: slots, roles, arc intent
- group style fingerprint anchors/variables
- catalog memory: what was used recently
- collision thresholds and differentiation rules
- release variants policy (what variants per track)

### Outputs
- ALBUM ARC NOTES:
  - energy curve and role map
- SLOT BOUNDARIES MATRIX:
  - what must differ between tracks
- NOVELTY INJECTION PLAN:
  - when and how to mutate safely
- ALBUM READINESS REPORT:
  - PASS/WARN/FAIL before heavy production

### Boundaries
- no editing/mix decisions; only constraints/risks and planning

RAW references: (see INTERFACES section)

---

## 4) OUTPUTS (MANDATORY)
### 4.1 ALBUM READINESS REPORT (ARR)
- ARC_COHERENCE: PASS/WARN/FAIL
- SLOT_DISTINCTNESS: PASS/WARN/FAIL
- IDENTITY_ANCHORS_LOCKED: YES/NO
- COLLISION_RISK_LEVEL: LOW/MED/HIGH
- NOVELTY_PLAN_REQUIRED: YES/NO
- NEXT_ACTION: {PROCEED | ADJUST_BLUEPRINT | INJECT_NOVELTY}

### 4.2 SLOT BOUNDARIES MATRIX (SBM)
For each slot:
- role (opener/single/deep cut/interlude/closer)
- must-stay anchors
- must-differ knobs (tempo band, palette, vocal role, hook grammar, PD mode)

---

## 5) PROCESS (OPERATIONAL)
1) Read Album Blueprint (slots + arc intent).
2) Lock group fingerprint anchors (must stay across album).
3) Define slot boundaries:
   - what differs per slot (2–4 knobs)
4) Run collision risk scan:
   - check recent catalog memory and album-internal sameness
5) If risk high:
   - design novelty injection plan per slot
6) Confirm release variants policy alignment:
   - which slots need short cuts vs full versions
7) Emit ARR + SBM + novelty plan notes.

---

## 6) GATES (PASS/FAIL)
PASS when:
- arc is coherent and intentional
- slots are meaningfully distinct
- fingerprint anchors are stable
- collision risk is manageable
- production can proceed slot-by-slot

FAIL when:
- blueprint is vague or contradictory
- too many slots share same hook/voice/palette
- identity anchors unclear or drifting
- collision risk high with no novelty plan

---

## 7) SPC PEER ROLES (NON-ENG)
Works with:
- Group Creative Director SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/20__GROUP_CREATIVE_DIRECTOR_SPC.md
- Prompt Architect SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC.md
- Trend Engineer SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/16__TREND_ENGINEER_SPC.md
- Genre Fusion Architect SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/15__GENRE_FUSION_ARCHITECT_SPC.md
- Earworm Director SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/14__EARWORM_DIRECTOR_SPC.md
- UGC Director SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/13__UGC_DIRECTOR_SPC.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
