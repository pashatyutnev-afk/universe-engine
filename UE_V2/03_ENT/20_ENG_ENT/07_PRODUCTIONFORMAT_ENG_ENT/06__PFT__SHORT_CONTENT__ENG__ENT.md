# SHORT CONTENT ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/07_PRODUCTION_FORMAT_ENGINES/06__SHORT_CONTENT_ENG.md
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 07_PRODUCTION_FORMAT_ENGINES
CLASS: PRODUCTION (L3)
LEVEL: L3
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.PROD.FORMAT.SHORT.001
OWNER: SYSTEM
ROLE: Defines deterministic short-content format constraints (reels/shorts/vertical): unit sizing proxies, hook/payoff constraints, minimal structure rules, deliverable spec, and compliance gates.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Short Content Engine created: short unit model, hook/payoff constraints, deliverable spec, and compliance gates."
- REASON: "Short content has distinct constraints (hook speed, compressed structure) not covered by series/book."
- IMPACT: "Projects can plan short content deterministically and validate drift."
- CHANGE_ID: UE.CHG.2026-01-08.PROD.FORMAT.SHORT.001

---

## 0) PURPOSE (LAW)
This engine owns **SHORT content format constraints**:
- defines short as a single unit (or micro-sequence) with strict size bounds
- defines hook/payoff constraints as testable rules
- defines minimal structure constraints (open/turn/close) as constraints (not writing)
- emits deliverable spec and gates for compliance

Hard rule:
- This engine defines constraints for short format; it does NOT write scripts or edit videos.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- write short scripts/scenes (narrative engines)
- define editing/montage implementation (production editing engine)
- define style palettes (style family)
- define world/character canon content
- define distribution strategy

Also forbidden:
- treating hook/payoff as “clickbait”; must be expressed as structural constraints.

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- FORMAT_CONSTRAINT_PACKAGE (required)
- UNIT_SIZING_RULES (required; format=SHORT)
- GENRE_PROFILE (optional)
- GENRE_BLEND_PROFILE (optional)
- TONE_PROFILE (optional)
- EVENT_PACK (optional)
- CONFLICT_OBJECT_SET (optional)

PRODUCES:
- SHORT_UNIT_MODEL
- SHORT_STRUCTURE_RULES
- SHORT_DELIVERABLE_SPEC
- SHORT_GATES_REPORT

DEPENDS_ON:
- [07_PRODUCTION_FORMAT_ENGINES/03__FORMAT_ADAPTATION_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/FORMAT/SHORT/
OPTIONAL:
- KB/FORMAT/SHORT (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Short Unit: single compressed deliverable (one video short or micro-story).
- Size Proxy: SECONDS|BEATS|SCENES.
- Hook Constraint: rule for first segment’s function (attention capture).
- Payoff Constraint: rule for last segment’s function (resolution/insight/turn).
- Micro-Structure: OPEN -> TURN -> CLOSE (constraint skeleton).

Enums (baseline):
- unit_size_proxy: SECONDS|BEATS|SCENES
- segment: HOOK|BODY|PAYOFF
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- short unit model and size bounds
- hook/body/payoff structural constraints
- deliverable spec and compliance gates

OUT OF SCOPE (HARD):
- writing content
- editing implementation
- series planning (series engine)
- youtube longform planning (youtube engine)

COLLISION RULE:
- If request is “multi-episode vertical series” → series engine (or treat as series with short unit proxy)
- If request is “long YouTube episodes” → youtube longform engine
- If request is “write the hook line” → narrative engines (this engine only defines hook constraints)

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: SHORT_UNIT_MODEL defines required fields and size proxy bounds.
R2 (HARD) MUST: SHORT_STRUCTURE_RULES define hook/payoff constraints as testable rules.
R3 (HARD) MUST: deliverable spec includes required components and QC checks.
R4 (HARD) FORBIDDEN: short plan that lacks payoff constraint.
R5 (HARD) MUST: gates validate size bounds and structure completeness.
R6 (SOFT) SHOULD: allow multiple variants within bounds (A/B) as optional planning constraint.
R7 (HARD) MUST: remain compatible with FORMAT_CONSTRAINT_PACKAGE.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: SHORT_UNIT_MODEL
- MUST:
  - short_model_id
  - version
  - unit_size_proxy (SECONDS|BEATS|SCENES)
  - bounds:
    - min
    - target
    - max
  - required_fields[] (non-empty)
  - checks[] (non-empty)
- REQUIRED FIELD (baseline):
  - short_id
  - title_stub (optional)
  - purpose (testable)
  - hook_constraint_refs[] (required)
  - payoff_constraint_refs[] (required)
  - target_size
  - size_bounds
  - constraint_refs[] (optional)
  - notes
- VALIDATION:
  - bounds valid and match UNIT_SIZING_RULES
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/FORMAT/SHORT/SHORT_UNIT_MODEL.md

ARTIFACT: SHORT_STRUCTURE_RULES
- MUST:
  - rules_id
  - version
  - segment_rules[] (non-empty)
  - checks[] (non-empty)
- SEGMENT RULE (minimum):
  - rule_id
  - segment (HOOK|BODY|PAYOFF)
  - type (MUST|FORBIDDEN|ALLOWED)
  - statement (testable)
  - severity_if_broken (S0|S1|S2|S3)
- VALIDATION:
  - at least one MUST for HOOK
  - at least one MUST for PAYOFF
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/FORMAT/SHORT/SHORT_STRUCTURE_RULES.md

ARTIFACT: SHORT_DELIVERABLE_SPEC
- MUST:
  - deliverable_id
  - version
  - required_components[] (non-empty)
  - quality_checks[] (non-empty)
- REQUIRED COMPONENT (baseline examples):
  - short_unit_model
  - structure_rules
  - metadata_block (title, version)
  - export_targets (optional)
- QUALITY CHECK:
  - check_id
  - description
  - severity (S0|S1|S2|S3)
- VALIDATION:
  - required_components non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/FORMAT/SHORT/SHORT_DELIVERABLE_SPEC.md

ARTIFACT: SHORT_GATES_REPORT
- MUST:
  - report_id
  - version
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
  - recommended_repairs[] (required if S0)
- Minimum required gates:
  - G1_SIZING_RULES_MISSING (S0)
  - G2_HOOK_MISSING (S0)
  - G3_PAYOFF_MISSING (S0)
  - G4_SIZE_OUT_OF_BOUNDS (S1)
  - G5_DELIVERABLE_INCOMPLETE (S0)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/FORMAT/SHORT/SHORT_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load format package + sizing rules (SHORT).
2) Create short unit model (fields + bounds).
3) Create structure rules:
   - HOOK/BODY/PAYOFF constraints
4) Bind upstream constraints (refs to genre/blend/style).
5) Define deliverable spec and QC checks.
6) Run gates and emit outputs.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: missing sizing rules or invalid bounds.
- S0-2: missing HOOK MUST rule.
- S0-3: missing PAYOFF MUST rule.
- S0-4: deliverable spec incomplete.
- S0-5: produced artifacts missing schema fields.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- format adaptation provides translated constraints and sizing rules

Downstream:
- narrative engines can generate short scripts constrained by hook/payoff rules
- production engines can implement editing/visual language (separate layer)
- QA engines validate final short against deliverable spec and gates

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family README:
  07_PRODUCTION_FORMAT_ENGINES/00__README__PRODUCTION_FORMAT_ENGINES.md
- Family template:
  07_PRODUCTION_FORMAT_ENGINES/00__TEMPLATE__ENGINE__PRODUCTION_FORMAT_ENGINES.md

--- END.

LOCK: OPEN
