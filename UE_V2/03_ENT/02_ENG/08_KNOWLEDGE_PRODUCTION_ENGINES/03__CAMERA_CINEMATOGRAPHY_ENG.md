# CAMERA & CINEMATOGRAPHY ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/03__CAMERA_CINEMATOGRAPHY_ENG.md
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
UID: UE.ENG.PROD.KP.CAMERA.CINEMA.001
OWNER: SYSTEM
ROLE: Defines deterministic camera/cinematography implementation specs from upstream constraints: shot types, lens/DoF policy, movement grammar, framing rules, and validation gates. Consumes composition/style/atmosphere constraints and outputs camera plans without editing montage ownership.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Camera & Cinematography Engine created: camera grammar schema, shot plan, lens/movement policy, and compliance gates."
- REASON: "Composition defines constraints; camera engine turns them into implementable shot grammar."
- IMPACT: "Shots become consistent, reproducible, and compatible with style and composition constraints."
- CHANGE_ID: UE.CHG.2026-01-08.PROD.KP.CAMERA.CINEMA.001

---

## 0) PURPOSE (LAW)
This engine owns **camera & cinematography implementation** (visual capture grammar):
- shot plan generation from composition/hierarchy constraints
- lens policy and DoF rules as controlled parameters
- movement grammar (static/pan/dolly/handheld) as constrained choices
- framing rules (coverage and continuity) as a plan
- gates to prevent contradictions (e.g., lens policy breaks composition)

Hard rule:
- This engine does NOT own editing/montage rhythm; it produces shot grammar and plans.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- define composition constraints (belongs to `01__VISUAL_COMPOSITION_ENG`)
- define art style palette (belongs to `02__ART_STYLE_ENG`)
- define lighting design (belongs to `04__LIGHTING_ENG`)
- generate images/video (belongs to `05__IMAGE_GENERATION_ENG` / `06__VIDEO_GENERATION_ENG`)
- define editing rules and montage rhythm (belongs to `07__EDITING_MONTAGE_ENG`)
- define narrative content/meaning (domain families)

FORBIDDEN:
- embedding montage timing, cut patterns as camera rules
- replacing composition hierarchy (camera must implement it)

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- COMPOSITION_GUIDE (recommended)
- VISUAL_HIERARCHY_MAP (optional)
- ART_STYLE_SPEC (optional)
- TONE_PROFILE / ATMOSPHERE_LAYER_SPEC (optional)
- SCENE_PACK (optional)
- EVENT_SCHEDULE (optional)

PRODUCES:
- CAMERA_GRAMMAR_SPEC
- SHOT_PLAN
- LENS_DOF_POLICY
- MOVEMENT_GRAMMAR
- CAMERA_GATES_REPORT

