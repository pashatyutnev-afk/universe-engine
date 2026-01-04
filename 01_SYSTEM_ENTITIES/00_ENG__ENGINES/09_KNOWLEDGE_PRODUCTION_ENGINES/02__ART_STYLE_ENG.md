# 🎨 ART STYLE ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · PRODUCTION ENGINE · STYLE CONTRACT · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 02__ART_STYLE_ENG.md
- ENGINE_ID: L3-PROD-ART-STYLE-ENGINE-002
- UID: UE.ENT.ENG.PROD.ART_STYLE
- NAME: Art Style Engine
- CLASS: Knowledge Production Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (style continuity)
- EDITABLE: true

### ABSOLUTE RULE
> Style is a contract. If the contract changes between shots, the world breaks.

---

## 1. PURPOSE

Art Style Engine defines a **style contract** for image/video production:
- visual identity (look & feel)
- palette constraints and contrast behavior
- line/shape language (hard/soft, angular/organic)
- material/texture language
- realism level and stylization level
- negative style constraints (what must NOT appear)
- continuity anchors (what must stay stable across assets)

It produces:
- **ART_STYLE_SPEC**
- style tokens for downstream prompt/generation/editing

This engine prevents “random model aesthetic drift”.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define style contract and its invariants
- Define palette rules (temperature, saturation bounds)
- Define line/shape language and rendering cues
- Define texture/material rules (grain, gloss, roughness)
- Define realism/stylization slider
- Define forbidden artifacts and negative prompts
- Define continuity anchors (faces, symbols, uniforms, UI)
- Emit spec for camera/lighting/generation engines

### OUT-OF-SCOPE (FORBIDDEN)
- Composition decisions (Visual Composition Engine)
- Camera plan (Camera & Cinematography Engine)
- Lighting plan (Lighting Engine)
- Writing full prompts (Image/Video Gen engines do)
- Changing canon facts

---

## 3. ART STYLE SPEC MODEL

### 3.1 Output — ART_STYLE_SPEC (required fields)
- `ass_id`
- `target_medium` = IMAGE | VIDEO
- `style_family` = REALISM | CINEMATIC_REALISM | ANIME | ILLUSTRATION | 3D_RENDER | COMIC | DOCUMENTARY | HYBRID
- `stylization_level` (0–10, required)
- `realism_level` (0–10, required)
- `palette_spec` (required)
- `line_shape_language` (required)
- `texture_material_language` (required)
- `rendering_rules` (required)
- `negative_constraints` (required)
- `continuity_anchors` (required)
- `variation_budget` (required)
- `integrity_report` (issues + fixes)
- `trace_id` (optional)

Missing any required field → REJECT.

Hard rule:
- stylization_level and realism_level must not both be extreme without HYBRID mode.

---

## 4. PALETTE SPEC

### 4.1 PALETTE_SPEC (required fields)
- `temperature` = COOL | NEUTRAL | WARM | MIXED_CONTROLLED
- `saturation_range` (min/max 0–100)
- `contrast_mode` = LOW | MEDIUM | HIGH | FILMIC
- `primary_palette` (list of palette tokens; conceptual ok)
- `accent_palette` (list; limited)
- `skin_tone_policy` (if characters)
- `forbidden_palette_moves` (e.g., neon spam, random gradients)
- `notes`

Hard rules:
- accents must be scarce (default ≤ 10% of frame impact).
- saturation must respect tone profile (mood coupling).

---

## 5. LINE & SHAPE LANGUAGE

### 5.1 LINE_SHAPE_LANGUAGE (required fields)
- `shape_bias` = ANGULAR | ORGANIC | MIXED_CONTROLLED
- `edge_behavior` = HARD | SOFT | HYBRID_CONTROLLED
- `detail_density` = LOW | MEDIUM | HIGH
- `silhouette_priority` = true
- `forbidden_shapes` (optional)
- `notes`

Hard rule:
- silhouette must remain readable under the chosen language.

---

## 6. TEXTURE & MATERIAL LANGUAGE

### 6.1 TEXTURE_MATERIAL_LANGUAGE (required fields)
- `material_bias` (metal/stone/skin/fabric/plastic etc.)
- `surface_finish_rules` (matte/gloss distribution)
- `micro_detail_policy` (grain/noise/scratches)
- `film_grain_policy` (optional)
- `artifact_avoidance` (over-sharpening, wax skin, plastic look)
- `notes`

---

## 7. RENDERING RULES

