# 👁️‍🗨️ SENSORY DETAIL ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · STYLE ENGINE · SENSE CONTROL · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 06__SENSORY_DETAIL_ENG.md
- ENGINE_ID: L3-STYLE-SENSORY-DETAIL-ENGINE-006
- UID: UE.ENT.ENG.STYLE.SENSORY_DETAIL
- NAME: Sensory Detail Engine
- CLASS: Style Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (clarity integrity)
- EDITABLE: true

### ABSOLUTE RULE
> Sensory detail must serve meaning or action. If it delays causality, it becomes noise.

---

## 1. PURPOSE

Sensory Detail Engine defines:
- **what senses are used**
- **how much detail** is allowed
- **where density rises/falls**
- **how motifs repeat** without overload

It produces:
- **SENSORY_DETAIL_SCHEMA**
- density pacing plan (windows)
- modality balance (sight/sound/touch/smell/taste + internal)
- show-don’t-drown gates
- repair hints (reduce clutter, increase vividness)

This engine prevents purple-prose overload and “blank room” scenes.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define sensory schema and modality rules
- Set density budgets per arc/sequence/scene type
- Balance modalities and motifs
- Tie sensory motifs to atmosphere/symbolism/metaphor
- Validate sensory detail does not break pacing and causality
- Emit constraints for scene construction and production engines

### OUT-OF-SCOPE (FORBIDDEN)
- Plot decisions
- Canon authority decisions
- Full prose generation (only schema and constraints)

---

## 3. SENSORY DETAIL MODEL

### 3.1 Output — SENSORY_DETAIL_SCHEMA (required fields)
- `sd_id`
- `scope` = PROJECT | ARC | SEQUENCE | SCENE_TYPE
- `density_profile` (by windows)
- `modality_weights` (percent distribution)
- `motif_registry` (optional but recommended)
- `gates` (hard rules)
- `allowed_detail_types` (list)
- `forbidden_detail_types` (list)
- `integrity_report` (issues + fixes)
- `trace_id` (optional)

Missing any required field → REJECT.

### 3.2 Density Window (required fields)
- `window_id`
- `time_ref`
- `density` = NONE | SPARSE | MEDIUM | HIGH
- `max_sensory_tokens` (budget unit; symbolic ok)
- `priority_modalities` (list)
- `allowed_motifs` (optional list)
- `purpose` (clarify / immerse / intensify / contrast)
- `notes`

Missing any required field → REJECT.

### 3.3 Modality Weights (required fields)
- `sight`
- `sound`
- `touch`
- `smell`
- `taste`
- `internal` (breath/heartbeat/vertigo/pain)

Sum must equal 100 (±1 tolerance) → else INVALID.

### 3.4 Motif Object (optional registry but if present must be valid)
- `motif_id`
- `type` = SOUND | LIGHT | TEXTURE | SMELL | TEMPERATURE | COLOR | RHYTHM
- `meaning_hook` (what it supports)
- `activation_triggers` (refs)
- `recurrence_rule`
- `decay_rule`

---

## 4. SHOW-DON’T-DROWN GATES (HARD)

- Causality gate:
  - any HIGH density window must include at least 1 causal action beat (event progression) unless explicitly marked “pause”.
- Pacing gate:
  - no more than 2 consecutive HIGH windows per arc unless genre is “poetic saturation”.
- Modality gate:
  - no single modality > 70 unless explicitly justified (e.g., blindness → sound-heavy).
- Detail relevance gate:
  - every sensory detail must belong to one of:
    - action support
    - atmosphere support
    - symbolism/metaphor support
    - emotional resonance support
  Else → NOISE.

---

## 5. CONTROLLED VOCABULARY (STANDARD)

Allowed detail types:
- SPATIAL_ORIENTATION (where we are)
- MATERIAL_TEXTURE (what things feel like)
- AMBIENT_SOUND
- LIGHT_AND_SHADOW
- TEMPERATURE_AND_AIR
- SMELL_TRACE (rare but powerful)
- BODY_SIGNAL (internal)

Forbidden (unless explicitly allowed by constraints):
- exhaustive inventory lists
- technical dumps that stall action
- repeated sensory synonyms without new information

---

## 6. INPUT ARTIFACTS

### 6.1 INPUT — SENSORY_DETAIL_REQUEST
**REQUIRED FIELDS**
- `sd_req_id`
- `timestamp`
- `tone_profile_ref` (required)
- `mood_curve_ref` (recommended)
- `atmosphere_layer_map_ref` (required)
- `symbol_system_ref` (recommended)
- `metaphor_system_ref` (recommended)
- `constraints_refs` (required)
- `production_format_ref` (optional: book/series/short)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 7. OUTPUT ARTIFACTS

### 7.1 OUTPUT — SENSORY_DETAIL_SCHEMA
(see model above)

### 7.2 OUTPUT — SENSORY_DETAIL_VERDICT
- `sd_req_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 8. CORE OPERATIONS

- OP_01: INGEST_TONE_MOOD_ATMOSPHERE_CONSTRAINTS
- OP_02: DEFINE_DENSITY_PROFILE_WINDOWS (pacing-aligned)
- OP_03: SET_MODALITY_WEIGHTS (balanced or intentional skew)
- OP_04: DEFINE_ALLOWED_FORBIDDEN_DETAIL_TYPES
- OP_05: DEFINE_MOTIF_REGISTRY (optional) + recurrence/decay
- OP_06: APPLY_SHOW_DONT_DROWN_GATES
- OP_07: EMIT_SENSORY_DETAIL_SCHEMA

---

## 9. CLUTTER DETECTION

Hard violations (INVALID):
- modality weights sum wrong
- repeated HIGH density without pacing relief
- HIGH density windows with no causal action beat (unmarked)
- detail relevance gate violated frequently

Soft violations (PARTIAL):
- too generic sensory language (low specificity)
- motif appears too often (decay violated)

Repair suggestions:
- reduce density windows
- shift modality weights
- swap inventory for 1–2 sharp cues
- tie motifs to meaning hooks
- add “pause” marker where intended

---

## 10. DEPENDENCIES

### REQUIRED
- Atmosphere Layer Map
- Tone Profile
- Constraints refs

### OPTIONAL
- Mood curve
- Symbol & metaphor systems
- Production format

### FORBIDDEN
- sensory overload that stalls story motion
- sensory emptiness that breaks immersion (NONE everywhere)
- motifs with no recurrence/decay logic

---

## 11. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- No density profile
- Gates missing
- Atmosphere layer map not referenced
- Modality weights invalid
- Integrity report indicates systematic drowning of causality

Reaction:
- Verdict INVALID (CRITICAL)
- Emit repair plan:
  - rebuild density profile
  - enforce gates
  - rebalance modalities
  - reduce irrelevant detail

---

## 12. TRACE RULES

- trace_id optional unless pipeline requires traced execution
- if present, propagate into scene construction and production packaging

---

## 13. NON-GOALS
- Does not write prose
- Does not decide plot or canon
- Does not replace atmosphere engine

---

## 14. FINAL STATEMENT

Sensory detail is a budget.
Spend it where it hits — not everywhere.

---

**STATUS:** Sensory Detail Engine v1.0  
**REALM:** ACTIVE
