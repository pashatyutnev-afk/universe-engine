# YOUTUBE LONGFORM ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/07_PRODUCTION_FORMAT_ENGINES/07__YOUTUBE_LONGFORM_ENG.md
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
UID: UE.ENG.PROD.FORMAT.YT.LONGFORM.001
OWNER: SYSTEM
ROLE: Defines deterministic YouTube longform format constraints: segment unit model, retention-friendly structure constraints (as rules), sizing proxies, deliverable spec, and compliance gates (without editing implementation).

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "YouTube Longform Engine created: segment model, structure constraints, sizing rules, deliverable spec, and compliance gates."
- REASON: "YouTube longform has distinct structure (hook/retention loops/segmenting) different from series/book."
- IMPACT: "Projects can plan YouTube longform videos deterministically and validate format compliance."
- CHANGE_ID: UE.CHG.2026-01-08.PROD.FORMAT.YT.LONGFORM.001

---

## 0) PURPOSE (LAW)
This engine owns **YouTube longform format constraints**:
- defines video as segmented unit (HOOK -> SETUP -> BODY SEGMENTS -> PAYOFF -> OUTRO)
- defines retention constraints as *structure rules* (not editing recipes)
- defines sizing proxies (minutes/segments)
- emits deliverable spec and compliance gates

Hard rule:
- This engine constrains structure; it does NOT define editing/montage implementation.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- write the script (narrative engines)
- define editing/montage, pacing-by-cuts, B-roll specifics (production editing engine)
- define style palettes (style family)
- define marketing/distribution strategy
- define world/character canon content

Also forbidden:
- turning retention rules into manipulative tactics; constraints must be testable structure rules.

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- FORMAT_CONSTRAINT_PACKAGE (required)
- UNIT_SIZING_RULES (required; format=YOUTUBE_LONGFORM)
- GENRE_PROFILE (optional)
- GENRE_BLEND_PROFILE (optional)
- TONE_PROFILE (optional)
- EVENT_PACK (optional)
- CONFLICT_OBJECT_SET (optional)

PRODUCES:
- YT_SEGMENT_UNIT_MODEL
- YT_STRUCTURE_RULES
- YT_DELIVERABLE_SPEC
- YT_GATES_REPORT

