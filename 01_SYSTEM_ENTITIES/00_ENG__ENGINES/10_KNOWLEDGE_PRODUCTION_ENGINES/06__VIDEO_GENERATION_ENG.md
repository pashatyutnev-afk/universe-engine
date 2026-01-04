# 🎞️ VIDEO GENERATION ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · PRODUCTION ENGINE · SHOT TIMELINE SPEC · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 06__VIDEO_GENERATION_ENG.md
- ENGINE_ID: L3-PROD-VIDEO-GENERATION-ENGINE-006
- UID: UE.ENT.ENG.PROD.VIDEO_GENERATION
- NAME: Video Generation Engine
- CLASS: Knowledge Production Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (temporal continuity)
- EDITABLE: true

### ABSOLUTE RULE
> Video is continuity over time. If continuity breaks, the viewer feels it instantly.

---

## 1. PURPOSE

Video Generation Engine converts production specs into a **generator-ready video specification**:
- shot timeline (sequence of shots with duration)
- per-shot composition/camera/lighting/style binding
- motion constraints (camera + subject)
- temporal continuity anchors (identity, props, direction)
- transitions and stabilization rules
- deliverable declaration (fps, duration, resolution, aspect)
- QA gates for temporal artifacts
- retry/repair plan (per failure mode)

It produces:
- **VIDEO_GENERATION_SPEC**
- optional **SHOT_PROMPT_BLOCKS** (tool-ready per shot)

This engine prevents “pretty frames that don’t match” across time.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define shot timeline and duration budgets
- Bind upstream specs into per-shot constraints
- Define motion language and limits
- Define temporal continuity anchors and variation budget
- Define transition policies
- Define deliverable parameters (fps, length, format)
- Define QA gates for temporal artifacts (flicker, morphing, drift)
- Define retry/repair plan and escalation rules

### OUT-OF-SCOPE (FORBIDDEN)
- Editing/montage decisions (Editing Engine)
- Sound design and music (Sound & Music Engine)
- Changing canon facts
- Infinite resampling without redesign (must escalate)

---

## 3. VIDEO GENERATION SPEC MODEL

### 3.1 Output — VIDEO_GENERATION_SPEC (required fields)
- `vgs_id`
- `deliverable` (required)
- `timeline` (required)
- `global_bindings` (required)
- `per_shot_bindings` (required)
- `motion_constraints` (required)
- `temporal_continuity_anchors` (required)
- `transition_policy` (required)
- `parameter_policy` (required)
- `reference_policy` (required)
- `negative_constraints` (required)
- `qa_gates` (required)
- `retry_repair_plan` (required)
- `integrity_report` (issues + fixes)
- `trace_id` (optional)

Missing any required field → REJECT.

---

## 4. DELIVERABLE

### 4.1 DELIVERABLE (required fields)
- `duration_seconds` (required)
- `fps` (required)
- `aspect_ratio` (required)
- `resolution_target` (required)
- `output_format` (mp4/mov; conceptual ok)
- `audio_track_expected` (bool; optional)
- `naming_policy` (optional)

Hard rule:
- duration + fps must be feasible for target platform constraints.

---

## 5. TIMELINE MODEL

### 5.1 TIMELINE (required fields)
- `shot_count` (int)
- `shots` (ordered list of SHOT_SPEC)
- `global_runtime_budget` (seconds)
- `max_shot_duration_seconds` (optional)
- `min_shot_duration_seconds` (optional)
- `cadence_rules` (required)

### 5.2 SHOT_SPEC (required fields)
- `shot_id`
- `duration_seconds`
- `shot_type` (WS/MS/CU/POV/INSERT etc.)
- `goal` (what the shot must communicate)
- `must_show` (list)
- `must_not_show` (list)
- `prompt_blocks_ref` (optional)
- `transition_out` (required)
- `notes`

Hard rule:
- each shot must have a goal and must_show items that are satisfiable.

---

## 6. GLOBAL BINDINGS

### 6.1 GLOBAL_BINDINGS (required fields)
- `visual_composition_spec_ref` (required)
- `camera_cinematography_spec_ref` (required)
- `lighting_spec_ref` (required)
- `art_style_spec_ref` (required)
- `tone_profile_ref` (required)
- `platform_constraints_ref` (required)

Hard rule:
- if any ref missing → INVALID (fail-closed).

---

## 7. PER-SHOT BINDINGS

### 7.1 PER_SHOT_BINDINGS (required fields)
- `shot_binding_overrides` (map: shot_id → overrides)
- `allowed_override_axes` (e.g., lens within range, exposure within band)
- `forbidden_override_axes` (style family, palette flips, axis breaks)
- `override_validation_rule` (must not violate anchors)

Hard rule:
- any override that breaks continuity anchors → INVALID.

---

## 8. MOTION CONSTRAINTS

### 8.1 MOTION_CONSTRAINTS (required fields)
- `camera_motion_policy` (static/mixed/handheld controlled)
- `allowed_camera_moves` (pan/tilt/dolly/truck/crane)
- `max_camera_motion_intensity` (0–10)
- `subject_motion_policy` (limited/medium/high)
- `max_subject_motion_intensity` (0–10)
- `stabilization_policy` (stable/controlled shake)
- `forbidden_motion_patterns` (shaky chaos, teleport jumps)
- `notes`

Hard rule:
- motion must not violate readability gates (primary stays readable).

---

## 9. TEMPORAL CONTINUITY ANCHORS (HARD)

### 9.1 TEMPORAL_CONTINUITY_ANCHORS (required fields)
- `identity_lock_rules` (characters/props stable)
- `wardrobe_palette_lock` (if characters)
- `symbol_logo_lock` (if any)
- `screen_direction_lock` (left-right consistency)
- `lighting_anchor_lock` (key direction/temp bands)
- `style_anchor_lock` (rendering cues stable)
- `variation_budget_over_time` (0–10)
- `forbidden_temporal_drift` (morphing faces, swapping objects)

