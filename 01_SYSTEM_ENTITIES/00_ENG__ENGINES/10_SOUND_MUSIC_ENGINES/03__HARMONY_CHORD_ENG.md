# 🎼 HARMONY & CHORD ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · PRODUCTION ENGINE · HARMONIC DESIGN · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 03__HARMONY_CHORD_ENG.md
- ENGINE_ID: L3-PROD-HARMONY-CHORD-ENGINE-003
- UID: UE.ENT.ENG.PROD.HARMONY_CHORD
- NAME: Harmony & Chord Engine
- CLASS: Sound & Music Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (harmonic continuity)
- EDITABLE: true

### ABSOLUTE RULE
> Harmony must serve structure and emotion — and must not break motif identity.

---

## 1. PURPOSE

Harmony & Chord Engine designs **HARMONY_BLUEPRINTS**:
- key / tonal center plan (conceptual)
- chord progression templates per section
- tension & release mapping
- cadence rules
- modal color choices
- voicing constraints (coarse)
- compatibility locks for melody/hook and motif plan

It outputs a blueprint that Melody Hook (04) and Arrangement (08) can implement.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define tonal center / key plan (may be abstract)
- Select progression templates per section type
- Define harmonic rhythm (chord change rate)
- Define tension mapping and release points
- Define cadence types and placement
- Define modulation rules (if allowed)
- Define dissonance budget
- Define compatibility gates with hook/motif locks

### OUT-OF-SCOPE (FORBIDDEN)
- writing the melody notes
- detailed orchestration and voicing (beyond constraints)
- mixing/mastering
- lyric writing

---

## 3. INPUT / OUTPUT

### 3.1 INPUT — HARMONY_REQUEST
Required fields:
- `hc_req_id`
- `timestamp`
- `song_blueprint_ref` (or structure summary)
- `tone_profile_ref`
- `genre_profile_ref` (optional)
- `harmonic_color_ref` (from composition engine or declared)
- `constraints_refs`
- `motif_plan_ref` (required if motifs used)
- `hook_map_ref` (recommended)
- `trace_id` (optional)

Missing required input → REJECT.

### 3.2 OUTPUT — HARMONY_BLUEPRINT
Required fields:
- `harmony_id`
- `engine_id`
- `version`
- `status` = DRAFT | PARTIAL | FINAL
- `tonal_center_plan`
- `section_progressions` (map sec_id → progression)
- `harmonic_rhythm_plan`
- `tension_release_map`
- `cadence_plan`
- `modal_color_plan`
- `dissonance_budget`
- `modulation_rules`
- `voicing_constraints`
- `compatibility_locks`
- `qa_gates`
- `repair_plan`

---

## 4. TONAL CENTER PLAN

### 4.1 TONAL_CENTER_PLAN (required fields)
- `center_type` = KEYED | MODAL | ATONAL_CONTROLLED
- `primary_center` (e.g., “A minor” or “center A”; conceptual ok)
- `secondary_centers` (optional list)
- `center_stability` (0–10)
- `notes`

Hard rule:
- if ATONAL_CONTROLLED, must define dissonance_budget + cadence_plan strategy.

---

## 5. PROGRESSION TEMPLATES (ENUM)

### 5.1 TEMPLATE ENUM (examples, not tied to exact chords)
- TPL_POP_I_V_VI_IV
- TPL_POP_VI_IV_I_V
- TPL_MINOR_I_VI_III_VII
- TPL_MODAL_DRONE
- TPL_TENSION_PEDAL
- TPL_TWO_CHORD_VAMP
- TPL_CINEMATIC_STEPWISE
- TPL_AMBIENT_STATIC
- TPL_DISSONANT_CLUSTER_CONTROLLED
- TPL_OTHER_DECLARED

Hard rule:
- if OTHER_DECLARED, must provide progression logic description.

---

## 6. SECTION PROGRESSION MODEL

### 6.1 SECTION_PROGRESSION (required fields)
- `sec_id`
- `template_id`
- `chord_function_flow` (tonic/predominant/dominant or equivalent)
- `harmonic_rhythm` (slow/med/fast + optional bars-per-change)
- `tension_level` (0–10)
- `release_target` (bool)
- `cadence_target` (enum)
- `notes`

Hard rule:
- chorus (or hook section) must have a defined cadence_target.

---

## 7. HARMONIC RHYTHM PLAN

### 7.1 HARMONIC_RHYTHM_PLAN (required fields)
- `global_rate` (slow/med/fast)
- `per_section_rate_override` (map sec_id → rate)
- `sync_alignment_rule` (align chord changes to cuts/hitpoints if provided)
- `notes`

---

## 8. TENSION / RELEASE MAP

### 8.1 TENSION_RELEASE_MAP (required fields)
- `tension_points` (timestamp or sec_id → tension 0–10)
- `release_points` (list of sec_id or timestamps)
- `build_rule` (how tension rises)
- `release_rule` (how it resolves)
- `avoid_rule` (what to avoid, e.g., early full resolve)

Hard rule:
- climax/reveal cues must declare at least one release point.

---

## 9. CADENCE PLAN

