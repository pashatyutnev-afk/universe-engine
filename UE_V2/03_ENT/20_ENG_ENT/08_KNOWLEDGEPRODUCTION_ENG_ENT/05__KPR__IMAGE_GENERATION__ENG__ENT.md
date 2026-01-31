# IMAGE GENERATION ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/05__IMAGE_GENERATION_ENG.md
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
UID: UE.ENG.PROD.KP.IMAGE.GEN.001
OWNER: SYSTEM
ROLE: Converts production constraints into deterministic image-generation specs: prompt blueprint, negative constraints, shot/style/lighting bindings, batch plan, and validation gates. Produces generator-ready artifacts without owning story content.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Image Generation Engine created: prompt blueprint schema, negative constraint set, batch plan, and validation gates."
- REASON: "Upstream style/composition/camera/lighting must translate into reproducible image generation specs."
- IMPACT: "Images can be generated consistently and audited against constraints."
- CHANGE_ID: UE.CHG.2026-01-08.PROD.KP.IMAGE.GEN.001

---

## 0) PURPOSE (LAW)
This engine owns **IMAGE GENERATION specification**:
- translates constraints (composition, art style, camera, lighting, atmosphere) into an image spec
- produces prompt blueprint + negative constraints + control parameters (as abstract fields)
- supports batch generation planning (variants, seeds, naming)
- emits gates to prevent constraint omission, contradictions, and unsafe leakage (e.g., adding plot)

Hard rule:
- This engine outputs generator-ready specs, not final images and not narrative writing.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- define composition (composition engine owns)
- define art style (art style engine owns)
- define camera grammar (camera engine owns)
- define lighting (lighting engine owns)
- define editing/montage (editing engine owns)
- generate the image itself (execution is external/tooling)
- define story content/meaning (narrative/character/world engines)

FORBIDDEN:
- injecting new canon facts into prompts
- embedding copyrighted reference images as requirements (only descriptors)

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- COMPOSITION_GUIDE (recommended)
- VISUAL_HIERARCHY_MAP (optional)
- ART_STYLE_SPEC (recommended)
- PALETTE_POLICY (optional)
- MATERIAL_TEXTURE_RULESET (optional)
- SHOT_PLAN (optional)
- LIGHTING_STYLE_SPEC (recommended)
- LIGHTING_PLAN (optional)
- ATMOSPHERE_LAYER_SPEC (optional)
- SCENE_PACK (optional)
- ASSET_REQUEST (optional: what images needed)

PRODUCES:
- IMAGE_PROMPT_BLUEPRINT
- NEGATIVE_CONSTRAINT_SET
- IMAGE_BATCH_PLAN
- IMAGE_GEN_GATES_REPORT