DEPENDS_ON:
- [08_KNOWLEDGE_PRODUCTION_ENGINES/01__VISUAL_COMPOSITION_ENG]
(soft) [08_KNOWLEDGE_PRODUCTION_ENGINES/02__ART_STYLE_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/PRODUCTION/VISUAL/CAMERA/
OPTIONAL:
- KB/PRODUCTION/VISUAL/CAMERA (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Shot Plan: ordered list of shots per scene window with purpose and constraints.
- Camera Grammar: controlled vocabulary of shot types and movements.
- Lens Policy: allowed focal lengths (as ranges or classes) and usage constraints.
- DoF Policy: depth-of-field constraints (shallow/medium/deep) as categories with conditions.
- Coverage Rule: minimum set of shots to cover required actions (constraint plan).
- Continuity Rule: camera consistency constraints across shot sequences.

Enums (baseline):
- shot_type: WIDE|MEDIUM|CLOSE|EXTREME_CLOSE|POV|OVER_SHOULDER|INSERT|ESTABLISHING
- move_type: STATIC|PAN|TILT|DOLLY|TRACK|CRANE|HANDHELD|STEADICAM|DRONE
- dof: SHALLOW|MEDIUM|DEEP
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- camera grammar and implementation plans (shots/lens/movement)
- continuity and coverage constraints for camera layer
- validation gates (composition compliance, continuity, overuse)

OUT OF SCOPE (HARD):
- composition ownership (hierarchy/routing)
- lighting execution
- art style palette
- editing/montage timing and cut logic

COLLISION RULE:
- If request is “where eye should go in frame” → composition engine
- If request is “lighting plan” → lighting engine
- If request is “edit rhythm/cut pattern” → editing/montage engine
- If request is “generate final frames/video” → image/video generation engines

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: SHOT_PLAN implements composition hierarchy (P1 clarity) for each planned shot.
R2 (HARD) MUST: LENS_DOF_POLICY defines allowed lens classes and DoF categories with conditions.
R3 (HARD) MUST: MOVEMENT_GRAMMAR defines allowed movements and forbidden movements by context.
R4 (HARD) MUST: CAMERA_GRAMMAR_SPEC defines controlled vocab and default patterns.
R5 (HARD) FORBIDDEN: embedding editing/montage rules (cuts) as camera rules.
R6 (SOFT) SHOULD: include anti-shake/anti-whiplash constraints unless handheld is explicitly allowed.
R7 (HARD) MUST: gates detect continuity breaks and composition violations.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: CAMERA_GRAMMAR_SPEC
- MUST:
  - grammar_id
  - version
  - shot_types[] (non-empty)
  - movement_types[] (non-empty)
  - default_patterns[] (optional)
  - continuity_rules[] (non-empty)
  - checks[] (non-empty)
- CONTINUITY RULE (minimum):
  - rule_id
  - statement (testable)
  - severity_if_broken (S0|S1|S2|S3)
- VALIDATION:
  - shot_types and movement_types non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/VISUAL/CAMERA/CAMERA_GRAMMAR_SPEC.md

---

ARTIFACT: LENS_DOF_POLICY
- MUST:
  - policy_id
  - version
  - lens_classes[] (non-empty)
  - dof_classes[] (non-empty)
  - selection_rules[] (non-empty)
  - forbidden_combinations[] (optional)
  - checks[] (non-empty)
- LENS CLASS (minimum):
  - class_id
  - name (WIDE|NORMAL|TELE|MACRO)
  - focal_range_mm (optional)
  - when_to_use (testable)
  - when_forbidden (optional)
- DOF CLASS (minimum):
  - dof (SHALLOW|MEDIUM|DEEP)
  - when_to_use (testable)
  - when_forbidden (optional)
- VALIDATION:
  - selection_rules non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/VISUAL/CAMERA/LENS_DOF_POLICY.md

---

ARTIFACT: MOVEMENT_GRAMMAR
- MUST:
  - movement_id
  - version
  - allowed_moves[] (non-empty)
  - rules[] (non-empty)
  - checks[] (non-empty)
- RULE (minimum):
  - rule_id
  - move_type
  - condition (testable)
  - allowed (bool)
  - reason (testable)
  - severity_if_broken (S0|S1|S2|S3)
- VALIDATION:
  - allowed_moves non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/VISUAL/CAMERA/MOVEMENT_GRAMMAR.md

---

ARTIFACT: SHOT_PLAN
- MUST:
  - shot_plan_id
  - version
  - source_refs (composition_guide_id optional, scene_pack_id optional)
  - shots[] (non-empty)
  - coverage_requirements[] (optional)
  - checks[] (non-empty)
- SHOT (minimum):
  - shot_id
  - scene_ref (optional)
  - order_index
  - shot_type (enum)
  - framing_notes (testable)
  - primary_anchor (P1) (required)
  - lens_class_ref (required)
  - dof_class (required)
  - move_type (required)
  - continuity_notes (optional)
  - constraints_refs[] (optional)
- VALIDATION:
  - shots ordered
  - each shot has primary_anchor and lens/dof/move fields
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/VISUAL/CAMERA/SHOT_PLAN.md

---

ARTIFACT: CAMERA_GATES_REPORT
- MUST:
  - report_id
  - version
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
- Minimum required gates:
  - G1_SHOT_PLAN_EMPTY (S0)
  - G2_MISSING_PRIMARY_ANCHOR (S0)
  - G3_COMPOSITION_VIOLATION (S1)
  - G4_CONTINUITY_BREAK (S1)
  - G5_LENS_POLICY_MISSING (S0)
  - G6_EDITING_RULE_LEAK (S1)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/VISUAL/CAMERA/CAMERA_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load composition guide and optional hierarchy map/scene pack.
2) Build camera grammar (shot types, continuity rules).
3) Build lens + DoF policy (classes + selection rules).
4) Build movement grammar (allowed moves with conditions).
5) Generate shot plan per scene window:
   - ensure P1 clarity and coverage constraints
6) Run gates (missing anchors, continuity breaks, composition violations).
7) Emit artifacts.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: shot plan empty or missing required fields.
- S0-2: lens/DoF policy missing.
- S0-3: any shot missing primary anchor.
- S0-4: outputs missing schemas/storage targets.
- S0-5: editing/montage rules embedded as camera rules.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- composition provides hierarchy/routing constraints
- art style provides rendering constraints (optional)
- style family provides mood/atmosphere constraints (optional)

Downstream:
- lighting engine supports shot plan via emphasis rules
- image/video generation engines use shot plan + lens/move constraints as generation specs
- editing/montage engine uses shot list as inputs but owns timing/cuts separately
- QA engines validate continuity with gates report

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family template:
  08_KNOWLEDGE_PRODUCTION_ENGINES/00__TEMPLATE__ENGINE__KNOWLEDGE_PRODUCTION_ENGINES.md
- Family README:
  08_KNOWLEDGE_PRODUCTION_ENGINES/00__README__KNOWLEDGE_PRODUCTION_ENGINES.md

--- END.

LOCK: OPEN
