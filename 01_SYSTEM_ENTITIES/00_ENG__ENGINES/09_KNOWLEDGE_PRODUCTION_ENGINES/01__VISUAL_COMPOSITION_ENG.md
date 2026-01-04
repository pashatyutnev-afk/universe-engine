# 🧩 VISUAL COMPOSITION ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · PRODUCTION ENGINE · FRAME LOGIC · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 01__VISUAL_COMPOSITION_ENG.md
- ENGINE_ID: L3-PROD-VISUAL-COMPOSITION-ENGINE-001
- UID: UE.ENT.ENG.PROD.VISUAL_COMPOSITION
- NAME: Visual Composition Engine
- CLASS: Knowledge Production Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (composition clarity)
- EDITABLE: true

### ABSOLUTE RULE
> If the viewer can’t read the frame in one second, the frame failed.

---

## 1. PURPOSE

Visual Composition Engine defines **how images/frames are built**:
- focal hierarchy (primary/secondary/tertiary)
- framing and subject placement
- depth and layering
- negative space control
- silhouette readability
- motion guidance (for video frames)
- continuity rules (what must stay stable across shots)

It produces:
- **VISUAL_COMPOSITION_SPEC**
- composition templates per scene/shot type

This engine prevents messy, unreadable visuals.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define focal hierarchy and eye-path
- Define framing rules (rule of thirds, center, symmetry, etc.)
- Define depth strategy (foreground/mid/background)
- Define scale and perspective intent
- Define negative space budget
- Define shot composition templates per format (short/series/youtube/game)
- Define continuity constraints (screen direction, key props placement)
- Emit constraints for camera + lighting + generation specs

### OUT-OF-SCOPE (FORBIDDEN)
- Choose art style (Art Style Engine)
- Choose lighting plan (Lighting Engine)
- Decide plot content
- Write prompts directly (Image/Video Generation Engine owns final prompt spec)

---

## 3. COMPOSITION SPEC MODEL

### 3.1 Output — VISUAL_COMPOSITION_SPEC (required fields)
- `vcs_id`
- `target_medium` = IMAGE | VIDEO
- `aspect_ratio` (required)
- `resolution_target` (required)
- `composition_mode` = CLASSIC | CINEMATIC | GRAPHIC | DOCUMENTARY | GAME_UI
- `focal_hierarchy` (required)
- `framing_rules` (required)
- `depth_plan` (required)
- `negative_space_budget` (required)
- `silhouette_gate` (required)
- `eye_path_rules` (required)
- `continuity_rules` (required)
- `format_overrides` (optional)
- `integrity_report` (issues + fixes)
- `trace_id` (optional)

Missing any required field → REJECT.

---

## 4. FOCAL HIERARCHY

### 4.1 FOCAL_HIERARCHY object (required fields)
- `primary_subject` (what must be read first)
- `secondary_subjects` (list)
- `tertiary_details` (list, optional)
- `contrast_strategy` (scale/light/color/texture; symbolic ok)
- `read_order` (ordered list)
- `do_not_compete_rules` (what must NOT compete with primary)

Hard rule:
- if secondary competes with primary → INVALID unless explicitly intended (rare).

---

## 5. FRAMING RULES

### 5.1 FRAMING_RULESET (required fields)
- `rule_set` (thirds / center / symmetry / leading lines / dutch tilt etc.)
- `subject_placement` (coordinates or description)
- `headroom_lookroom_rules` (if character present)
- `camera_height_intent` (eye/low/high)
- `horizon_policy` (level/tilt allowed)
- `crop_safety` (platform UI safe zones)

Hard rule:
- subject must not be cut by platform UI overlays.

---

## 6. DEPTH PLAN

### 6.1 DEPTH_PLAN object (required fields)
- `layering` (FG/MG/BG defined)
- `separation_method` (focus/contrast/lighting)
- `scale_cues` (objects that show size)
- `atmospheric_depth_allowed` (fog/haze; optional)
- `background_noise_budget` (LOW/MEDIUM/HIGH)

Hard rule:
- background noise must not reduce readability of primary silhouette.

