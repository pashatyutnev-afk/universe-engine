# 🖼️ IMAGE GENERATION ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · PRODUCTION ENGINE · PROMPT SPEC CONTRACT · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 05__IMAGE_GENERATION_ENG.md
- ENGINE_ID: L3-PROD-IMAGE-GENERATION-ENGINE-005
- UID: UE.ENT.ENG.PROD.IMAGE_GENERATION
- NAME: Image Generation Engine
- CLASS: Knowledge Production Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (spec completeness)
- EDITABLE: true

### ABSOLUTE RULE
> No generator can produce consistency from vague input. If the spec is incomplete — generation is forbidden.

---

## 1. PURPOSE

Image Generation Engine converts upstream production specs into a **generator-ready prompt specification**:
- structured prompt blocks (positive/negative)
- subject/scene constraints
- composition + camera + lighting + style binding
- parameter policies (seed, variation, CFG-like guidance conceptual)
- reference image handling (if available)
- output deliverable declaration
- QA gates for artifacts and continuity

It produces:
- **IMAGE_GENERATION_SPEC**
- optional **PROMPT_BLOCKS** (ready to paste into tools)

This engine prevents “prompt spaghetti” and style drift.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Bind Composition/Camera/Lighting/Style into a single generation spec
- Define prompt blocks and ordering
- Define negative constraints and artifact prevention
- Define parameter policy (seed reuse, variation budget)
- Define reference handling policy (if refs exist)
- Define deliverable spec (count, aspect, resolution)
- Define QA gates (hands, faces, text artifacts, watermark)
- Emit generator-ready instructions

### OUT-OF-SCOPE (FORBIDDEN)
- Changing canon facts
- Inventing new entities unless explicitly allowed by request
- Video generation (handled by Video Generation Engine)
- Editing/montage (Editing Engine)

---

## 3. IMAGE GENERATION SPEC MODEL

### 3.1 Output — IMAGE_GENERATION_SPEC (required fields)
- `igs_id`
- `target_model_family` (optional; tool-agnostic by default)
- `deliverable` (required)
- `scene_subject_spec` (required)
- `composition_binding_ref` (required)
- `camera_binding_ref` (required)
- `lighting_binding_ref` (required)
- `style_binding_ref` (required)
- `prompt_blocks` (required)
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
- `image_count` (int)
- `aspect_ratio` (required)
- `resolution_target` (required)
- `background_policy` (solid/scene/transparent if supported)
- `output_format` (png/jpg/webp; conceptual ok)
- `naming_policy` (optional)

Hard rule:
- aspect_ratio must match upstream platform constraints.

---

## 5. SCENE & SUBJECT SPEC

### 5.1 SCENE_SUBJECT_SPEC (required fields)
- `subject_list` (who/what appears)
- `environment` (where)
- `action_state` (what is happening)
- `time_weather` (optional)
- `must_show` (list)
- `must_not_show` (list)
- `safety_content_limits` (no disallowed content)
- `canon_lock_refs` (if canonical entities)

Hard rule:
- must_show must be satisfiable with composition/camera constraints.

---

## 6. BINDINGS (UPSTREAM SPECS)

Required bindings:
- `composition_binding_ref` → VISUAL_COMPOSITION_SPEC
- `camera_binding_ref` → CAMERA_CINEMATOGRAPHY_SPEC
- `lighting_binding_ref` → LIGHTING_SPEC
- `style_binding_ref` → ART_STYLE_SPEC

Hard rule:
- if any binding missing → INVALID (fail-closed).

---

## 7. PROMPT BLOCKS (STRUCTURED)

### 7.1 PROMPT_BLOCKS (required fields)
- `positive_core` (required)
- `positive_style` (required)
- `positive_camera` (required)
- `positive_lighting` (required)
- `positive_composition` (required)
- `positive_quality` (optional)
- `negative_core` (required)
- `negative_artifacts` (required)
- `negative_style_drift` (required)
- `ordering_rule` (required: concatenation order)

Hard rules:
- negative blocks must include artifact avoidance.
- if text is not intended, explicitly forbid text/logos/watermarks.

---

## 8. PARAMETER POLICY

### 8.1 PARAMETER_POLICY (required fields)
- `seed_policy` = FIXED | VARIED | CONTROLLED_SET
- `seed_reuse_rules` (when to reuse)
- `variation_budget` (0–10)
- `detail_level_target` (0–10)
- `guidance_strength` (conceptual low/med/high)
- `steps_time_budget` (conceptual)
- `batching_rules` (optional)

