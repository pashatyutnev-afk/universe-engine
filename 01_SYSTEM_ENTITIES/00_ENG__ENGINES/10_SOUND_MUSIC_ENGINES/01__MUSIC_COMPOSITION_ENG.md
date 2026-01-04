# 🎹 MUSIC COMPOSITION ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · PRODUCTION ENGINE · MUSIC GENERATION / COMPOSITION · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 01__MUSIC_COMPOSITION_ENG.md
- ENGINE_ID: L3-PROD-MUSIC-COMPOSITION-ENGINE-001
- UID: UE.ENT.ENG.PROD.MUSIC_COMPOSITION
- NAME: Music Composition Engine
- CLASS: Sound & Music Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (continuity + deliverability)
- EDITABLE: true

### ABSOLUTE RULE
> A cue is valid only if it can be reproduced, varied, and synced without breaking continuity.

---

## 1. PURPOSE

Music Composition Engine produces **MUSIC_CUE specs** that are:
- consistent with tone/genre constraints
- linked to scene timing and narrative function
- compatible with motif locks
- deliverable as stems
- repairable and iteratable

This engine does not need to output actual audio.  
It outputs a **composition blueprint** usable by human/AI composer tools.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define cue purpose and cue type (bed, stinger, transition, theme, pulse)
- Register motif usage and recurrence rules
- Define tempo band, meter, harmonic color (conceptual)
- Define instrumentation palette constraints
- Define cue arc (intro/build/release/outro)
- Define sync hooks + cut points
- Define stem plan and export plan
- Define QA gates and repair plan

### OUT-OF-SCOPE (FORBIDDEN)
- Mixing/mastering (13 engine)
- Detailed harmony/chord selection (03 engine)
- Melody/hook construction in detail (04 engine)
- Rhythm/groove design in detail (05 engine)
- Lyrics/vocals (06–09 engines)
- Sound design SFX (10 engine)

---

## 3. INPUT / OUTPUT

### 3.1 INPUT — MUSIC_COMPOSITION_REQUEST
Required fields:
- `mc_req_id`
- `timestamp`
- `target_format_ref`
- `tone_profile_ref`
- `genre_profile_ref` (optional but recommended)
- `scene_ref` (optional)
- `duration_target` (required)
- `cue_type` (required)
- `constraints_refs` (required)
- `continuity_anchors_ref` (required)
- `editing_hooks_ref` (optional)
- `trace_id` (optional)

Missing required input → REJECT.

### 3.2 OUTPUT — MUSIC_CUE_BLUEPRINT
Required fields:
- `cue_id`
- `engine_id`
- `version`
- `status` = DRAFT | PARTIAL | FINAL
- `cue_type`
- `purpose`
- `duration_target`
- `tempo_band`
- `meter`
- `harmonic_color`
- `motif_plan`
- `arrangement_constraints`
- `cue_arc`
- `sync_plan`
- `stem_plan`
- `delivery_profile`
- `qa_gates`
- `repair_plan`
- `integrity_report`
- `trace_id` (optional)

Missing required fields → INVALID.

---

## 4. CUE TYPES (ENUM)

Allowed `cue_type`:
- THEME_CUE
- BED_CUE
- TENSION_PULSE
- STINGER
- TRANSITION_CUE
- REVEAL_CUE
- CLIMAX_CUE
- RESOLUTION_CUE
- DIEGETIC_CUE (music in-world)

Hard rule:
- cue_type must be one of enum values.

---

## 5. PURPOSE MODEL

### 5.1 PURPOSE (required fields)
- `narrative_function` (what it does)
- `emotion_target` (what it makes viewer feel)
- `intensity_curve_target` (0–10 over time)
- `constraints_summary` (short)
- `avoid_list` (what must NOT happen)

---

## 6. TEMPO / METER / HARMONIC COLOR

### 6.1 TEMPO_BAND (conceptual)
- `slow` | `mid` | `fast` with optional numeric hints

### 6.2 METER (enum)
- 4_4 | 3_4 | 6_8 | 5_4 | OTHER_DECLARED

### 6.3 HARMONIC_COLOR (enum)
- MAJOR_BRIGHT
- MINOR_DARK
- DORIAN_MYSTIC
- PHRYGIAN_TENSION
- AMBIENT_NEUTRAL
- DISSONANT_PRESSURE
- OTHER_DECLARED

Hard rule:
- if OTHER_DECLARED, must include description.

---

## 7. MOTIF PLAN (CONTINUITY LOCK)

### 7.1 MOTIF_PLAN (required fields)
- `motif_ids_used` (list)
- `motif_roles` (map motif_id → role)
- `recurrence_rule` (when it repeats)
- `variation_budget` (0–10)
- `forbidden_variations` (list)
- `motif_identity_lock` (true/false)

