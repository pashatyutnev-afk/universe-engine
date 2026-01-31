# LIGHTING ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/04__LIGHTING_ENG.md
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
UID: UE.ENG.PROD.KP.LIGHTING.001
OWNER: SYSTEM
ROLE: Defines deterministic lighting implementation specs: key/fill/rim policies, contrast and mood mapping, shadow rules, practicals policy, and validation gates. Consumes style/atmosphere and camera/composition constraints; outputs lighting plans without owning color grading or sound.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Lighting Engine created: lighting plan schema, key/fill/rim policies, contrast rules, and compliance gates."
- REASON: "Lighting is a separate implementable layer that must align with style and composition hierarchy."
- IMPACT: "Visual outputs maintain consistent mood and focus support through deterministic lighting rules."
- CHANGE_ID: UE.CHG.2026-01-08.PROD.KP.LIGHTING.001

---

## 0) PURPOSE (LAW)
This engine owns **LIGHTING implementation** as production constraints/plans:
- translates tone/mood/atmosphere into lighting intent (contrast, softness, shadow policy)
- supports composition hierarchy (P1 emphasis) via lighting emphasis constraints
- defines key/fill/rim policies and practicals policy (as plan)
- produces lighting plans and rulesets with gates against contradictions

Hard rule:
- Lighting engine outputs implementable lighting specs; it does NOT own camera grammar, editing, or art style palette.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- define composition hierarchy (belongs to `01__VISUAL_COMPOSITION_ENG`)
- define camera lens/movement grammar (belongs to `03__CAMERA_CINEMATOGRAPHY_ENG`)
- define art style palette/render language (belongs to `02__ART_STYLE_ENG`)
- define color grading/post pipeline (can be separate later; not here)
- generate assets (image/video engines)
- define montage/editing rhythm (editing engine)

FORBIDDEN:
- using lighting rules to rewrite story content (“make it tragic”) — only constraints
- embedding camera lens choices or editing cuts

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- TONE_PROFILE (optional)
- MOOD_PROFILE (optional)
- ATMOSPHERE_LAYER_SPEC (recommended)
- COMPOSITION_GUIDE (recommended)
- VISUAL_HIERARCHY_MAP (optional)
- CAMERA_GRAMMAR_SPEC / SHOT_PLAN (optional but recommended)
- ART_STYLE_SPEC (optional)

PRODUCES:
- LIGHTING_STYLE_SPEC
- LIGHTING_PLAN
- LIGHTING_RULESET
- LIGHTING_GATES_REPORT

