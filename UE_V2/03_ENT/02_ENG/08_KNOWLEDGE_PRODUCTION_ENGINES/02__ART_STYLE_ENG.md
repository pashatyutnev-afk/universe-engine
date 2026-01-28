# ART STYLE ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/02__ART_STYLE_ENG.md
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 08_KNOWLEDGE_PRODUCTION_ENGINES
CLASS: PRODUCTION (L3)
LEVEL: L3
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.PROD.KP.ART.STYLE.001
OWNER: SYSTEM
ROLE: Defines deterministic art-style constraints for visual production: palette policies, rendering language, material/texture rules, line/shape treatment, style invariants, and drift gates. Outputs style specs consumable by image/video generation and art direction without defining story content.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Art Style Engine created: art style spec schema, palette policy, material rules, invariants, and drift gates."
- REASON: "Production needs a reusable style language distinct from composition, camera, and lighting."
- IMPACT: "Visual assets remain style-consistent across scenes and generations."
- CHANGE_ID: UE.CHG.2026-01-08.PROD.KP.ART.STYLE.001

---

## 0) PURPOSE (LAW)
This engine owns **ART STYLE constraints** (render language):
- palette policies (not just colors, but constraints)
- line/edge treatment and shape language rules (as style spec)
- material/texture treatment rules
- detail granularity constraints (fine vs coarse)
- invariants (what must stay constant across outputs)
- drift gates to detect style leakage or inconsistency

Hard rule:
- This engine defines style constraints for production; it does NOT define tone/mood (style family) and does NOT define camera or lighting.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- define composition hierarchy (belongs to `01__VISUAL_COMPOSITION_ENG`)
- define camera/lens/movement (belongs to `03__CAMERA_CINEMATOGRAPHY_ENG`)
- define lighting design (belongs to `04__LIGHTING_ENG`)
- generate assets (belongs to `05__IMAGE_GENERATION_ENG` and `06__VIDEO_GENERATION_ENG`)
- define narrative meaning/plot/characters/world laws (domain families)

FORBIDDEN:
- “art style” as subjective prose without controlled spec fields
- embedding editing/montage rules

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- TONE_PROFILE (optional)
- ATMOSPHERE_LAYER_SPEC (optional)
- VISUAL_CONTEXT_BRIEF (optional: setting/props/character refs)
- COMPOSITION_GUIDE (optional)
- STYLE_REFERENCE_SET (optional: descriptors, not copyrighted images)

PRODUCES:
- ART_STYLE_SPEC
- PALETTE_POLICY
- MATERIAL_TEXTURE_RULESET
- STYLE_GATES_REPORT

