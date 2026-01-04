# 🧱 SONG STRUCTURE ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · PRODUCTION ENGINE · SONG BLUEPRINTS · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 02__SONG_STRUCTURE_ENG.md
- ENGINE_ID: L3-PROD-SONG-STRUCTURE-ENGINE-002
- UID: UE.ENT.ENG.PROD.SONG_STRUCTURE
- NAME: Song Structure Engine
- CLASS: Sound & Music Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (structure + hook)
- EDITABLE: true

### ABSOLUTE RULE
> If structure does not control repetition and payoff, the song will not land.

---

## 1. PURPOSE

Song Structure Engine designs **SONG_BLUEPRINTS**:
- sections (intro/verse/pre/chorus/bridge/outro)
- repetition and variation rules
- hook placement and timing
- dynamic/intensity curves
- short-form vs long-form patterns
- editability for multiple formats (full, cutdown, loop)

It outputs a blueprint that other engines fill in:
- Harmony & Chord (03)
- Melody Hook (04)
- Rhythm Groove (05)
- Lyrics (07)
- Arrangement (08)

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Select structure template based on format goals
- Define section list and durations
- Define hook slots and “arrival points”
- Define repetition/variation rules
- Define tension/release curve at section level
- Define cutdown strategy (15s/30s/60s)
- Define loop strategy (beds, shorts)

### OUT-OF-SCOPE (FORBIDDEN)
- writing melody
- writing harmony details
- writing lyrics text
- mixing/mastering

---

## 3. INPUT / OUTPUT

### 3.1 INPUT — SONG_STRUCTURE_REQUEST
Required fields:
- `ss_req_id`
- `timestamp`
- `target_format_ref` (SHORT_6_22 | SHORT_15 | SHORT_30 | SHORT_60 | SONG_2_4MIN | SONG_3_5MIN | SCORE_CUE)
- `tone_profile_ref`
- `genre_profile_ref` (optional)
- `hook_priority` (HIGH | MEDIUM | LOW)
- `duration_target` (required)
- `constraints_refs`
- `continuity_anchors_ref` (optional but recommended)
- `trace_id` (optional)

Missing required input → REJECT.

### 3.2 OUTPUT — SONG_BLUEPRINT
Required fields:
- `song_id`
- `engine_id`
- `version`
- `status` = DRAFT | PARTIAL | FINAL
- `target_format_ref`
- `duration_target`
- `structure_template_id`
- `sections` (ordered list)
- `hook_map`
- `repetition_rules`
- `variation_rules`
- `energy_curve`
- `cutdown_plan`
- `loop_plan`
- `delivery_notes`
- `qa_gates`
- `repair_plan`

---

## 4. STRUCTURE TEMPLATES (ENUM)

### 4.1 TEMPLATE ENUM
- TPL_SHORT_HOOK_FAST (6–22s)
- TPL_SHORT_VERSE_HOOK (15–30s)
- TPL_SHORT_BUILD_DROP (30–60s)
- TPL_POP_STANDARD (2–4m)
- TPL_POP_BRIDGE_LIFT (3–5m)
- TPL_HOOK_LOOP (loopable)
- TPL_SCORE_ARC (cue-like)

Hard rule:
- template must match target_format_ref.

---

## 5. SECTION MODEL

### 5.1 SECTION (required fields)
- `sec_id`
- `sec_type` = INTRO | VERSE | PRE_CHORUS | CHORUS | POST_CHORUS | BRIDGE | BREAKDOWN | DROP | OUTRO | TAG | BUILD | RELEASE
- `duration_ref` (seconds or %)
- `function` (what this section does)
- `energy_target` (0–10)
- `hook_presence` = NONE | MICRO | PRIMARY
- `lyrics_density` (low/med/high/none)
- `notes`

Hard rule:
- every section must have function + energy_target.

---

## 6. HOOK MAP

### 6.1 HOOK MAP (required fields)
- `primary_hook_section_ids` (list)
- `hook_arrival_time_targets` (list of timestamps)
- `hook_reentry_rule` (how often hook repeats)
- `hook_variation_budget` (0–10)
- `hook_signature_lock` (true/false)

Hard rule:
- if hook_priority = HIGH, primary hook must appear within:
  - 0–7s for SHORT formats
  - 0–45s for SONG formats

---

## 7. REPETITION RULES

