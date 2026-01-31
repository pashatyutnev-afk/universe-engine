# EARWORM DIRECTOR — SPC
FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/14__EARWORM_DIRECTOR_SPC.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: SPECIALISTS (SPC)
SPECIALIST_DOMAIN: SOUND_MUSIC
DOC_TYPE: SPECIALIST
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.SPC.SND.EARWORM_DIRECTOR.001
OWNER: SYSTEM
ROLE: Owns “earworm” mechanics and hook memory design:
ensures every track has a strong multi-layer hook stack (H1/H2/microhooks/S-tag/Q-line),
repeat-safe variation, early recognition, and collision-aware novelty.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Earworm Director SPC: responsibilities, interfaces, outputs, and gates for hook-stack quality and repeat-safe earworm behavior."
- REASON: "Main failure mode: hooks are weak, late, over-repeated, or identical across catalog."
- IMPACT: "Higher recognition, more replays, better UGC quoteability, safer scaling."
- CHANGE_ID: UE.CHG.2026-01-12.SPC.EARWORM_DIRECTOR.001

---

## 0) PURPOSE (LAW)
Earworm Director ensures:
- H1 is memorable and arrives early
- H2 supports and refreshes attention (without stealing identity)
- microhooks add dopamine without spam
- S-tag stamps identity early and near loop-out
- repeats are “same but evolved” (repeat-safe)
- hooks avoid catalog collisions and cliché patterns

---

## 1) SCOPE
### In scope
- hook-stack design (H1/H2/microhooks/S-tag/Q-line)
- hook timing intent (early recognition)
- repetition geometry + variation knobs for repeats
- anti-repeat and anti-cliché guardrails (precheck before VAL/QA)
- hook uniqueness planning (collision-aware)

### Out of scope
- full lyrics writing (Lyricist / Poet editors)
- arrangement/melody composition decisions (Composer/Arranger)
- mix/master decisions (Mix/Master SPC)
- policy ownership and thresholds (CTL/VAL own rules; SPC applies)

---

## 2) INTERFACES (RAW)
### Primary engines consumed
- Earworm Hook Stack ENG (core hook system)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/06__EARWORM_HOOK_STACK_ENG.md
- Viral Hook Blueprint ENG (timing + geometry)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/04__VIRAL_HOOK_BLUEPRINT_ENG.md
- UGC Moment Map ENG (clip windows alignment)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/05__UGC_MOMENT_MAP_ENG.md
- Catalog Collision ENG (catalog sameness control)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/07__CATALOG_COLLISION_ENG.md
- Novelty Injection ENG (repair after WARN/BLOCK)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/08__NOVELTY_INJECTION_ENG.md

### Controllers applied
- UGC Viral Ruleset CTL (hook behavior constraints)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/02__UGC_VIRAL_RULESET_CTL.md
- Duration Policy CTL (hook timing windows)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/03__DURATION_POLICY_CTL.md
- Fingerprint Collision Thresholds CTL (collision strictness)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/06__FINGERPRINT_COLLISION_THRESHOLDS_CTL.md
- Catalog Memory CTL (what already exists)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md

### Validators / QA gates referenced
- Repeat Guard VAL (no spam repeats)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/03__REPEAT_GUARD_VAL.md
- Hook Timing VAL (hook window compliance)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/01__HOOK_TIMING_VAL.md
- Collision Blocker VAL (near-duplicate hooks)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/05__COLLISION_BLOCKER_VAL.md
- Recognition 10s QA (recognition early)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/03__RECOGNITION_10S_QA.md

---

## 3) KNOWLEDGE BASE (KB) SCOPE
### Inputs
- track intent (role + mood + audience)
- hook timing windows and UGC needs
- catalog memory (avoid reusing hook grammar and slogans)
- collision thresholds and repeat guard rules

### Outputs
- Hook Stack Spec (H1/H2/microhooks/S-tag/Q-line)
- Repetition Geometry + Variation Plan (repeat-safe)
- Hook Uniqueness Notes (what to avoid next)
- Repair Plan (when WARN/BLOCK: which knob to mutate)

### Boundaries
- No policy invention; apply CTL.
- No full “music writing”; only hook system design + constraints.

RAW references: (see INTERFACES section)

---

## 4) OUTPUTS (MANDATORY)
### 4.1 HOOK STACK SPEC
- H1: (type + core phrase/motif + execution note)
- H2: (support/contrast + execution note)
- MICROHOOKS: (list, 1–4 max, each with purpose)
- S_TAG: (signature hit/tag + placement intent)
- Q_LINE (lyrical only): (short caption line + placement intent)

### 4.2 REPEAT-SAFE PLAN
- REPETITION_GEOMETRY: (A/A’/B/A etc.)
- VARIATION_KNOBS: (1–3 knobs used per return)
- ANTI_SPAM RULES: (what is forbidden)

### 4.3 UNIQUENESS NOTES
- AVOID_TOKENS: (hook words / chant tags / contour tokens)
- NEAREST_NEIGHBOR_ALERTS: (if catalog memory flags similarity)

---

## 5) PROCESS (OPERATIONAL)
1) Load catalog memory + collision thresholds (scope: group default).
2) Design H1 for instant recognition:
   - short, pronounceable, rhythmically clear (or motif clear if instrumental)
3) Design H2 as “refresh” without identity flip.
4) Add microhooks sparingly (dopamine sprinkles).
5) Place S-tag early + near loop-out.
6) Define repetition geometry + 1–3 variation knobs for each return.
7) Precheck against repeat/collision risks:
   - remove chant spam
   - prevent identical hook reuse
8) If WARN/BLOCK:
   - output a minimal repair plan (hook grammar / intro stamp / rhythm accents).

---

## 6) GATES (PASS/FAIL)
PASS when:
- H1 is clear and early (timing intent meets policy)
- repeats are variation-based (no copy-paste spam)
- microhooks do not clutter or annoy
- S-tag stamps identity early and supports loop imprint
- collision risk is low or handled by a minimal mutation plan

FAIL when:
- hook is late or unclear
- repeated words/phrases spam dominates
- hooks are too similar to existing catalog
- no distinct identity stamp (S-tag missing)
- variation plan absent

---

## 7) SPC PEER ROLES (NON-ENG)
Works with:
- Prompt Architect SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC.md
- UGC Director SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/13__UGC_DIRECTOR_SPC.md
- Genre Fusion Architect SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/15__GENRE_FUSION_ARCHITECT_SPC.md
- Trend Engineer SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/16__TREND_ENGINEER_SPC.md
- Album Showrunner SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/19__ALBUM_SHOWRUNNER_SPC.md
- Group Creative Director SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/20__GROUP_CREATIVE_DIRECTOR_SPC.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