DEPENDS_ON:
- [] (can consume other production/style artifacts but not required)

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/PRODUCTION/VISUAL/ART_STYLE/
OPTIONAL:
- KB/PRODUCTION/VISUAL/ART_STYLE (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Art Style Spec: structured style language for visual output generation/creation.
- Palette Policy: constraints on hue families, contrast, saturation, and forbidden palettes.
- Material Rule: constraints on how surfaces appear (roughness, specular, wear).
- Line/Edge Treatment: hard/soft edges, outlines, stylization rules.
- Detail Granularity: allowed level of micro-detail (0..100).
- Drift: output diverges from declared invariants.

Enums (baseline):
- scope: GLOBAL|ARC|SCENE_WINDOW|ASSET_CLASS
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- palette constraints and invariants
- rendering language rules (line, edges, materials, textures)
- style consistency gates

OUT OF SCOPE (HARD):
- composition planning (composition engine)
- camera grammar (camera engine)
- lighting implementation (lighting engine)
- asset generation execution (image/video engines)

COLLISION RULE:
- If request is “frame hierarchy / negative space” → composition engine
- If request is “lens choice / camera move” → camera engine
- If request is “key/fill/rim lighting design” → lighting engine
- If request is “generate images/videos” → image/video generation engines

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: ART_STYLE_SPEC defines invariants and controlled fields (palette, line, material, detail).
R2 (HARD) MUST: PALETTE_POLICY declares allowed ranges and forbidden ranges (not vague “nice colors”).
R3 (HARD) MUST: MATERIAL_TEXTURE_RULESET defines material treatment rules and forbidden treatments.
R4 (HARD) MUST: gates detect drift and invariant breaks.
R5 (HARD) FORBIDDEN: style spec that contains camera/lens/lighting implementation instructions.
R6 (SOFT) SHOULD: include “asset class overrides” (characters/props/environments) without breaking invariants.
R7 (HARD) MUST: produced artifacts have schemas and storage targets.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: ART_STYLE_SPEC
- MUST:
  - style_spec_id
  - version
  - scope (GLOBAL|ARC)
  - invariants[] (non-empty)
  - line_edge_profile (required)
  - detail_profile (required)
  - palette_policy_ref (required)
  - material_rules_ref (required)
  - allowed_overrides[] (optional)
  - validation_checks[] (non-empty)
- LINE EDGE PROFILE (minimum):
  - edge_hardness (0..100)
  - outline_policy (NONE|SOFT|HARD|SELECTIVE)
  - line_weight_variation (0..100)
  - forbidden_treatments[] (optional)
- DETAIL PROFILE (minimum):
  - detail_granularity_target (0..100)
  - detail_bounds (min,max)
  - noise_texture_policy (NONE|SUBTLE|VISIBLE) (optional)
- INVARIANT (minimum):
  - invariant_id
  - statement (testable)
  - severity_if_broken (S0|S1|S2|S3)
- VALIDATION:
  - invariants non-empty
  - detail bounds valid and include target
  - refs present (palette/material)
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/VISUAL/ART_STYLE/ART_STYLE_SPEC.md

---

ARTIFACT: PALETTE_POLICY
- MUST:
  - palette_id
  - version
  - allowed_hue_families[] (non-empty)
  - saturation_bounds (min,max 0..100)
  - contrast_policy (LOW|MED|HIGH|CONTROLLED)
  - accent_policy (optional)
  - forbidden_palettes[] (optional)
  - checks[] (non-empty)
- ACCENT POLICY (optional):
  - allowed_accents[] (hue families)
  - max_accent_share (0..100)
  - when_allowed (testable)
- VALIDATION:
  - hue families non-empty
  - bounds valid
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/VISUAL/ART_STYLE/PALETTE_POLICY.md

---

ARTIFACT: MATERIAL_TEXTURE_RULESET
- MUST:
  - ruleset_id
  - version
  - material_rules[] (non-empty)
  - texture_rules[] (optional)
  - forbidden_treatments[] (non-empty recommended)
  - checks[] (non-empty)
- MATERIAL RULE (minimum):
  - rule_id
  - material_class (METAL|STONE|WOOD|FABRIC|SKIN|GLASS|LIQUID|OTHER)
  - roughness_target (0..100)
  - specular_policy (LOW|MED|HIGH|CONTROLLED)
  - wear_policy (CLEAN|WORN|AGED|MIXED)
  - statement (testable)
  - severity_if_broken (S0|S1|S2|S3)
- TEXTURE RULE (optional):
  - rule_id
  - texture_type (GRAIN|SCRATCH|DUST|PATINA|NOISE)
  - allowed_intensity (0..100)
  - when_allowed (testable)
- VALIDATION:
  - material_rules non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/VISUAL/ART_STYLE/MATERIAL_TEXTURE_RULESET.md

---

ARTIFACT: STYLE_GATES_REPORT
- MUST:
  - report_id
  - version
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
- Minimum required gates:
  - G1_INVARIANTS_EMPTY (S0)
  - G2_PALETTE_POLICY_MISSING (S0)
  - G3_MATERIAL_RULES_EMPTY (S0)
  - G4_CAMERA_LIGHTING_LEAK (S1)
  - G5_DETAIL_BOUNDS_INVALID (S0)
  - G6_DRIFT_DETECTED (S1)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/VISUAL/ART_STYLE/STYLE_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load optional style context (tone/atmosphere) + visual context brief.
2) Define palette policy (allowed hue families, saturation/contrast bounds).
3) Define material/texture rules (per material class).
4) Define line/edge profile and detail profile.
5) Define invariants (what must stay constant).
6) Run gates (missing pieces, bounds invalid, camera/lighting leak, drift).
7) Emit artifacts.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: invariants[] empty.
- S0-2: palette policy missing or invalid.
- S0-3: material rules empty.
- S0-4: detail bounds invalid.
- S0-5: produced artifacts missing required schemas/storage targets.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- tone/atmosphere (optional) inform style constraints (not owned)
- composition guide (optional) helps ensure style supports hierarchy

Downstream:
- image/video generation engines consume art style spec + palette/material rules
- camera/lighting engines align implementation to style constraints
- QA/consistency engines validate assets against style gates

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family template:
  08_KNOWLEDGE_PRODUCTION_ENGINES/00__TEMPLATE__ENGINE__KNOWLEDGE_PRODUCTION_ENGINES.md
- Family README:
  08_KNOWLEDGE_PRODUCTION_ENGINES/00__README__KNOWLEDGE_PRODUCTION_ENGINES.md

--- END.

LOCK: OPEN
