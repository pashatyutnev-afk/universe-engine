# 💡 LIGHTING ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · PRODUCTION ENGINE · LIGHT LOGIC · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 04__LIGHTING_ENG.md
- ENGINE_ID: L3-PROD-LIGHTING-ENGINE-004
- UID: UE.ENT.ENG.PROD.LIGHTING
- NAME: Lighting Engine
- CLASS: Knowledge Production Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (mood + continuity)
- EDITABLE: true

### ABSOLUTE RULE
> Lighting carries mood. If mood lighting drifts, the scene lies.

---

## 1. PURPOSE

Lighting Engine defines **how scenes are lit**:
- key/fill/rim logic (or practicals for doc style)
- contrast ratios and exposure behavior
- color temperature strategy
- shadow softness policy
- separation and depth support (coupled to composition)
- continuity anchors (light direction, key intensity bands)
- forbidden lighting drift patterns

It produces:
- **LIGHTING_SPEC**
- lighting templates for scenes/shots and downstream generation prompts

This engine prevents “random lighting per frame”.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define lighting style mode (filmic/doc/stylized)
- Define key/fill/rim setup logic
- Define contrast and exposure policy
- Define color temperature and practicals strategy
- Define shadow and highlight behavior bounds
- Define subject separation requirements
- Define continuity anchors across shots/episodes
- Emit constraints for image/video generation and grading

### OUT-OF-SCOPE (FORBIDDEN)
- Composition choices (Composition Engine)
- Camera lens/movement plan (Camera Engine)
- Art style selection (Art Style Engine)
- Writing prompts (Gen engines do)
- Changing canon facts

---

## 3. LIGHTING SPEC MODEL

### 3.1 Output — LIGHTING_SPEC (required fields)
- `ls_id`
- `target_medium` = IMAGE | VIDEO
- `lighting_mode` = FILMIC | NATURALISTIC | DOCUMENTARY | STYLIZED | HYBRID_CONTROLLED
- `mood_coupling` (required)
- `key_fill_rim_model` (required)
- `contrast_exposure_policy` (required)
- `color_temperature_policy` (required)
- `shadow_policy` (required)
- `highlight_policy` (required)
- `separation_requirements` (required)
- `continuity_anchors` (required)
- `negative_constraints` (required)
- `integrity_report` (issues + fixes)
- `trace_id` (optional)

Missing any required field → REJECT.

---

## 4. MOOD COUPLING

### 4.1 MOOD_COUPLING (required fields)
- `tone_profile_ref` (required)
- `mood_curve_ref` (optional)
- `allowed_mood_shifts` (bounded list)
- `forbidden_mood_shifts` (e.g., warm→cold flip without story reason)
- `mood_to_light_mapping` (rules)

Hard rule:
- lighting cannot contradict tone/mood without explicit “contrast intent” flag.

---

## 5. KEY/FILL/RIM MODEL

### 5.1 KEY_FILL_RIM_MODEL (required fields)
- `key_light_policy` (direction + softness + intensity band)
- `fill_light_policy` (ratio bounds)
- `rim_or_separation_policy` (allowed + limits)
- `practicals_policy` (allowed sources: lamps, screens, fire, neon)
- `source_motivation_rule` (every major light must have motivation, unless stylized mode)
- `notes`

Hard rule:
- if lighting_mode is NATURALISTIC/DOCUMENTARY, source motivation is mandatory.

---

## 6. CONTRAST & EXPOSURE POLICY

### 6.1 CONTRAST_EXPOSURE_POLICY (required fields)
- `contrast_ratio_target` (conceptual: low/med/high + bounds)
- `exposure_bias` = LOW_KEY | NORMAL | HIGH_KEY
- `black_floor_policy` (crushed blacks allowed? limits)
- `highlight_rolloff_policy` (filmic rolloff vs hard clip)
- `dynamic_range_policy` (keep details in faces/primary)
- `notes`

Hard rule:
- primary subject readability must survive exposure choices.

---

## 7. COLOR TEMPERATURE POLICY

### 7.1 COLOR_TEMPERATURE_POLICY (required fields)
- `temp_mode` = WARM | COOL | NEUTRAL | MIXED_MOTIVATED
- `key_temp_band` (conceptual)
- `fill_temp_band` (conceptual)
- `mixed_light_rules` (when allowed)
- `forbidden_temp_patterns` (random RGB lighting, neon spill unless intended)
- `notes`

Hard rule:
- if MIXED_MOTIVATED, each temp must be tied to a plausible source.

---

## 8. SHADOW POLICY