Hard rule:
- if identity morphing is likely, tighten constraints or reduce motion complexity.

---

## 10. TRANSITION POLICY

### 10.1 TRANSITION_POLICY (required fields)
- `allowed_transitions` (cut, match cut, dissolve limited, whip only if allowed)
- `forbidden_transitions` (random jump across space without bridge)
- `transition_safety_rules` (no cut mid-reveal unless intended)
- `re-hook_rule` (what must happen after transition: new info/loop touch)

---

## 11. PARAMETER POLICY

### 11.1 PARAMETER_POLICY (required fields)
- `seed_policy` = FIXED | CONTROLLED_SET | VARIED
- `seed_lock_scope` (global/per-shot)
- `variation_budget` (0–10)
- `guidance_strength` (conceptual low/med/high)
- `steps_time_budget` (conceptual)
- `consistency_priority` (0–10)
- `notes`

Hard rule:
- if consistency_priority high, variation_budget must be low.

---

## 12. REFERENCE POLICY

### 12.1 REFERENCE_POLICY (required fields)
- `use_references` (bool)
- `reference_assets_refs` (optional)
- `reference_priority` (identity/style/location)
- `reference_conflict_rule` (spec wins unless explicit override)
- `notes`

Hard rule:
- references cannot override canon/anchors without declared permission.

---

## 13. NEGATIVE CONSTRAINTS

### 13.1 NEGATIVE_CONSTRAINTS (required fields)
- `forbid_watermarks` (true)
- `forbid_text` (true unless needed)
- `forbid_temporal_flicker` (true)
- `forbid_identity_morph` (true)
- `forbid_background_warp` (true)
- `forbid_frame_jitter` (true beyond stabilization policy)
- `notes`

---

## 14. QA GATES (TEMPORAL)

### 14.1 QA_GATES (required fields)
- `frame_readability_gate` (primary readable each shot)
- `temporal_stability_gate` (no flicker/morphing)
- `continuity_gate` (anchors preserved across shots)
- `axis_gate` (screen direction continuity)
- `artifact_gate` (hands/faces/text)
- `spec_completeness_gate` (all required fields)

Verdict rules:
- temporal_stability_gate fail at HIGH severity → INVALID.
- continuity_gate fail → PARTIAL/INVALID depending on scope.

---

## 15. RETRY & REPAIR PLAN (MANDATORY)

### 15.1 RETRY_REPAIR_PLAN (required fields)
- `retry_count_max` (int)
- `repair_actions_by_failure` (map)
  - flicker → reduce variation + lock lighting + simplify motion
  - identity_morph → tighten anchors + add references + reduce DOF extremes
  - background_warp → reduce camera motion + simplify background
  - jitter → stabilize + reduce handheld intensity
  - axis_confusion → lock axis + add geography establishing shot
- `escalation_rule` (stop brute force and redesign after N failures)

Hard rule:
- repeated failure triggers redesign, not infinite retries.

---

## 16. INPUT ARTIFACTS

### 16.1 INPUT — VIDEO_GENERATION_REQUEST
**REQUIRED FIELDS**
- `vg_req_id`
- `timestamp`
- `timeline_or_storyboard_ref` (required)
- `visual_composition_spec_ref` (required)
- `camera_cinematography_spec_ref` (required)
- `lighting_spec_ref` (required)
- `art_style_spec_ref` (required)
- `platform_constraints_ref` (required)
- `constraints_refs` (required)
- `reference_assets_refs` (optional)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 17. OUTPUT ARTIFACTS

### 17.1 OUTPUT — VIDEO_GENERATION_SPEC
(see model above)

### 17.2 OUTPUT — VIDEO_GENERATION_VERDICT
- `vg_req_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 18. CORE OPERATIONS

- OP_01: INGEST_TIMELINE_AND_UPSTREAM_SPECS
- OP_02: VALIDATE_GLOBAL_BINDINGS (fail-closed)
- OP_03: BUILD_SHOT_SPECS (goal + must_show)
- OP_04: DEFINE_MOTION_CONSTRAINTS
- OP_05: DEFINE_TEMPORAL_CONTINUITY_ANCHORS
- OP_06: DEFINE_TRANSITION_POLICY
- OP_07: SET_PARAMETER_POLICY (seed/variation/consistency)
- OP_08: SET_REFERENCE_POLICY
- OP_09: BUILD_NEGATIVE_CONSTRAINTS (temporal artifacts)
- OP_10: DEFINE_QA_GATES (temporal)
- OP_11: DEFINE_RETRY_REPAIR_PLAN
- OP_12: RUN_SPEC_COMPLETENESS_CHECK
- OP_13: EMIT_VIDEO_GENERATION_SPEC

---

## 19. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- missing bindings
- no continuity anchors
- motion exceeds stability capacity
- temporal artifact risk unmitigated
- retry plan missing
- deliverable conflicts with platform constraints

Reaction:
- Verdict INVALID (CRITICAL)
- Emit repair plan:
  - lock seeds + reduce variation
  - tighten anchors + add references
  - simplify motion/background
  - enforce axis + geography shot
  - redesign timeline if overloaded

---

## 20. TRACE RULES

- trace_id optional unless pipeline requires traced execution
- if present, propagate into audit log and editing plan

---

## 21. NON-GOALS
- Does not edit video
- Does not design sound
- Does not guarantee generator model capability
- Does not change canon

---

## 22. FINAL STATEMENT

A good video spec is continuity written down.
If it isn’t written, it won’t stay consistent.

---

**STATUS:** Video Generation Engine v1.0  
**REALM:** ACTIVE