### 7.1 REPETITION_RULES (required fields)
- `section_repeat_map` (sec_type → allowed repeats)
- `max_identical_repeat_count`
- `repeat_spacing_rule` (how repeats are spaced)
- `forbidden_repeat_pairs` (e.g., “CHORUS immediately twice” unless declared)
- `repetition_intent_tag` (optional)

Hard rule:
- more repeats requires more variation in at least one dimension (melody/rhythm/arrangement/lyrics).

---

## 8. VARIATION RULES

### 8.1 VARIATION_RULES (required fields)
Allowed variation dimensions:
- MELODY
- HARMONY
- RHYTHM
- ARRANGEMENT
- LYRICS
- DYNAMICS
- FX

Fields:
- `allowed_dimensions` (list)
- `variation_budget` (0–10)
- `minimum_variation_required` (per repeat)
- `forbidden_dimensions` (list)
- `notes`

Hard rule:
- if hook_signature_lock = true, hook melody contour cannot be altered beyond budget.

---

## 9. ENERGY CURVE

### 9.1 ENERGY_CURVE (required fields)
- `curve_points` (timestamp → 0–10)
- `peak_target_time` (optional)
- `release_target_time` (optional)
- `fatigue_rule` (avoid constant 9–10 unless intended)

---

## 10. CUTDOWN PLAN

### 10.1 CUTDOWN_PLAN (required fields)
- `versions` (list):
  - 6–22s
  - 15s
  - 30s
  - 60s
  - FULL
- for each version:
  - `version_id`
  - `duration_target`
  - `section_subset` (ordered)
  - `entry_point`
  - `exit_point`
  - `hook_presence` requirement

Hard rule:
- every cutdown must contain the primary hook or a declared micro-hook substitute.

---

## 11. LOOP PLAN

### 11.1 LOOP_PLAN (required fields)
- `loopable` (bool)
- `loop_length_ref`
- `loop_seam_strategy` (crossfade / reverb-tail / hard-cut)
- `loop_entry_exit_points`
- `no-click_rule` (must avoid clicks)
- `notes`

---

## 12. QA GATES

### 12.1 QA_GATES (required fields)
- `structure_gate` (sections valid, ordered, durations sum)
- `hook_gate` (hook appears on time)
- `repetition_gate` (no dead repeats)
- `variation_gate` (variation rules satisfied)
- `format_gate` (matches target format)
- `edit_gate` (cutdown plan present)
- `loop_gate` (if loopable)

Fail rules:
- hook_gate fail in HIGH hook priority → INVALID (HIGH)
- structure_gate fail → INVALID (HIGH/CRITICAL)

---

## 13. REPAIR PLAN (MANDATORY)

### 13.1 REPAIR PLAN (required)
- If hook too late → move hook section earlier or insert micro-hook
- If repeats too identical → add variation dimension per repeat
- If duration mismatch → resize sections (keep hook intact)
- If energy flat → introduce build/release contrast
- If cutdowns missing → derive cutdown versions from hook sections

Include:
- `recheck_gates`
- `max_revision_cycles`

---

## 14. CORE OPERATIONS

- OP_01: INGEST_REQUEST
- OP_02: SELECT_STRUCTURE_TEMPLATE
- OP_03: BUILD_SECTION_LIST_AND_DURATIONS
- OP_04: BUILD_HOOK_MAP
- OP_05: BUILD_REPETITION_RULES
- OP_06: BUILD_VARIATION_RULES
- OP_07: BUILD_ENERGY_CURVE
- OP_08: BUILD_CUTDOWN_PLAN
- OP_09: BUILD_LOOP_PLAN
- OP_10: BUILD_QA_GATES
- OP_11: BUILD_REPAIR_PLAN
- OP_12: EMIT_SONG_BLUEPRINT

---

## 15. FAILURE CONDITIONS (ENGINE)

CRITICAL:
- duration_target missing
- target_format_ref missing
- hook_priority missing

Reaction:
- reject (fail-closed)
- request missing inputs

---

## 16. NON-GOALS
- does not compose melody or chords
- does not generate lyrics text
- does not mix/master

---

## 17. FINAL STATEMENT

Structure is the promise.
Hook is the payoff.
Without both — no song survives repetition.

---

**STATUS:** Song Structure Engine v1.0  
**REALM:** ACTIVE
