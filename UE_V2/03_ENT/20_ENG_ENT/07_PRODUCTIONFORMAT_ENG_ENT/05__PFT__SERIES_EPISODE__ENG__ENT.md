# SERIES & EPISODE ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/07_PRODUCTION_FORMAT_ENGINES/05__SERIES_EPISODE_ENG.md
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
UID: UE.ENG.PROD.FORMAT.SERIES.EPISODE.001
OWNER: SYSTEM
ROLE: Defines deterministic series format planning: season/episode unit models, episode sizing proxies, structural expectations, cliff/recap constraints, deliverable specs, and compliance gates.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Series & Episode Engine created: season/episode plan schema, unit sizing, structural expectations, and compliance gates."
- REASON: "Series medium needs unit planning different from book/short/youtube/game."
- IMPACT: "Projects can produce auditable season/episode plans aligned with format constraints."
- CHANGE_ID: UE.CHG.2026-01-08.PROD.FORMAT.SERIES.EPISODE.001

---

## 0) PURPOSE (LAW)
This engine owns **SERIES format constraints and planning**:
- defines season + episode units
- defines episode sizing proxies (minutes/scenes/beats) as ranges
- defines structural expectations (open/close patterns, recap/cliff constraints)
- emits SERIES_PLAN + EPISODE_UNIT_MODEL + DELIVERABLE_SPEC with gates

Hard rule:
- This engine plans constraints; it does NOT write scripts.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- write episode scripts/scenes (narrative engines)
- define montage/editing rhythm (production editing engine)
- define style palettes (style family)
- define world laws or character psychology as primary
- define distribution/marketing packaging

Also forbidden:
- treating episode length as exact runtime requirements (only proxies/ranges here).

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- FORMAT_CONSTRAINT_PACKAGE (required)
- UNIT_SIZING_RULES (required; format=SERIES)
- GENRE_PROFILE (optional)
- GENRE_BLEND_PROFILE (optional)
- TONE_PROFILE (optional)
- STORY_STRUCTURE (optional)
- TURNING_POINT_SET (optional)
- CLIMAX_SET (optional)

PRODUCES:
- SERIES_PLAN
- EPISODE_UNIT_MODEL
- SEASON_STRUCTURE_RULES
- SERIES_DELIVERABLE_SPEC
- SERIES_GATES_REPORT

