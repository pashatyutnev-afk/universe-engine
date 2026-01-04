# 🥁 RHYTHM & GROOVE ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · PRODUCTION ENGINE · GROOVE DESIGN · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 05__RHYTHM_GROOVE_ENG.md
- ENGINE_ID: L3-PROD-RHYTHM-GROOVE-ENGINE-005
- UID: UE.ENT.ENG.PROD.RHYTHM_GROOVE
- NAME: Rhythm & Groove Engine
- CLASS: Sound & Music Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (timing + pocket)
- EDITABLE: true

### ABSOLUTE RULE
> If the groove pocket is not defined, every element will fight the beat.

---

## 1. PURPOSE

Rhythm & Groove Engine designs **GROOVE_BLUEPRINTS**:
- beat grid + subdivision
- swing/feel and pocket placement (ahead/behind/on)
- drum role map (kick/snare/hat/percussion)
- rhythmic hook patterns (if needed)
- intensity dynamics per section
- sync alignment with edit points / hit points
- loop seam strategy (if loopable)

Outputs are blueprint-level: implementable by producers/composers.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define rhythmic foundation per section
- Define pocket feel and swing amount (conceptual)
- Define groove complexity and density
- Define accent map and syncopation budget
- Define drum role map and layering plan
- Define transition fills rules
- Define cut-safe rhythmic exits (edit-friendly)
- Define QA gates + repair plan

### OUT-OF-SCOPE (FORBIDDEN)
- harmony/chords (03)
- melody hook note design (04)
- full orchestration (08)
- mixing/mastering (13)

---

## 3. INPUT / OUTPUT

### 3.1 INPUT — GROOVE_REQUEST
Required fields:
- `rg_req_id`
- `timestamp`
- `song_blueprint_ref` (sections + durations)
- `tempo_band` (required)
- `meter` (required)
- `cue_type` (optional)
- `tone_profile_ref`
- `genre_profile_ref` (optional)
- `hook_blueprint_ref` (recommended if rhythmic hook)
- `constraints_refs`
- `sync_plan_ref` (optional)
- `loop_plan_ref` (optional)
- `trace_id` (optional)

Missing required input → REJECT.

### 3.2 OUTPUT — GROOVE_BLUEPRINT
Required fields:
- `groove_id`
- `engine_id`
- `version`
- `status` = DRAFT | PARTIAL | FINAL
- `grid_profile`
- `pocket_profile`
- `section_grooves`
- `syncopation_budget`
- `accent_map`
- `drum_role_map`
- `transition_rules`
- `edit_points`
- `loop_rules` (if loopable)
- `qa_gates`
- `repair_plan`

---

## 4. GRID PROFILE

### 4.1 GRID_PROFILE (required fields)
- `subdivision` = 1_2 | 1_4 | 1_8 | 1_16 | 1_8_TRIPLET | 1_16_TRIPLET | OTHER_DECLARED
- `humanize_level` (0–10)
- `quantize_policy` = STRICT | SOFT | HUMAN_ONLY
- `notes`

Hard rule:
- OTHER_DECLARED must specify exact subdivision concept.

---

## 5. POCKET PROFILE (FEEL)

### 5.1 POCKET_PROFILE (required fields)
- `feel` = STRAIGHT | SWUNG | SHUFFLE | HALF_TIME | DOUBLE_TIME | BROKEN
- `swing_amount` (0–10; 0 if straight)
- `placement` = AHEAD | ON | BEHIND
- `push_pull_rule` (where pushes happen)
- `notes`

Hard rule:
- if feel = SWUNG/SHUFFLE, swing_amount must be > 0.

---

## 6. SECTION GROOVES

### 6.1 SECTION_GROOVE (required fields)
Per `sec_id`:
- `groove_role` = FOUNDATION | BUILD | DROP | BREAK | RELEASE
- `density` (low/med/high)
- `complexity` (0–10)
- `kick_pattern_role` (simple/drive/sparse/offbeat)
- `snare_role` (backbeat/ghosts/sparse/claps)
- `hat_role` (steady/pulse/syncopated/none)
- `perc_layers` (0..n)
- `fill_policy` (none/rare/section_end)
- `notes`

Hard rule:
- hook sections must not exceed complexity threshold unless genre demands it.

---

## 7. SYNCOPATION BUDGET

### 7.1 SYNCOPATION_BUDGET (required fields)
- `budget_level` (0–10)
- `allowed_sources` (kick/hat/percs/melodic rhythm)
- `forbidden_sources`
- `hook_protection_rule` (avoid masking hook rhythm)
- `notes`