Hard rule:
- variation_budget > 0 requires explicit allowed variation types.

---

## 8. ARRANGEMENT CONSTRAINTS (COARSE)

### 8.1 ARRANGEMENT_CONSTRAINTS (required fields)
- `instrument_palette_lock` (list of allowed instrument groups)
- `instrument_forbidden` (list)
- `texture_density` (low/med/high)
- `register_focus` (low/mid/high or mixed)
- `dynamic_ceiling` (max intensity)
- `notes`

This feeds the detailed Arrangement engine (08).

---

## 9. CUE ARC (STRUCTURE)

### 9.1 CUE_ARC (required fields)
- `segments` (list of ARC_SEGMENT)
- `transition_rules` (how to move between segments)
- `loopability` (bool; if bed cue)
- `exit_points` (list; time refs)

### 9.2 ARC_SEGMENT (required)
- `seg_id`
- `label` (intro/build/peak/release/outro)
- `time_range_ref` (or duration percent)
- `intensity_target` (0–10)
- `texture_target` (low/med/high)
- `notes`

Hard rule:
- climax cues must have a peak segment.

---

## 10. SYNC PLAN (EDIT COUPLING)

### 10.1 SYNC_PLAN (required fields)
- `sync_hooks` (list)
- `cut_safe_points` (list)
- `hit_points` (list; optional)
- `silence_windows` (list; optional)
- `notes`

Hard rule:
- if editing_hooks_ref exists, sync_plan must map to it.

---

## 11. STEM PLAN (DELIVERABLES)

### 11.1 STEM_PLAN (required fields)
- `stems` (list)
  - MAIN
  - DRUMS
  - BASS
  - HARMONY
  - MELODY
  - PADS
  - FX
  - ALT_MINIMAL
- `mute_safe_policy` (what can be muted without breaking)
- `export_notes`

Hard rule:
- at least MAIN + ALT_MINIMAL must exist for edit flexibility.

---

## 12. DELIVERY PROFILE

### 12.1 DELIVERY_PROFILE (required fields)
- `format_ref` (wav/mp3; conceptual)
- `sample_rate_ref` (conceptual)
- `loudness_policy_ref` (must align with 10.08 policy)
- `file_naming_policy` (optional)
- `version_tagging_policy` (required)

---

## 13. QA GATES

### 13.1 QA_GATES (required fields)
- `continuity_gate` (motif identity preserved)
- `tone_gate` (matches tone profile)
- `editability_gate` (cut points exist)
- `stem_gate` (required stems exist)
- `duration_gate` (within tolerance)
- `fatigue_gate` (no constant max intensity unless intended)

Verdict constraints:
- continuity_gate fail → INVALID (HIGH/CRITICAL)
- stem_gate fail → PARTIAL/INVALID depending on usage

---

## 14. REPAIR PLAN (MANDATORY)

### 14.1 REPAIR_PLAN (required fields)
Map failures to actions:
- tone mismatch → adjust harmonic_color + texture_density
- too busy → reduce texture_density + widen silence windows
- no edit points → add cut_safe_points + exit_points
- motif drift → lock motif identity + reduce variation_budget
- duration off → time-compress/restructure segments
- fatigue → lower dynamic_ceiling + add release segments

Must include:
- `max_revision_cycles`
- `recheck_gates`

---

## 15. CORE OPERATIONS

- OP_01: INGEST_REQUEST
- OP_02: VALIDATE_REQUIRED_INPUTS
- OP_03: SELECT_CUE_TYPE_AND_PURPOSE
- OP_04: APPLY_TONE_AND_GENRE_CONSTRAINTS
- OP_05: BUILD_MOTIF_PLAN
- OP_06: SET_TEMPO_METER_HARMONIC_COLOR
- OP_07: BUILD_ARRANGEMENT_CONSTRAINTS
- OP_08: BUILD_CUE_ARC
- OP_09: BUILD_SYNC_PLAN
- OP_10: BUILD_STEM_PLAN
- OP_11: BUILD_DELIVERY_PROFILE
- OP_12: BUILD_QA_GATES
- OP_13: BUILD_REPAIR_PLAN
- OP_14: EMIT_MUSIC_CUE_BLUEPRINT

---

## 16. FAILURE CONDITIONS (ENGINE)

CRITICAL:
- continuity_anchors_ref missing
- cue_type invalid
- duration_target missing
- tone_profile_ref missing

Reaction:
- reject request (fail-closed)
- request missing refs

---

## 17. NON-GOALS
- does not mix/master
- does not fully specify harmony/melody/rhythm (delegated engines)
- does not produce final rendered audio by itself

---

## 18. FINAL STATEMENT

Composition is architecture.
A cue without continuity locks is just noise with tempo.

---

**STATUS:** Music Composition Engine v1.0  
**REALM:** ACTIVE