DEPENDS_ON:
- [08_KNOWLEDGE_PRODUCTION_ENGINES/01__VISUAL_COMPOSITION_ENG]
(soft) [08_KNOWLEDGE_PRODUCTION_ENGINES/03__CAMERA_CINEMATOGRAPHY_ENG, 06_GENRE_STYLE_ENGINES/02__ATMOSPHERE_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/PRODUCTION/VISUAL/LIGHTING/
OPTIONAL:
- KB/PRODUCTION/VISUAL/LIGHTING (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Lighting Style Spec: global lighting language constraints (contrast, softness, shadow policy).
- Lighting Plan: per shot/scene lighting intent and practical requirements.
- Key/Fill/Rim: primary light roles (as ratios/policies, not exact gear lists).
- Practicals: in-scene light sources that motivate lighting (lamps, screens).
- Contrast Level: LOW|MED|HIGH|CONTROLLED (constraint).
- Softness: 0..100 (proxy for edge softness).
- Shadow Policy: how shadows behave (deep, readable, noisy) as constraints.

Enums (baseline):
- contrast: LOW|MED|HIGH|CONTROLLED
- motivation: NATURAL|PRACTICAL|STYLED|MIXED
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- lighting intent and implementable policies
- key/fill/rim and practicals constraints
- support of composition P1 hierarchy via light emphasis
- validation gates (contradictions, over-dark, lost focus)

OUT OF SCOPE (HARD):
- camera lens/movement decisions
- art style palette/rendering language
- editing/montage
- final color grading

COLLISION RULE:
- If request is “lens/DoF choice” → camera engine
- If request is “composition hierarchy” → composition engine
- If request is “palette/render style” → art style engine
- If request is “cut timing and rhythm” → editing/montage engine

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: LIGHTING_STYLE_SPEC declares contrast/softness/shadow policies and motivation style.
R2 (HARD) MUST: LIGHTING_PLAN supports P1 focus from composition (primary anchor lit policy).
R3 (HARD) MUST: LIGHTING_RULESET defines MUST/FORBIDDEN rules (e.g., “P1 cannot be underexposed below threshold proxy”).
R4 (HARD) MUST: gates detect loss of hierarchy and contradictions with atmosphere constraints.
R5 (HARD) FORBIDDEN: lighting rules that specify exact gear or color grade; keep as policies.
R6 (SOFT) SHOULD: include practicals policy to keep lighting motivated unless styled explicitly.
R7 (HARD) MUST: produced artifacts include schemas and storage.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: LIGHTING_STYLE_SPEC
- MUST:
  - lighting_style_id
  - version
  - base_refs (atmosphere_spec_id optional, tone_profile_id optional)
  - contrast_policy (LOW|MED|HIGH|CONTROLLED)
  - softness_target (0..100)
  - softness_bounds (min,max)
  - shadow_policy (required)
  - motivation_style (NATURAL|PRACTICAL|STYLED|MIXED)
  - anti_style_rules[] (non-empty)
  - validation_checks[] (non-empty)
- SHADOW POLICY (minimum):
  - depth_target (0..100)
  - readability_requirement (testable)
  - forbidden_shadow_patterns[] (optional)
- VALIDATION:
  - softness bounds valid and include target
  - anti_style_rules non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/VISUAL/LIGHTING/LIGHTING_STYLE_SPEC.md

---

ARTIFACT: LIGHTING_PLAN
- MUST:
  - lighting_plan_id
  - version
  - source_refs (shot_plan_id optional, composition_guide_id optional)
  - entries[] (non-empty)
  - checks[] (non-empty)
- ENTRY (minimum):
  - entry_id
  - scope (SCENE_WINDOW|SHOT)
  - ref_id (scene_id/shot_id)
  - primary_anchor (P1) (required)
  - key_fill_policy:
    - ratio_proxy (e.g., "2:1", "4:1") (string)
    - key_direction (optional)
    - fill_presence (LOW|MED|HIGH)
  - rim_policy (NONE|SUBTLE|STRONG|SELECTIVE)
  - practicals_policy:
    - required (bool)
    - practical_refs[] (optional)
    - motivation_note (optional)
  - exposure_guardrails (optional proxy):
    - min_p1_visibility (0..100)
    - max_blowout_risk (0..100)
  - notes
- VALIDATION:
  - entries non-empty
  - each entry has primary_anchor
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/VISUAL/LIGHTING/LIGHTING_PLAN.md

---

ARTIFACT: LIGHTING_RULESET
- MUST:
  - ruleset_id
  - version
  - rules[] (non-empty)
  - checks[] (non-empty)
- RULE (minimum):
  - rule_id
  - type (MUST|FORBIDDEN|ALLOWED)
  - scope (GLOBAL|ARC|SCENE_WINDOW|SHOT)
  - statement (testable)
  - severity_if_broken (S0|S1|S2|S3)
- VALIDATION:
  - rules non-empty
  - at least one FORBIDDEN rule
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/VISUAL/LIGHTING/LIGHTING_RULESET.md

---

ARTIFACT: LIGHTING_GATES_REPORT
- MUST:
  - report_id
  - version
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
- Minimum required gates:
  - G1_STYLE_SPEC_MISSING (S0)
  - G2_PLAN_EMPTY (S0)
  - G3_P1_UNSUPPORTED (S0)
  - G4_CONTRADICTS_ATMOSPHERE (S1)
  - G5_SOFTNESS_BOUNDS_INVALID (S0)
  - G6_GEAR_OR_GRADE_LEAK (S1)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/VISUAL/LIGHTING/LIGHTING_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load atmosphere/tone (optional) + composition guide + shot plan (if available).
2) Build LIGHTING_STYLE_SPEC:
   - contrast, softness, shadow policy, motivation style
3) Build LIGHTING_PLAN:
   - per scene/shot entries, ensure P1 support and guardrails
4) Build LIGHTING_RULESET:
   - must/forbidden constraints
5) Run gates:
   - missing plan/spec, P1 unsupported, invalid bounds, atmosphere contradictions
6) Emit artifacts.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: LIGHTING_STYLE_SPEC missing required fields.
- S0-2: LIGHTING_PLAN entries[] empty.
- S0-3: any entry missing primary_anchor (P1).
- S0-4: softness bounds invalid.
- S0-5: produced artifacts missing schemas/storage targets.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- atmosphere/tone provides feel constraints
- composition provides hierarchy targets
- camera engine provides shot plan (optional but recommended)

Downstream:
- image/video generation engines consume lighting spec/plan as generation constraints
- editing/montage consumes shots but not lighting rules
- QA validates final visuals against gates report

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family template:
  08_KNOWLEDGE_PRODUCTION_ENGINES/00__TEMPLATE__ENGINE__KNOWLEDGE_PRODUCTION_ENGINES.md
- Family README:
  08_KNOWLEDGE_PRODUCTION_ENGINES/00__README__KNOWLEDGE_PRODUCTION_ENGINES.md

--- END.

LOCK: OPEN