### 8.1 SHADOW_POLICY (required fields)
- `shadow_softness` = SOFT | MEDIUM | HARD | VARIABLE_CONTROLLED
- `shadow_detail_requirement` (retain detail? bounds)
- `forbidden_shadow_artifacts` (muddy faces, noisy blotches)
- `notes`

---

## 9. HIGHLIGHT POLICY

### 9.1 HIGHLIGHT_POLICY (required fields)
- `specular_policy` (controlled/allowed/forbidden)
- `bloom_policy` (none/subtle/stylized + bounds)
- `hotspot_policy` (no blown faces)
- `notes`

Hard rule:
- blown highlights on primary face/subject → INVALID unless horror/overexposure intent is declared and gated.

---

## 10. SEPARATION REQUIREMENTS

### 10.1 SEPARATION_REQUIREMENTS (required fields)
- `subject_background_separation` (required: yes)
- `allowed_methods` (rim, contrast, background falloff, color split)
- `minimum_separation_gate` (thumbnail/read test)
- `forbidden_merges` (primary merges into BG)
- `notes`

Couples with silhouette gate from Composition Engine.

---

## 11. CONTINUITY ANCHORS

### 11.1 CONTINUITY_ANCHORS (required fields)
- `key_direction_lock` (e.g., “key from screen-left”)
- `intensity_band_lock` (bounded)
- `temp_band_lock` (bounded)
- `shadow_softness_lock` (bounded)
- `scene_to_scene_variation_budget` (0–10)
- `episode_or_set_lock_rules` (if series)
- `notes`

Hard rule:
- anchors must be declared for multi-shot sequences. No anchors → PARTIAL/INVALID.

---

## 12. NEGATIVE CONSTRAINTS

### 12.1 NEGATIVE_CONSTRAINTS (required fields)
- `forbidden_lighting_drift` (e.g., day→night look mid-scene)
- `forbidden_color_casts` (green skin, magenta shadows unless stylized)
- `forbidden_noise_patterns` (banding, blotchy shadows)
- `forbidden_fake_rim` (halo artifacts)
- `notes`

---

## 13. INPUT ARTIFACTS

### 13.1 INPUT — LIGHTING_REQUEST
**REQUIRED FIELDS**
- `l_req_id`
- `timestamp`
- `visual_composition_spec_ref` (required)
- `camera_cinematography_spec_ref` (required)
- `art_style_spec_ref` (required)
- `tone_profile_ref` (required)
- `platform_constraints_ref` (required)
- `target_medium` (required)
- `constraints_refs` (required)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 14. OUTPUT ARTIFACTS

### 14.1 OUTPUT — LIGHTING_SPEC
(see model above)

### 14.2 OUTPUT — LIGHTING_VERDICT
- `l_req_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 15. CORE OPERATIONS

- OP_01: INGEST_COMPOSITION_CAMERA_STYLE_TONE_PLATFORM
- OP_02: SELECT_LIGHTING_MODE
- OP_03: DEFINE_MOOD_COUPLING_RULES
- OP_04: DEFINE_KEY_FILL_RIM_MODEL
- OP_05: DEFINE_CONTRAST_EXPOSURE_POLICY
- OP_06: DEFINE_COLOR_TEMPERATURE_POLICY
- OP_07: DEFINE_SHADOW_POLICY
- OP_08: DEFINE_HIGHLIGHT_POLICY
- OP_09: DEFINE_SEPARATION_REQUIREMENTS
- OP_10: DEFINE_CONTINUITY_ANCHORS
- OP_11: DEFINE_NEGATIVE_CONSTRAINTS
- OP_12: RUN_INTEGRITY_CHECKS (readability + drift)
- OP_13: EMIT_LIGHTING_SPEC

---

## 16. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- mood contradictions without declared intent
- primary subject unreadable due to exposure/contrast
- continuity anchors missing in multi-shot contexts
- temp drift without motivation
- forbidden artifacts (banding/blotchy shadows/halo rims)

Reaction:
- Verdict INVALID (CRITICAL)
- Emit repair plan:
  - lock key direction + temp
  - normalize exposure bands
  - increase separation
  - reduce bloom/specular
  - simplify mixed lighting

---

## 17. TRACE RULES

- trace_id optional unless pipeline requires traced execution
- if present, propagate into generation spec and grading

---

## 18. NON-GOALS
- Does not choose composition
- Does not choose camera
- Does not choose style
- Does not write prompts

---

## 19. FINAL STATEMENT

Lighting is emotional truth.
Lock the mood, then sculpt the frame.

---

**STATUS:** Lighting Engine v1.0  
**REALM:** ACTIVE
