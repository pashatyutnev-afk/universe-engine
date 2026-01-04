# 🎥 CAMERA & CINEMATOGRAPHY ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · PRODUCTION ENGINE · SHOT LOGIC · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 03__CAMERA_CINEMATOGRAPHY_ENG.md
- ENGINE_ID: L3-PROD-CAMERA-CINEMATOGRAPHY-ENGINE-003
- UID: UE.ENT.ENG.PROD.CAMERA_CINEMATOGRAPHY
- NAME: Camera & Cinematography Engine
- CLASS: Knowledge Production Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (axis + readability)
- EDITABLE: true

### ABSOLUTE RULE
> If the camera breaks axis without intent, the viewer is lost.

---

## 1. PURPOSE

Camera & Cinematography Engine defines **how the viewer sees**:
- shot types and shot list policies
- lens and field-of-view rules
- camera height/angle intent
- movement rules (static vs motion)
- focus and depth-of-field constraints
- continuity constraints (180° axis, screen direction, match cuts)

It produces:
- **CAMERA_CINEMATOGRAPHY_SPEC**
- shot templates and constraints for video/image generation pipelines

This engine prevents disorientation and “random cinematic language”.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define shot language (WS/MS/CU/ECU, etc.)
- Define lens family and focal ranges (conceptual)
- Define camera height/angle policies
- Define movement grammar (pan/tilt/dolly/handheld)
- Define focus/DOF constraints (coupled with composition + style)
- Define axis rules and match logic for sequences
- Define coverage requirements (what shots must exist per scene type)
- Emit spec for lighting + generation + editing engines

### OUT-OF-SCOPE (FORBIDDEN)
- Choosing art style (Art Style Engine)
- Choosing composition hierarchy (Composition Engine)
- Choosing lighting plan (Lighting Engine)
- Writing prompts or scripts
- Changing canon facts

---

## 3. CAMERA SPEC MODEL

### 3.1 Output — CAMERA_CINEMATOGRAPHY_SPEC (required fields)
- `ccs_id`
- `target_medium` = IMAGE | VIDEO
- `aspect_ratio` (required)
- `camera_language_mode` = CINEMATIC | DOCUMENTARY | GAMEPLAY | GRAPHIC
- `shot_type_policy` (required)
- `lens_policy` (required)
- `angle_height_policy` (required)
- `movement_policy` (required)
- `focus_dof_policy` (required)
- `coverage_rules` (required)
- `continuity_axis_rules` (required)
- `transition_match_rules` (required)
- `format_overrides` (optional)
- `integrity_report` (issues + fixes)
- `trace_id` (optional)

Missing any required field → REJECT.

---

## 4. SHOT TYPE POLICY

### 4.1 SHOT_TYPE_POLICY (required fields)
- `allowed_shots` (list: WS, WIDE, MS, MCU, CU, ECU, POV, OTS, INSERT)
- `preferred_shots_by_context` (map: dialogue/action/reveal/worldbuild)
- `forbidden_shots` (optional)
- `shot_frequency_guidance` (for video)
- `thumbnail_read_priority` (for image/shorts)
- `notes`

Hard rule:
- every scene type must have at least one readable establishing frame (unless intentional disorientation is declared and gated).

---

## 5. LENS POLICY

### 5.1 LENS_POLICY (required fields)
- `lens_family` = NATURAL | WIDE_BIASED | TELE_BIASED | ANAMORPHIC_STYLE | MIXED_CONTROLLED
- `focal_range_mm_equiv` (min/max conceptual; e.g., 18–85)
- `distortion_policy` (none/controlled/expressive)
- `compression_policy` (low/medium/high)
- `bokeh_policy` (subtle/filmic/stylized; bounded)
- `forbidden_lens_moves` (e.g., ultra-wide faces unless horror)
- `notes`

Hard rule:
- lens behavior must not violate style contract (no random distortion if realism is locked).

---

## 6. ANGLE & HEIGHT POLICY

### 6.1 ANGLE_HEIGHT_POLICY (required fields)
- `camera_height_modes` (eye/low/high/overhead)
- `angle_modes` (level/down/up/dutch allowed?)
- `intent_mapping` (map: power/fear/intimacy/awe)
- `horizon_policy` (level by default; tilt only by rule)
- `forbidden_angles` (optional)
- `notes`

Hard rule:
- dutch tilt must be explicitly allowed; otherwise forbidden.

---

## 7. MOVEMENT POLICY

### 7.1 MOVEMENT_POLICY (required fields)
- `movement_mode` = STATIC_BIASED | MOTION_BIASED | MIXED_CONTROLLED
- `allowed_moves` (pan, tilt, dolly, truck, crane, handheld, gimbal)
- `movement_intent_rules` (when movement is justified)
- `max_motion_density` (how often motion occurs)
- `stabilization_policy` (stable/handheld controlled)
- `forbidden_moves` (whip pans unless style allows)
- `notes`