DEPENDS_ON:
- [07_PRODUCTION_FORMAT_ENGINES/03__FORMAT_ADAPTATION_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/FORMAT/YOUTUBE_LONGFORM/
OPTIONAL:
- KB/FORMAT/YOUTUBE_LONGFORM (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Segment: planned unit within a video (hook, setup, segment, payoff, outro).
- Size Proxy: MINUTES|SEGMENTS|BEATS.
- Retention Rule: structure constraint that reduces drop-off risk (e.g., open loops, mid-commitments).
- Open Loop: declared unresolved question that must be paid by a later segment (constraint, not writing).
- Payoff: the segment that resolves main open loops.

Enums (baseline):
- unit_size_proxy: MINUTES|SEGMENTS|BEATS
- segment_type: HOOK|SETUP|SEGMENT|PAYOFF|OUTRO
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- segment unit model and bounds
- structure rules for longform retention (as constraints)
- deliverable spec and gates

OUT OF SCOPE (HARD):
- editing implementation (cuts, B-roll, sound mix)
- writing script text
- series planning across episodes (series engine)
- short vertical constraints (short engine)

COLLISION RULE:
- If request is “shorts/vertical” → `06__SHORT_CONTENT_ENG`
- If request is “series episodes” → `05__SERIES_EPISODE_ENG`
- If request is “editing rhythm and montage” → production editing engine
- If request is “tone/mood” → style engines

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: YT_SEGMENT_UNIT_MODEL defines segment fields and size proxy bounds.
R2 (HARD) MUST: YT_STRUCTURE_RULES include HOOK and PAYOFF MUST rules.
R3 (HARD) MUST: define loop policy: how open loops are created and when they must be paid.
R4 (HARD) FORBIDDEN: longform plan without loop payoff constraints.
R5 (HARD) MUST: gates validate size bounds and missing segment rules.
R6 (SOFT) SHOULD: allow multiple segment variants (A/B) within bounds.
R7 (HARD) MUST: remain compatible with FORMAT_CONSTRAINT_PACKAGE.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: YT_SEGMENT_UNIT_MODEL
- MUST:
  - yt_model_id
  - version
  - unit_size_proxy (MINUTES|SEGMENTS|BEATS)
  - bounds:
    - min
    - target
    - max
  - required_segment_types[] (non-empty)
  - segment_fields[] (non-empty)
  - checks[] (non-empty)
- SEGMENT FIELD (baseline):
  - segment_id
  - segment_type
  - purpose (testable)
  - target_size (proxy number)
  - size_bounds
  - open_loops_created[] (optional)
  - loops_paid[] (optional)
  - constraint_refs[] (optional)
- VALIDATION:
  - required_segment_types contains HOOK and PAYOFF
  - bounds valid and match UNIT_SIZING_RULES
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/FORMAT/YOUTUBE_LONGFORM/YT_SEGMENT_UNIT_MODEL.md

ARTIFACT: YT_STRUCTURE_RULES
- MUST:
  - rules_id
  - version
  - rules[] (non-empty)
  - loop_policy (required)
  - checks[] (non-empty)
- LOOP POLICY (minimum):
  - policy_id
  - max_open_loops (optional)
  - payoff_deadline (e.g., "by PAYOFF segment") (testable)
  - action_on_breach (FLAG|RESTRUCTURE|REMOVE_LOOP)
- RULE (minimum):
  - rule_id
  - segment_type (HOOK|SETUP|SEGMENT|PAYOFF|OUTRO)
  - type (MUST|FORBIDDEN|ALLOWED)
  - statement (testable)
  - severity_if_broken (S0|S1|S2|S3)
- VALIDATION:
  - at least one MUST for HOOK
  - at least one MUST for PAYOFF
  - loop_policy exists
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/FORMAT/YOUTUBE_LONGFORM/YT_STRUCTURE_RULES.md

ARTIFACT: YT_DELIVERABLE_SPEC
- MUST:
  - deliverable_id
  - version
  - required_components[] (non-empty)
  - quality_checks[] (non-empty)
- REQUIRED COMPONENT (baseline examples):
  - segment_unit_model
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
  - PROJECT_ARTIFACTS/<project>/FORMAT/YOUTUBE_LONGFORM/YT_DELIVERABLE_SPEC.md

ARTIFACT: YT_GATES_REPORT
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
  - G4_LOOP_POLICY_MISSING (S0)
  - G5_SIZE_OUT_OF_BOUNDS (S1)
  - G6_DELIVERABLE_INCOMPLETE (S0)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/FORMAT/YOUTUBE_LONGFORM/YT_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load format package + sizing rules (YOUTUBE_LONGFORM).
2) Create segment unit model:
   - required segment types and bounds
3) Create structure rules:
   - hook/loop/payoff constraints
4) Bind upstream constraint refs (genre/blend/style).
5) Define deliverable spec and QC checks.
6) Run gates and emit outputs.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: missing sizing rules or invalid bounds.
- S0-2: missing HOOK MUST rule.
- S0-3: missing PAYOFF MUST rule.
- S0-4: loop_policy missing.
- S0-5: deliverable spec incomplete or schema fields missing.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- format adaptation provides translated constraints and sizing rules

Downstream:
- narrative engines can write scripts following segment constraints
- production editing engines implement pacing/cuts (separate layer)
- QA engines validate final plan against gates and deliverable spec

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family README:
  07_PRODUCTION_FORMAT_ENGINES/00__README__PRODUCTION_FORMAT_ENGINES.md
- Family template:
  07_PRODUCTION_FORMAT_ENGINES/00__TEMPLATE__ENGINE__PRODUCTION_FORMAT_ENGINES.md

--- END.

LOCK: OPEN
