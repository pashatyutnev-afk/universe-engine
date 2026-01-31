# VIDEO GENERATION ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/06__VIDEO_GENERATION_ENG.md
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
UID: UE.ENG.PROD.KP.VIDEO.GEN.001
OWNER: SYSTEM
ROLE: Converts production constraints into deterministic video-generation specs: shot-to-clip blueprint, motion/continuity constraints, audio placeholders policy, batch plan, and validation gates. Produces generator-ready artifacts without owning editing montage or final sound mix.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Video Generation Engine created: clip blueprint schema, continuity constraints, batch plan, and validation gates."
- REASON: "Production constraints must translate into reproducible video-gen specs separate from editing/montage ownership."
- IMPACT: "Video clips can be generated consistently and audited against shot/style/lighting constraints."
- CHANGE_ID: UE.CHG.2026-01-08.PROD.KP.VIDEO.GEN.001

---

## 0) PURPOSE (LAW)
This engine owns **VIDEO GENERATION specification**:
- translates shot plan + style + lighting into clip blueprints
- defines motion/continuity constraints between clips
- defines audio placeholder policy (no deep audio production here)
- supports batch generation planning with reproducible seeds
- emits gates against missing constraints, contradictions, and montage leakage

Hard rule:
- This engine creates generator-ready clip specs; it does NOT own montage/editing rhythm.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- define editing/montage (belongs to `07__EDITING_MONTAGE_ENG`)
- define camera grammar (camera engine provides shot plan)
- define lighting/style constraints (their engines own)
- generate final mastered audio/music (sound engines own)
- write narrative content

FORBIDDEN:
- specifying final cut pattern or pacing-by-edit inside clip specs
- injecting new canon facts into specs

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- SHOT_PLAN (recommended)
- CAMERA_GRAMMAR_SPEC (optional)
- COMPOSITION_GUIDE (optional)
- ART_STYLE_SPEC (recommended)
- LIGHTING_STYLE_SPEC (recommended)
- LIGHTING_PLAN (optional)
- ATMOSPHERE_LAYER_SPEC (optional)
- EVENT_SCHEDULE (optional)
- VIDEO_REQUEST (optional: what clips needed)

PRODUCES:
- VIDEO_CLIP_BLUEPRINT
- CONTINUITY_MOTION_CONSTRAINT_SET
- VIDEO_BATCH_PLAN
- VIDEO_GEN_GATES_REPORT

