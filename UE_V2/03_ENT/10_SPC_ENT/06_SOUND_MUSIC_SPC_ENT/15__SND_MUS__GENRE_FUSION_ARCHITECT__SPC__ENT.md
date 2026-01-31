# GENRE FUSION ARCHITECT — SPC
FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/15__GENRE_FUSION_ARCHITECT_SPC.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: SPECIALISTS (SPC)
SPECIALIST_DOMAIN: SOUND_MUSIC
DOC_TYPE: SPECIALIST
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.SPC.SND.GENRE_FUSION_ARCHITECT.001
OWNER: SYSTEM
ROLE: Owns controlled genre blending:
selects fusion candidates, defines axis-limited recipes (A/B/C ratios), insertion points, drift blockers,
and ensures fused outputs stay inside Style Fingerprint anchors and platform prompt fidelity.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Genre Fusion Architect SPC: responsibilities, interfaces, outputs, and gates for controlled fusion."
- REASON: "Uncontrolled fusion causes drift and incoherent tracks; we need a specialist role to apply Fusion Recipe rules."
- IMPACT: "Trend-ready hybrids with stable identity and repeatable production."
- CHANGE_ID: UE.CHG.2026-01-12.SPC.GENRE_FUSION_ARCHITECT.001

---

## 0) PURPOSE (LAW)
Genre Fusion Architect ensures:
- one primary identity (Genre A) stays dominant
- Genre B/C influence is axis-limited and ratio-controlled
- fusion happens at chosen insertion points (not everywhere)
- drift blockers prevent “genre soup”
- fusion is encoded clearly for Prompt Architect / Prompt Compiler

---

## 1) SCOPE
### In scope
- selecting fusion candidates (B/C) from taxonomy
- defining fusion recipe ratios and owned axes
- defining insertion points (drop/bridge/pre-hook etc.)
- defining drift blockers and forbiddens
- producing fusion variants V1..V3 when needed

### Out of scope
- writing hooks and UGC moments (Earworm/UGC roles)
- naming (Naming engines)
- policy ownership (CTL) and validator logic (VAL)

---

## 2) INTERFACES (RAW)
### Primary engines consumed
- Genre Taxonomy ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/01__GENRE_TAXONOMY_ENG.md
- Fusion Recipe ENG (core)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/02__FUSION_RECIPE_ENG.md
- Style Fingerprint ENG (anchors/forbiddens)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/03__STYLE_FINGERPRINT_ENG.md
- Prompt Compiler ENG (encoding)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/07__PROMPT_COMPILER_ENG.md

### Controllers applied
- Negative Spec Library CTL (anti-drift list)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/12__NEGATIVE_SPEC_LIBRARY_CTL.md
- Duration Policy CTL (where fusion is safest)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/03__DURATION_POLICY_CTL.md

### Validators / QA referenced
- Prompt Fidelity VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/08__PROMPT_FIDELITY_VAL.md
- Collision Blocker VAL (avoid sameness)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/05__COLLISION_BLOCKER_VAL.md

---

## 3) KNOWLEDGE BASE (KB) SCOPE
### Inputs
- primary genre A (group/track intent)
- audience segment target
- style fingerprint anchors and forbiddens
- catalog memory (avoid repeating same fusion)
- platform prompt constraints

### Outputs
- Fusion Recipe Pack (A/B/C, ratios, axes, insertion points)
- Drift Blocker Set (negative specs additions)
- Fusion Variant Set (V1..V3, optional)
- Prompt Encoding Notes (how to say fusion without contradictions)

### Boundaries
- no “creative writing”; only controlled fusion specs and risks.

RAW references: (see INTERFACES section)

---

## 4) OUTPUTS (MANDATORY)
### FUSION RECIPE PACK (FRP)
- PRIMARY_GENRE_A:
- SECONDARY_GENRE_B:
- MICRO_GENRE_C (optional):
- RATIO: (A/B/C)
- OWNED_AXES:
  - A owns:
  - B owns:
  - C owns:
- INSERTION_POINTS:
  - where B appears (drop/bridge/pre-hook etc.)
- ANCHOR_PRESERVATION:
  - locked anchors
- DRIFT_BLOCKERS:
  - concrete “no-go” list
- PROMPT_ENCODING_NOTES:
  - short fusion phrasing lines

---

## 5) PROCESS (OPERATIONAL)
1) Confirm primary genre A and fingerprint anchors.
2) Choose B candidate:
   - compatibility high/medium per taxonomy
   - must add novelty without breaking identity
3) Decide ratio:
   - default 70/30
   - safe 85/15
   - aggressive 60/40 only if approved
4) Choose owned axes:
   - B owns max 1–2 axes
   - A owns at least 3 axes
5) Choose insertion points:
   - 1–2 primary insertion points max
6) Write drift blockers:
   - prevent full genre switch
   - prevent conflicting vocal style
   - prevent random instruments
7) Emit FRP and optional variants V1..V3.

---

## 6) GATES (PASS/FAIL)
PASS when:
- A identity remains dominant (ratio + axes)
- insertion points are explicit and limited
- drift blockers are concrete
- prompt encoding is clear and non-contradictory
- collision risk is reduced (or at least not increased)

FAIL when:
- too many axes owned by B/C
- fusion everywhere in track
- drift blockers vague
- contradictory genre tags likely to break fidelity

---

## 7) SPC PEER ROLES (NON-ENG)
Works with:
- Prompt Architect SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC.md
- Earworm Director SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/14__EARWORM_DIRECTOR_SPC.md
- Trend Engineer SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/16__TREND_ENGINEER_SPC.md
- Group Creative Director SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/20__GROUP_CREATIVE_DIRECTOR_SPC.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