Hard rule:
- budget_level >= 7 requires explicit hook_protection_rule + accent_map clarity.

---

## 8. ACCENT MAP

### 8.1 ACCENT_MAP (required fields)
- `primary_accents` (grid positions or conceptual)
- `secondary_accents`
- `downbeat_policy` (strong/soft/avoid)
- `backbeat_policy` (strong/soft/none)
- `notes`

---

## 9. DRUM ROLE MAP (LAYERS)

### 9.1 DRUM_ROLE_MAP (required fields)
- `kick_layer` (role + density)
- `snare_layer` (role + density)
- `hat_layer` (role + density)
- `perc_layer` (role + density)
- `fx_rhythm_layer` (optional)
- `fills_layer` (optional)
- `mute_safe_policy` (what can be muted without losing pulse)

Hard rule:
- must define mute_safe_policy for editability.

---

## 10. TRANSITION RULES

### 10.1 TRANSITION_RULES (required fields)
- `fill_points` (list sec_id or timestamps)
- `fill_intensity` (0–10)
- `pickup_rule` (lead-in behavior)
- `drop_rule` (how to “land”)
- `break_rule` (how to remove elements)
- `notes`

Hard rule:
- transitions into primary hook sections must avoid over-fills.

---

## 11. EDIT POINTS (CUT-SAFE)

### 11.1 EDIT_POINTS (required fields)
- `entry_points` (list)
- `exit_points` (list)
- `hard_cut_safe_points` (list)
- `tail_policy` (reverb tail / ring-out / hard stop)
- `notes`

Hard rule:
- at least one exit point must exist per major section group (verse/chorus/drop).

---

## 12. LOOP RULES (OPTIONAL)

If loop_plan_ref indicates loopable:

### 12.1 LOOP_RULES (required fields)
- `loop_seam_strategy` (crossfade/hardcut/tail-match)
- `loop_length_ref`
- `no_click_rule` (mandatory)
- `groove_reset_policy` (how loop restarts without “jump”)
- `notes`

---

## 13. QA GATES

### 13.1 QA_GATES (required fields)
- `grid_gate` (subdivision valid, consistent)
- `pocket_gate` (feel defined and coherent)
- `hook_protection_gate` (groove not masking hook)
- `energy_gate` (density/complexity matches song energy curve)
- `edit_gate` (entry/exit/cut points exist)
- `loop_gate` (if loopable)

Fail rules:
- pocket_gate fail → INVALID (HIGH/CRITICAL)
- edit_gate fail → PARTIAL/INVALID depending on usage

---

## 14. REPAIR PLAN (MANDATORY)

### 14.1 REPAIR PLAN (required)
Common repairs:
- groove feels stiff → increase humanize_level / soften quantize
- groove too busy → reduce density / lower syncopation budget
- hook masked → simplify hats/percs in hook section
- transitions messy → reduce fill intensity, add drop rule
- not cut-friendly → add exit points + tail policy
- loop clicks → adjust seam strategy + reset policy

Include:
- `recheck_gates`
- `max_revision_cycles`

---

## 15. CORE OPERATIONS

- OP_01: INGEST_REQUEST
- OP_02: SET_GRID_PROFILE
- OP_03: SET_POCKET_PROFILE
- OP_04: BUILD_SECTION_GROOVES
- OP_05: SET_SYNCOPATION_BUDGET
- OP_06: BUILD_ACCENT_MAP
- OP_07: BUILD_DRUM_ROLE_MAP
- OP_08: BUILD_TRANSITION_RULES
- OP_09: BUILD_EDIT_POINTS
- OP_10: BUILD_LOOP_RULES (if needed)
- OP_11: BUILD_QA_GATES
- OP_12: BUILD_REPAIR_PLAN
- OP_13: EMIT_GROOVE_BLUEPRINT

---

## 16. FAILURE CONDITIONS (ENGINE)

CRITICAL:
- meter missing
- tempo_band missing
- sections missing

Reaction:
- reject (fail-closed)
- request missing inputs

---

## 17. NON-GOALS
- does not write melody/harmony
- does not mix/master
- does not generate final drum samples

---

## 18. FINAL STATEMENT

Groove is gravity.
Define the pocket — or everything floats.

---

**STATUS:** Rhythm & Groove Engine v1.0  
**REALM:** ACTIVE