---

## 7. NEGATIVE SPACE BUDGET

### 7.1 NEGATIVE_SPACE_BUDGET (required fields)
- `ratio` (0.0–1.0)
- `purpose` (clarity / loneliness / awe / UI space)
- `placement` (where space lives)
- `forbidden_clutter_zones` (list)

---

## 8. SILHOUETTE GATE (HARD)

### 8.1 SILHOUETTE_GATE (required fields)
- `must_be_readable` (bool = true by default)
- `readability_distance_test` (conceptual: thumbnail test)
- `forbidden_merges` (primary merges with background)
- `repair_actions` (increase separation, simplify BG, change angle)

If silhouette unreadable → INVALID.

---

## 9. EYE PATH RULES

### 9.1 EYE_PATH_RULES (required fields)
- `entry_point` (where viewer starts)
- `path_devices` (leading lines, contrast, motion, gaze)
- `exit_point` (optional)
- `loop_policy` (return to primary)
- `avoid_distraction_zones` (list)

Hard rule:
- eye path must return to primary at least once in the read cycle.

---

## 10. CONTINUITY RULES

### 10.1 CONTINUITY_RULES (required fields)
- `screen_direction_policy` (left-right consistency)
- `prop_anchor_rules` (key objects stable)
- `costume_color_consistency` (if character)
- `location_landmarks` (what must remain)
- `shot_to_shot_variation_limits` (how much can change)

---

## 11. FORMAT OVERRIDES (OPTIONAL)

Examples:
- SHORTS: center-weighted subject + higher contrast for mobile
- YOUTUBE: clear mid-frame + space for captions
- SERIES: cinematic framing + consistent axis
- GAME: UI safe zones + gameplay readability

---

## 12. INPUT ARTIFACTS

### 12.1 INPUT — VISUAL_COMPOSITION_REQUEST
**REQUIRED FIELDS**
- `vc_req_id`
- `timestamp`
- `tone_profile_ref` (required)
- `mood_curve_ref` (optional)
- `atmosphere_layer_map_ref` (required)
- `platform_constraints_ref` (required)
- `target_medium` (required)
- `constraints_refs` (required)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 13. OUTPUT ARTIFACTS

### 13.1 OUTPUT — VISUAL_COMPOSITION_SPEC
(see model above)

### 13.2 OUTPUT — VISUAL_COMPOSITION_VERDICT
- `vc_req_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 14. CORE OPERATIONS

- OP_01: INGEST_TONE_ATMOSPHERE_PLATFORM_CONSTRAINTS
- OP_02: SET_TARGET_MEDIUM_ASPECT_RESOLUTION
- OP_03: DEFINE_FOCAL_HIERARCHY
- OP_04: DEFINE_FRAMING_RULES
- OP_05: DEFINE_DEPTH_PLAN
- OP_06: DEFINE_NEGATIVE_SPACE_BUDGET
- OP_07: APPLY_SILHOUETTE_GATE
- OP_08: DEFINE_EYE_PATH_RULES
- OP_09: DEFINE_CONTINUITY_RULES
- OP_10: RUN_INTEGRITY_CHECKS (thumbnail read)
- OP_11: EMIT_VISUAL_COMPOSITION_SPEC

---

## 15. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- silhouette unreadable
- focal competition unresolved
- framing violates UI safe zones
- background noise overload
- continuity rules missing for multi-shot contexts

Reaction:
- Verdict INVALID (CRITICAL)
- Emit repair plan:
  - simplify background
  - increase separation
  - reposition subject
  - enforce safe zones
  - lock continuity anchors

---

## 16. TRACE RULES

- trace_id optional unless pipeline requires traced execution
- if present, propagate into camera + lighting + generation specs

---

## 17. NON-GOALS
- Does not pick style or lighting
- Does not write prompts
- Does not change canon

---

## 18. FINAL STATEMENT

Composition is the grammar of images.
If the grammar is wrong, nothing you render will read.

---

**STATUS:** Visual Composition Engine v1.0  
**REALM:** ACTIVE