Hard rule:
- movement must carry meaning (reveal, follow, escalate) or it is cut.

---

## 8. FOCUS & DEPTH-OF-FIELD POLICY

### 8.1 FOCUS_DOF_POLICY (required fields)
- `dof_mode` = DEEP | SHALLOW | VARIABLE_CONTROLLED
- `focus_priority` (primary subject first)
- `rack_focus_allowed` (bool)
- `rack_focus_rules` (when allowed)
- `forbidden_focus_patterns` (hunting, accidental blur)
- `notes`

Hard rule:
- primary subject must not be unintentionally out of focus.

---

## 9. COVERAGE RULES (SCENE COVERAGE)

### 9.1 COVERAGE_RULES (required fields)
- `dialogue_coverage_minimum` (e.g., OTS L/R + CU)
- `action_coverage_minimum` (wide geography + inserts)
- `reveal_coverage_minimum` (setup → reveal → reaction)
- `worldbuild_coverage_minimum` (establishing + detail insert)
- `notes`

If coverage minimum is not satisfiable under runtime/format → PARTIAL with repair plan.

---

## 10. CONTINUITY AXIS RULES (180°)

### 10.1 CONTINUITY_AXIS_RULES (required fields)
- `axis_lock_policy` (lock once established)
- `screen_direction_policy` (left-right consistency)
- `crossing_axis_allowed` (bool)
- `axis_crossing_gate` (if allowed: must have bridge shot)
- `geography_clarity_requirement` (must show space before cuts)
- `notes`

Hard rule:
- if crossing_axis_allowed = true, must specify the bridge method (neutral shot, camera move, re-establish).

---

## 11. TRANSITION & MATCH RULES

### 11.1 TRANSITION_MATCH_RULES (required fields)
- `match_cut_types_allowed` (action match, eyeline match, graphic match)
- `forbidden_transitions` (random jump cuts in realism)
- `cut_on_motion_policy` (optional)
- `audio_pre-lap_allowed` (optional)
- `notes`

---

## 12. FORMAT OVERRIDES (OPTIONAL)

Examples:
- SHORT: tighter lens, center-weighted, fewer axis changes
- YOUTUBE: frequent re-hooks, cutaway policy (B-roll inserts)
- SERIES: consistent lens family per season
- GAME: gameplay camera constraints + UI safe zones

---

## 13. INPUT ARTIFACTS

### 13.1 INPUT — CAMERA_CINEMATOGRAPHY_REQUEST
**REQUIRED FIELDS**
- `cc_req_id`
- `timestamp`
- `visual_composition_spec_ref` (required)
- `art_style_spec_ref` (required)
- `tone_profile_ref` (required)
- `platform_constraints_ref` (required)
- `target_medium` (required)
- `constraints_refs` (required)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 14. OUTPUT ARTIFACTS

### 14.1 OUTPUT — CAMERA_CINEMATOGRAPHY_SPEC
(see model above)

### 14.2 OUTPUT — CAMERA_CINEMATOGRAPHY_VERDICT
- `cc_req_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 15. CORE OPERATIONS

- OP_01: INGEST_COMPOSITION_STYLE_TONE_PLATFORM
- OP_02: SET_CAMERA_LANGUAGE_MODE
- OP_03: DEFINE_SHOT_TYPE_POLICY
- OP_04: DEFINE_LENS_POLICY
- OP_05: DEFINE_ANGLE_HEIGHT_POLICY
- OP_06: DEFINE_MOVEMENT_POLICY
- OP_07: DEFINE_FOCUS_DOF_POLICY
- OP_08: DEFINE_COVERAGE_RULES
- OP_09: DEFINE_CONTINUITY_AXIS_RULES
- OP_10: DEFINE_TRANSITION_MATCH_RULES
- OP_11: RUN_INTEGRITY_CHECKS (axis, focus, style)
- OP_12: EMIT_CAMERA_CINEMATOGRAPHY_SPEC

---

## 16. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- axis rules missing for multi-shot sequences
- crossing axis without bridge logic
- focus policy allows primary blur
- lens policy violates style contract
- movement without intent (noise motion)

Reaction:
- Verdict INVALID (CRITICAL)
- Emit repair plan:
  - lock axis + screen direction
  - add bridge shot rule
  - constrain lens family
  - reduce motion density
  - enforce focus priority

---

## 17. TRACE RULES

- trace_id optional unless pipeline requires traced execution
- if present, propagate into lighting + editing + generation specs

---

## 18. NON-GOALS
- Does not pick style
- Does not pick composition
- Does not pick lighting
- Does not write prompts

---

## 19. FINAL STATEMENT

Camera is the viewer’s body.
Keep the axis — and the story stays inside the head.

---

**STATUS:** Camera & Cinematography Engine v1.0  
**REALM:** ACTIVE