### 7.1 RENDERING_RULES (required fields)
- `render_quality_target` = DRAFT | PRODUCTION | HERO
- `sharpness_policy` (soft/neutral/crisp + bounds)
- `color_grading_policy` (filmic/neutral/stylized)
- `shadow_behavior_policy` (soft/hard/filmic rolloff)
- `highlight_behavior_policy` (bloom allowed? limits)
- `depth_of_field_policy` (couples with camera engine)
- `notes`

---

## 8. NEGATIVE CONSTRAINTS (HARD)

### 8.1 NEGATIVE_CONSTRAINTS (required fields)
- `forbidden_artifacts` (list)
  - extra limbs/fingers
  - warped faces
  - inconsistent logos/symbols
  - unreadable text blocks
  - random watermarks
  - heavy jpeg artifacts
- `forbidden_style_drift` (list)
  - sudden anime eyes in realism
  - plastic skin in cinematic realism
  - random neon palette
  - inconsistent line thickness
- `negative_prompt_tokens` (list; generator-facing, optional but recommended)
- `notes`

Hard rule:
- any forbidden artifact at high severity → INVALID unless corrected.

---

## 9. CONTINUITY ANCHORS

### 9.1 CONTINUITY_ANCHORS (required fields)
- `anchor_entities` (characters/props/symbols/locations)
- `identity_rules` (what must remain stable)
- `costume_palette_rules` (if characters)
- `symbol_lock_rules` (logos, insignia, runes)
- `world_texture_lock_rules` (e.g., “metal is brushed, not chrome”)
- `allowed_variations` (bounded list)

Hard rule:
- anchors cannot vary beyond the declared variation budget.

---

## 10. VARIATION BUDGET

### 10.1 VARIATION_BUDGET (required fields)
- `allowed_variation_axes` (camera angle, lighting intensity, fog, lens)
- `forbidden_variation_axes` (style family, palette temp flips, line language)
- `max_variation_per_scene` (0–10)
- `max_variation_across_episode` (0–10)
- `repair_actions` (how to pull back drift)

---

## 11. INPUT ARTIFACTS

### 11.1 INPUT — ART_STYLE_REQUEST
**REQUIRED FIELDS**
- `as_req_id`
- `timestamp`
- `tone_profile_ref` (required)
- `atmosphere_layer_map_ref` (required)
- `platform_constraints_ref` (required)
- `target_medium` (required)
- `constraints_refs` (required)
- `existing_style_anchor_refs` (optional)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 12. OUTPUT ARTIFACTS

### 12.1 OUTPUT — ART_STYLE_SPEC
(see model above)

### 12.2 OUTPUT — ART_STYLE_VERDICT
- `as_req_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 13. CORE OPERATIONS

- OP_01: INGEST_TONE_ATMOSPHERE_PLATFORM_CONSTRAINTS
- OP_02: SELECT_STYLE_FAMILY + REALISM/STYLIZATION LEVELS
- OP_03: DEFINE_PALETTE_SPEC
- OP_04: DEFINE_LINE_SHAPE_LANGUAGE
- OP_05: DEFINE_TEXTURE_MATERIAL_LANGUAGE
- OP_06: DEFINE_RENDERING_RULES
- OP_07: DEFINE_NEGATIVE_CONSTRAINTS (tokens + artifacts)
- OP_08: DEFINE_CONTINUITY_ANCHORS
- OP_09: SET_VARIATION_BUDGET
- OP_10: RUN_STYLE_CONTINUITY_CHECKS
- OP_11: EMIT_ART_STYLE_SPEC

---

## 14. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- style family ambiguous
- palette violates tone
- anchors undefined for multi-shot contexts
- forbidden artifacts not prevented
- variation budget allows drift
- realism/stylization conflict without HYBRID

Reaction:
- Verdict INVALID (CRITICAL)
- Emit repair plan:
  - lock palette + temperature
  - lock anchors
  - reduce variation axes
  - add negative constraints
  - align realism/stylization targets

---

## 15. TRACE RULES

- trace_id optional unless pipeline requires traced execution
- if present, propagate into camera/lighting/generation specs

---

## 16. NON-GOALS
- Does not decide composition
- Does not decide lighting
- Does not write prompts
- Does not change canon

---

## 17. FINAL STATEMENT

Style is stability under variation.
Lock the contract — then let shots breathe safely.

---

**STATUS:** Art Style Engine v1.0  
**REALM:** ACTIVE