Hard rule:
- variation_budget must not violate style continuity anchors.

---

## 9. REFERENCE POLICY

### 9.1 REFERENCE_POLICY (required fields)
- `use_references` (bool)
- `reference_types_allowed` (character/style/location)
- `reference_priority` (what refs override)
- `reference_conflict_rule` (if refs conflict with canon/spec)
- `reference_safety_rule` (no identity claims; tool-safe)
- `notes`

Hard rule:
- references cannot override canon locks unless explicitly permitted.

---

## 10. NEGATIVE CONSTRAINTS (HARD)

### 10.1 NEGATIVE_CONSTRAINTS (required fields)
- `forbid_text` (bool; default true unless needed)
- `forbid_watermarks` (true)
- `forbid_ui_overlays` (true unless requested)
- `forbid_anatomy_errors` (true)
- `forbid_face_warp` (true)
- `forbid_logo_mutation` (true)
- `style_drift_blacklist` (list)
- `notes`

---

## 11. QA GATES

### 11.1 QA_GATES (required fields)
- `readability_gate` (thumbnail test)
- `silhouette_gate` (from composition)
- `artifact_gate` (hands/face/limbs/text/watermark)
- `continuity_gate` (anchors preserved)
- `exposure_gate` (primary readable)
- `prompt_spec_gate` (all required blocks present)

Verdict rules:
- if artifact_gate fails at HIGH severity → INVALID.
- if continuity_gate fails → PARTIAL/INVALID depending on severity.

---

## 12. RETRY & REPAIR PLAN (MANDATORY)

### 12.1 RETRY_REPAIR_PLAN (required fields)
- `retry_count_max` (int)
- `repair_actions_by_failure` (map)
  - anatomy_errors → strengthen negative + simplify pose
  - face_warp → tighter face constraints + reduce wide lens
  - clutter → reduce objects + increase negative space
  - style_drift → lock style tokens + reduce variation
  - lighting_drift → lock temp + key direction
- `escalation_rule` (when to stop and redesign spec)

Hard rule:
- if repeated failure occurs, do not brute force; redesign spec.

---

## 13. INPUT ARTIFACTS

### 13.1 INPUT — IMAGE_GENERATION_REQUEST
**REQUIRED FIELDS**
- `ig_req_id`
- `timestamp`
- `scene_subject_spec` (required)
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

## 14. OUTPUT ARTIFACTS

### 14.1 OUTPUT — IMAGE_GENERATION_SPEC
(see model above)

### 14.2 OUTPUT — IMAGE_GENERATION_VERDICT
- `ig_req_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 15. CORE OPERATIONS

- OP_01: INGEST_SCENE_SUBJECT_AND_UPSTREAM_SPECS
- OP_02: VALIDATE_BINDINGS (fail-closed if missing)
- OP_03: BUILD_PROMPT_BLOCKS (positive + negative)
- OP_04: SET_PARAMETER_POLICY (seed/variation/guidance)
- OP_05: SET_REFERENCE_POLICY (if refs)
- OP_06: DEFINE_DELIVERABLE (count/aspect/resolution)
- OP_07: DEFINE_QA_GATES
- OP_08: DEFINE_RETRY_REPAIR_PLAN
- OP_09: RUN_SPEC_COMPLETENESS_CHECK
- OP_10: EMIT_IMAGE_GENERATION_SPEC

---

## 16. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- missing any upstream binding
- missing negative blocks for artifacts
- deliverable conflicts with platform constraints
- no retry/repair plan
- references conflict with canon locks without rule

Reaction:
- Verdict INVALID (CRITICAL)
- Emit repair plan:
  - add missing bindings
  - add negative artifact constraints
  - lock aspect/resolution
  - reduce variation budget
  - resolve reference conflicts

---

## 17. TRACE RULES

- trace_id optional unless pipeline requires traced execution
- if present, propagate into production orchestrator + audit log

---

## 18. NON-GOALS
- Does not generate images itself
- Does not edit images
- Does not generate video
- Does not change canon

---

## 19. FINAL STATEMENT

Generation is not magic — it is compliance.
A good image is a prompt spec that leaves no ambiguity.

---

**STATUS:** Image Generation Engine v1.0  
**REALM:** ACTIVE