### 9.1 CADENCE ENUM
- AUTHENTIC_STRONG
- AUTHENTIC_SOFT
- PLAGAL
- DECEPTIVE
- HALF
- NO_CADENCE (requires explanation)
- OTHER_DECLARED

### 9.2 CADENCE_PLAN (required fields)
- `cadences` (list of cadence entries)
Each entry:
- `sec_id`
- `cadence_type`
- `strength` (0–10)
- `target_effect` (resolve/suspend/surprise)
- `notes`

Hard rule:
- if NO_CADENCE, must define alternative resolution strategy (texture/dynamics).

---

## 10. MODAL COLOR PLAN

### 10.1 MODAL_COLOR_PLAN (required fields)
- `mode_palette` (list: major/minor/dorian/phrygian/etc.)
- `mode_rules` (when each mode is used)
- `avoid_modes` (optional)
- `notes`

---

## 11. DISSONANCE BUDGET

### 11.1 DISSONANCE_BUDGET (required fields)
- `budget_level` (0–10)
- `allowed_sources` (extensions/clusters/pedals/bitonality/etc.)
- `forbidden_sources`
- `resolution_rule` (how to resolve dissonance)
- `notes`

Hard rule:
- if budget_level >= 7, must define explicit resolution_rule.

---

## 12. MODULATION RULES

### 12.1 MODULATION_RULES (required fields)
- `allowed` (bool)
- `max_modulations` (0..n)
- `allowed_targets` (relative/parallel/stepwise/other)
- `trigger_sections` (where modulation may occur)
- `forbidden_sections`
- `notes`

Hard rule:
- hook sections cannot modulate unless explicitly approved by motif/hook locks.

---

## 13. VOICING CONSTRAINTS (COARSE)

### 13.1 VOICING_CONSTRAINTS (required fields)
- `register_focus` (low/mid/high/mixed)
- `spread_rule` (tight/medium/wide)
- `avoid_intervals` (optional)
- `signature_interval` (optional)
- `notes`

---

## 14. COMPATIBILITY LOCKS (HOOK + MOTIF)

### 14.1 COMPATIBILITY_LOCKS (required fields)
- `hook_protection_rule` (do not undercut melody contour)
- `motif_identity_lock_ref` (from motif plan)
- `forbidden_progression_changes_for_hook` (list)
- `allowed_variation_budget_for_hook_harmony` (0–10)
- `collision_checks` (what to check: cadence timing, tension overlap)

Hard rule:
- if hook_signature_lock = true (from Song Structure), harmony variation budget must be <= 4 unless override declared.

---

## 15. QA GATES

### 15.1 QA_GATES (required fields)
- `tone_gate` (matches harmonic_color + tone profile)
- `structure_gate` (progressions mapped to all sections)
- `cadence_gate` (cadences defined where needed)
- `tension_gate` (tension/release matches energy curve)
- `hook_lock_gate` (hook not harmed)
- `modulation_gate` (within rules)
- `deliverability_gate` (can be realized by arrangement)

Fail rules:
- hook_lock_gate fail → INVALID (HIGH/CRITICAL)
- missing section progression → INVALID (HIGH)

---

## 16. REPAIR PLAN (MANDATORY)

### 16.1 REPAIR PLAN (required)
Common repairs:
- tone mismatch → change mode palette / reduce dissonance
- hook harmed → simplify cadence / reduce chord rate / lock progression
- too static → add harmonic motion in build sections
- too busy → slow harmonic rhythm
- climax lacks release → add cadence/release point
- modulation confusion → remove or constrain to bridge

Include:
- `max_revision_cycles`
- `recheck_gates`

---

## 17. CORE OPERATIONS

- OP_01: INGEST_REQUEST
- OP_02: PARSE_STRUCTURE_AND_HOOK_MAP
- OP_03: SELECT_TONAL_CENTER_PLAN
- OP_04: ASSIGN_TEMPLATES_PER_SECTION
- OP_05: BUILD_HARMONIC_RHYTHM_PLAN
- OP_06: BUILD_TENSION_RELEASE_MAP
- OP_07: BUILD_CADENCE_PLAN
- OP_08: BUILD_MODAL_COLOR_PLAN
- OP_09: SET_DISSONANCE_BUDGET
- OP_10: SET_MODULATION_RULES
- OP_11: SET_VOICING_CONSTRAINTS
- OP_12: APPLY_COMPATIBILITY_LOCKS
- OP_13: BUILD_QA_GATES
- OP_14: BUILD_REPAIR_PLAN
- OP_15: EMIT_HARMONY_BLUEPRINT

---

## 18. FAILURE CONDITIONS (ENGINE)

CRITICAL:
- structure/sections missing
- tone_profile_ref missing
- motif_plan_ref required but missing (if motifs used)

Reaction:
- reject (fail-closed)
- request missing refs

---

## 19. NON-GOALS
- does not compose melody lines
- does not orchestrate full voicings
- does not mix/master

---

## 20. FINAL STATEMENT

Harmony is the emotional floor.
If it collapses, every hook falls with it.

---

**STATUS:** Harmony & Chord Engine v1.0  
**REALM:** ACTIVE