DEPENDS_ON:
- [08_KNOWLEDGE_PRODUCTION_ENGINES/03__CAMERA_CINEMATOGRAPHY_ENG, 08_KNOWLEDGE_PRODUCTION_ENGINES/02__ART_STYLE_ENG, 08_KNOWLEDGE_PRODUCTION_ENGINES/04__LIGHTING_ENG]
(soft) [08_KNOWLEDGE_PRODUCTION_ENGINES/01__VISUAL_COMPOSITION_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/PRODUCTION/VIDEO/VIDEO_GEN/
OPTIONAL:
- KB/PRODUCTION/VIDEO/VIDEO_GEN (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Clip Blueprint: structured specification for a single generated clip (duration proxy, shot framing, motion constraints).
- Motion Constraint: allowed camera/object motion type and bounds.
- Continuity Constraint: required consistency across adjacent clips (subject position, direction, lighting continuity).
- Audio Placeholder Policy: declares whether clip has temp audio markers only (no mixing).
- Batch Plan: repeatable multi-clip generation plan with seeds and naming.

Enums (baseline):
- duration_proxy: SECONDS
- motion_type: STATIC|SLOW_MOVE|DYNAMIC_MOVE
- continuity_level: STRICT|SOFT|NONE
- fidelity: LOW|MED|HIGH|ULTRA
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- translating shot/style/lighting into clip specs
- continuity and motion constraint sets
- batch planning and gate validation

OUT OF SCOPE (HARD):
- montage/editing decisions (cut order, rhythm)
- sound design/mix/master
- story writing and structure ownership

COLLISION RULE:
- If request is “final edit rhythm / sequence” → editing & montage engine
- If request is “sound design/music for clip” → sound/music engines
- If request is “change shot grammar” → camera engine (then regenerate blueprint)

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: VIDEO_CLIP_BLUEPRINT binds to shot/style/lighting refs or explicit UNKNOWN with reason.
R2 (HARD) MUST: CONTINUITY_MOTION_CONSTRAINT_SET defines continuity level and motion bounds.
R3 (HARD) MUST: VIDEO_BATCH_PLAN defines seed plan and naming rule.
R4 (HARD) FORBIDDEN: embedding montage/cut timing as video generation constraints.
R5 (HARD) MUST: gates detect missing bindings, continuity contradictions, canon injection, missing seeds.
R6 (SOFT) SHOULD: define “safe variance bounds” for motion and lighting drift.
R7 (HARD) MUST: produced artifacts have schemas and storage targets.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: VIDEO_CLIP_BLUEPRINT
- MUST:
  - blueprint_id
  - version
  - purpose (testable)
  - shot_binding (ref or inline)
  - style_binding (ref or inline)
  - lighting_binding (ref or inline)
  - duration_seconds_target (number)
  - duration_bounds (min,max)
  - motion_policy (required)
  - continuity_level (STRICT|SOFT|NONE)
  - control_parameters (required)
  - constraints_summary[] (non-empty)
  - validation_checks[] (non-empty)
- MOTION POLICY (minimum):
  - motion_type (STATIC|SLOW_MOVE|DYNAMIC_MOVE)
  - bounds (optional: speed proxy 0..100)
  - forbidden_moves[] (optional)
- CONTROL PARAMETERS (minimum):
  - fidelity (LOW|MED|HIGH|ULTRA)
  - seed_policy (REQUIRED|OPTIONAL)
  - seed (optional)
  - aspect (optional: 16:9, 9:16, etc.)
- VALIDATION:
  - duration bounds valid and include target
  - constraints_summary non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/VIDEO/VIDEO_GEN/VIDEO_CLIP_BLUEPRINT.md

---

ARTIFACT: CONTINUITY_MOTION_CONSTRAINT_SET
- MUST:
  - set_id
  - version
  - continuity_rules[] (non-empty if continuity_level != NONE)
  - motion_rules[] (non-empty)
  - checks[] (non-empty)
- CONTINUITY RULE (minimum):
  - rule_id
  - applies_between (clip_id_a, clip_id_b optional)
  - statement (testable)
  - severity_if_broken (S0|S1|S2|S3)
- MOTION RULE (minimum):
  - rule_id
  - motion_type
  - condition (testable)
  - allowed (bool)
  - severity_if_broken (S0|S1|S2|S3)
- VALIDATION:
  - if continuity_level != NONE then continuity_rules non-empty
  - motion_rules non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/VIDEO/VIDEO_GEN/CONTINUITY_MOTION_CONSTRAINT_SET.md

---

ARTIFACT: VIDEO_BATCH_PLAN
- MUST:
  - batch_id
  - version
  - blueprint_ref
  - clip_list[] (non-empty)
  - seed_plan (required)
  - naming_rule (required)
  - variance_bounds (required)
  - checks[] (non-empty)
- CLIP LIST ITEM (minimum):
  - clip_id
  - purpose (testable)
  - derived_from_shot_id (optional)
  - duration_target
  - allowed_changes[] (optional)
  - forbidden_changes[] (optional)
  - seed (optional)
- SEED PLAN (minimum):
  - mode (FIXED|LIST|DERIVED)
  - seeds[] (optional)
  - derivation_rule (optional)
- VARIANCE BOUNDS (minimum):
  - max_style_drift (0..100)
  - max_lighting_drift (0..100)
  - max_motion_drift (0..100)
- VALIDATION:
  - clip_list non-empty
  - naming_rule present
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/VIDEO/VIDEO_GEN/VIDEO_BATCH_PLAN.md

---

ARTIFACT: VIDEO_GEN_GATES_REPORT
- MUST:
  - report_id
  - version
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
- Minimum required gates:
  - G1_BLUEPRINT_MISSING (S0)
  - G2_BINDINGS_MISSING (S1)
  - G3_DURATION_INVALID (S0)
  - G4_CONTINUITY_RULES_MISSING (S0 if continuity_level!=NONE)
  - G5_SEED_POLICY_MISSING (S0)
  - G6_MONTAGE_LEAK (S1)
  - G7_CANON_INJECTION (S0)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/VIDEO/VIDEO_GEN/VIDEO_GEN_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load shot plan + style + lighting + optional atmosphere.
2) Build clip blueprint:
   - duration bounds, motion policy, bindings, control params
3) Build continuity/motion constraint set:
   - continuity level and rules between adjacent clips
4) Build batch plan:
   - clip list, seed plan, naming, variance bounds
5) Run gates:
   - missing bindings, invalid durations, montage leak, canon injection, missing seeds
6) Emit artifacts.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: missing blueprint or required fields.
- S0-2: invalid duration bounds.
- S0-3: continuity rules missing when continuity_level != NONE.
- S0-4: missing seed policy (no reproducibility).
- S0-5: canon injection detected.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- camera engine provides shot plan and lens/move constraints
- art style + lighting provide render and emphasis constraints
- composition provides hierarchy constraints (optional)

Downstream:
- editing/montage engine consumes generated clips and owns ordering/cuts
- sound/music engines may later replace placeholders with produced audio
- QA validates generated clips against gates and variance bounds

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family template:
  08_KNOWLEDGE_PRODUCTION_ENGINES/00__TEMPLATE__ENGINE__KNOWLEDGE_PRODUCTION_ENGINES.md
- Family README:
  08_KNOWLEDGE_PRODUCTION_ENGINES/00__README__KNOWLEDGE_PRODUCTION_ENGINES.md

--- END.

LOCK: OPEN