DEPENDS_ON:
- [07_PRODUCTION_FORMAT_ENGINES/03__FORMAT_ADAPTATION_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/FORMAT/SERIES/
OPTIONAL:
- KB/FORMAT/SERIES (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Season: collection of episodes under a unified arc constraint.
- Episode: delivery unit with beginning/middle/end constraints.
- Episode Sizing Proxy: MINUTES|SCENES|BEATS.
- Cliff Constraint: explicit rule about end-of-episode tension/closure.
- Recap Constraint: rule about episode open context refresh.

Enums (baseline):
- unit_size_proxy: MINUTES|SCENES|BEATS
- scope: SERIES|SEASON|EPISODE
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- episode/season unit models and sizing ranges
- season/episode plan with order indexes
- structural rules (recap/cliff/open/close constraints)
- deliverable spec and gates

OUT OF SCOPE (HARD):
- writing scenes/scripts/dialogue
- narrative meaning and plot decisions
- editing/montage and production execution recipes

COLLISION RULE:
- If request is “write episode script” → narrative scene engines
- If request is “shorts/vertical series” → short content engine
- If request is “youtube longform” → youtube longform engine
- If request is “game quest chain” → game narrative engine

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: EPISODE_UNIT_MODEL defines required fields and sizing proxy.
R2 (HARD) MUST: SERIES_PLAN defines seasons and ordered episodes (non-empty).
R3 (HARD) MUST: SEASON_STRUCTURE_RULES define recap/cliff/open-close constraints as testable rules.
R4 (HARD) MUST: SERIES_DELIVERABLE_SPEC defines required components and checks.
R5 (HARD) FORBIDDEN: plan that is only a list without unit model + sizing + structural rules.
R6 (SOFT) SHOULD: allow optional “mid-season pivot” markers (as constraints, not content).
R7 (HARD) MUST: gates report validates sizing bounds and constraint conflicts.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: EPISODE_UNIT_MODEL
- MUST:
  - episode_model_id
  - version
  - unit_size_proxy (MINUTES|SCENES|BEATS)
  - required_fields[] (non-empty)
  - checks[] (non-empty)
- REQUIRED FIELD (baseline):
  - episode_id
  - season_id
  - order_index
  - purpose (testable)
  - target_size (proxy number)
  - size_bounds (min,max)
  - open_constraint_refs[] (optional)
  - close_constraint_refs[] (optional)
  - obligations_refs[] (optional)
  - notes
- VALIDATION:
  - unit_size_proxy matches UNIT_SIZING_RULES
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/FORMAT/SERIES/EPISODE_UNIT_MODEL.md

ARTIFACT: SEASON_STRUCTURE_RULES
- MUST:
  - rules_id
  - version
  - rules[] (non-empty)
  - patterns[] (optional)
  - checks[] (non-empty)
- RULE (minimum):
  - rule_id
  - type (MUST|FORBIDDEN|ALLOWED)
  - scope (SERIES|SEASON|EPISODE)
  - statement (testable)
  - severity_if_broken (S0|S1|S2|S3)
- PATTERN (optional):
  - pattern_id
  - description
  - where_applies (scope)
- VALIDATION:
  - at least one rule for EPISODE open
  - at least one rule for EPISODE close (cliff/closure policy)
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/FORMAT/SERIES/SEASON_STRUCTURE_RULES.md

ARTIFACT: SERIES_PLAN
- MUST:
  - series_plan_id
  - version
  - sizing_rules_ref
  - format_constraints_ref
  - seasons[] (non-empty)
  - episodes[] (non-empty; ordered within seasons)
  - checks[] (non-empty)
- SEASON (minimum):
  - season_id
  - order_index
  - episode_count_target (optional)
  - arc_constraints_refs[] (optional)
  - notes
- EPISODE (minimum):
  - episode_id
  - season_id
  - order_index
  - purpose
  - target_size
  - size_bounds
  - constraint_refs[] (genre/format/style refs)
  - structural_rule_refs[] (open/close/recap/cliff)
  - notes
- VALIDATION:
  - episodes have unique order_index within each season
  - target_size within size_bounds
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/FORMAT/SERIES/SERIES_PLAN.md

ARTIFACT: SERIES_DELIVERABLE_SPEC
- MUST:
  - deliverable_id
  - version
  - required_components[] (non-empty)
  - quality_checks[] (non-empty)
- REQUIRED COMPONENT (baseline examples):
  - series_bible_stub (optional)
  - season_episode_plan
  - episode_unit_model
  - structure_rules
  - metadata_block (title, version)
- QUALITY CHECK (minimum):
  - check_id
  - description
  - severity (S0|S1|S2|S3)
- VALIDATION:
  - required_components non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/FORMAT/SERIES/SERIES_DELIVERABLE_SPEC.md

ARTIFACT: SERIES_GATES_REPORT
- MUST:
  - report_id
  - version
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
  - recommended_repairs[] (required if S0)
- Minimum required gates:
  - G1_SIZING_RULES_MISSING (S0)
  - G2_SEASONS_OR_EPISODES_EMPTY (S0)
  - G3_SIZE_OUT_OF_BOUNDS (S1)
  - G4_OPEN_CLOSE_RULES_MISSING (S0)
  - G5_DELIVERABLE_INCOMPLETE (S0)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/FORMAT/SERIES/SERIES_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load format package + sizing rules (SERIES).
2) Instantiate episode unit model and season structure rules.
3) Build series plan:
   - season count (optional) + ordered episodes with targets and bounds
4) Bind constraint refs:
   - genre/blend/style refs applied to seasons/episodes
5) Define deliverable spec and checks.
6) Run gates and emit outputs.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: missing sizing rules or proxy mismatch.
- S0-2: seasons[] or episodes[] empty.
- S0-3: open/close structural rules missing.
- S0-4: deliverable spec incomplete.
- S0-5: produced artifacts missing schema fields.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- format adaptation provides translated constraints and sizing rules

Downstream:
- narrative engines can write episodes and scene packs following plan constraints
- production engines (video) can schedule production using episode plan (separate layer)
- QA/consistency engines validate scripts against plan and rules

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family README:
  07_PRODUCTION_FORMAT_ENGINES/00__README__PRODUCTION_FORMAT_ENGINES.md
- Family template:
  07_PRODUCTION_FORMAT_ENGINES/00__TEMPLATE__ENGINE__PRODUCTION_FORMAT_ENGINES.md

--- END.

LOCK: OPEN