DEPENDS_ON:
- [08_KNOWLEDGE_PRODUCTION_ENGINES/01__VISUAL_COMPOSITION_ENG, 08_KNOWLEDGE_PRODUCTION_ENGINES/02__ART_STYLE_ENG, 08_KNOWLEDGE_PRODUCTION_ENGINES/04__LIGHTING_ENG]
(soft) [08_KNOWLEDGE_PRODUCTION_ENGINES/03__CAMERA_CINEMATOGRAPHY_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/PRODUCTION/VISUAL/IMAGE_GEN/
OPTIONAL:
- KB/PRODUCTION/VISUAL/IMAGE_GEN (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Prompt Blueprint: structured prompt spec (subject, setting, composition, style, lighting, constraints).
- Negative Constraint Set: forbidden elements and anti-style rules (must be explicit).
- Control Parameters: abstract generation controls (seed, aspect, fidelity level) without tying to a single vendor.
- Batch Plan: repeatable plan for generating multiple images with naming and variance bounds.
- Variant: controlled variation of the same blueprint.

Enums (baseline):
- aspect: 1:1|4:5|16:9|9:16|CUSTOM
- fidelity: LOW|MED|HIGH|ULTRA (abstract)
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- translating upstream constraints to generation specs
- building negative constraints and variant plans
- validating completeness and contradiction-free prompt specs

OUT OF SCOPE (HARD):
- creating upstream constraints (composition/style/camera/lighting)
- editing/video timing
- writing narrative content

COLLISION RULE:
- If request is “change art style rules” → art style engine
- If request is “change composition hierarchy” → composition engine
- If request is “camera lens/move” → camera engine (then re-run here)
- If request is “lighting mood” → lighting engine (then re-run here)

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: IMAGE_PROMPT_BLUEPRINT includes bindings to composition + style + lighting (refs) or explicit “UNKNOWN” with reason.
R2 (HARD) MUST: NEGATIVE_CONSTRAINT_SET includes anti-style + forbidden elements (non-empty).
R3 (HARD) MUST: batch plan declares seeds or seed policy for reproducibility.
R4 (HARD) FORBIDDEN: adding new canon facts not present in inputs (must be declared as optional imagination flag).
R5 (HARD) MUST: gates detect missing bindings, contradictions, and unsafe leakage (plot injection).
R6 (SOFT) SHOULD: include variance bounds to avoid drift across batch.
R7 (HARD) MUST: produced artifacts have schemas and storage targets.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: IMAGE_PROMPT_BLUEPRINT
- MUST:
  - blueprint_id
  - version
  - purpose (testable)
  - subject_block (required)
  - setting_block (optional)
  - composition_binding (ref or inline constraints)
  - style_binding (ref or inline constraints)
  - lighting_binding (ref or inline constraints)
  - atmosphere_binding (optional)
  - control_parameters (required)
  - constraints_summary[] (non-empty)
  - validation_checks[] (non-empty)
- SUBJECT BLOCK (minimum):
  - subject (testable)
  - key_attributes[] (optional)
  - actions (optional)
  - excluded_attributes[] (optional)
- SETTING BLOCK (optional):
  - location (optional)
  - time_of_day (optional)
  - environment_notes (optional)
- CONTROL PARAMETERS (minimum):
  - aspect (1:1|4:5|16:9|9:16|CUSTOM)
  - fidelity (LOW|MED|HIGH|ULTRA)
  - seed_policy (REQUIRED|OPTIONAL)
  - seed (optional if policy OPTIONAL)
  - variant_count_target (optional)
- VALIDATION:
  - subject present
  - constraints_summary non-empty
  - control_parameters.aspect present
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/VISUAL/IMAGE_GEN/IMAGE_PROMPT_BLUEPRINT.md

---

ARTIFACT: NEGATIVE_CONSTRAINT_SET
- MUST:
  - negative_id
  - version
  - forbidden_elements[] (non-empty)
  - anti_style_rules[] (non-empty)
  - forbidden_styles[] (optional)
  - forbidden_composition_patterns[] (optional)
  - checks[] (non-empty)
- FORBIDDEN ELEMENT (minimum):
  - item
  - reason
  - severity_if_present (S0|S1|S2|S3)
- VALIDATION:
  - forbidden_elements non-empty
  - anti_style_rules non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/VISUAL/IMAGE_GEN/NEGATIVE_CONSTRAINT_SET.md

---

ARTIFACT: IMAGE_BATCH_PLAN
- MUST:
  - batch_id
  - version
  - blueprint_ref
  - seed_plan (required)
  - variants[] (non-empty)
  - naming_rule (required)
  - variance_bounds (required)
  - checks[] (non-empty)
- SEED PLAN (minimum):
  - mode (FIXED|LIST|DERIVED)
  - seeds[] (optional; required if LIST)
  - derivation_rule (optional; required if DERIVED)
- VARIANT (minimum):
  - variant_id
  - delta_notes (testable)
  - seed (optional)
  - allowed_changes[] (optional)
  - forbidden_changes[] (optional)
- VARIANCE BOUNDS (minimum):
  - max_style_drift (0..100)
  - max_composition_drift (0..100)
  - max_lighting_drift (0..100)
- VALIDATION:
  - variants non-empty
  - naming_rule present
  - variance_bounds present
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/VISUAL/IMAGE_GEN/IMAGE_BATCH_PLAN.md

---

ARTIFACT: IMAGE_GEN_GATES_REPORT
- MUST:
  - report_id
  - version
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
- Minimum required gates:
  - G1_BLUEPRINT_MISSING (S0)
  - G2_NEGATIVE_SET_EMPTY (S0)
  - G3_BINDINGS_MISSING (S1)
  - G4_CONTRADICTION_FOUND (S1)
  - G5_SEED_POLICY_MISSING (S0)
  - G6_CANON_INJECTION (S0)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/VISUAL/IMAGE_GEN/IMAGE_GEN_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load upstream constraints (composition/style/lighting + optional camera/atmosphere).
2) Build prompt blueprint:
   - subject + setting + bindings + control parameters
3) Build negative constraints:
   - forbidden elements + anti-style rules
4) Build batch plan:
   - seed plan + variants + naming + variance bounds
5) Run gates:
   - missing bindings, contradictions, canon injection, missing seeds
6) Emit artifacts.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: missing blueprint or missing required fields.
- S0-2: negative constraint set empty.
- S0-3: seed policy missing (no reproducibility).
- S0-4: canon injection detected (new facts added without allowance).
- S0-5: produced artifacts missing schemas/storage targets.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- composition/style/lighting/camera provide constraints
- scene/event packs provide what should be depicted (optional)

Downstream:
- video generation engine may reuse blueprint structure
- QA engines validate generated images against gates + variance bounds
- asset storage/pipeline uses batch plan naming rules

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family template:
  08_KNOWLEDGE_PRODUCTION_ENGINES/00__TEMPLATE__ENGINE__KNOWLEDGE_PRODUCTION_ENGINES.md
- Family README:
  08_KNOWLEDGE_PRODUCTION_ENGINES/00__README__KNOWLEDGE_PRODUCTION_ENGINES.md

--- END.

LOCK: OPEN
