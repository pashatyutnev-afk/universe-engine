# GAME NARRATIVE ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/07_PRODUCTION_FORMAT_ENGINES/08__GAME_NARRATIVE_ENG.md
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
UID: UE.ENG.PROD.FORMAT.GAME.NARRATIVE.001
OWNER: SYSTEM
ROLE: Defines deterministic game narrative format constraints: quest/mission unit model, branching policy, player agency constraints, fail-state rules, progression gates, deliverable spec, and compliance checks (without implementing gameplay systems).

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Game Narrative Engine created: quest unit model, branching/agency policy, progression gates, deliverable spec, and compliance report."
- REASON: "Game narrative requires interactive constraints and branching policies absent in book/series/video formats."
- IMPACT: "Projects can plan interactive narratives deterministically while preserving canon and constraints."
- CHANGE_ID: UE.CHG.2026-01-08.PROD.FORMAT.GAME.NARRATIVE.001

---

## 0) PURPOSE (LAW)
This engine owns **GAME narrative format constraints**:
- defines quest/mission as primary units
- defines branching policy and player agency constraints (what can vary)
- defines fail-state and retry rules as constraints
- defines progression gates and unlock logic at narrative level
- emits deliverable spec and compliance gates

Hard rule:
- This engine defines narrative interaction constraints; it does NOT implement gameplay systems or mechanics.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- implement gameplay mechanics, combat systems, economy systems (outside this engine)
- write dialogue/scripts (narrative/character engines)
- define world laws (world family)
- define production editing/camera/sound implementation (media production family)
- define style palettes (style family)

Also forbidden:
- branching that changes canon facts without governance routing.

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- FORMAT_CONSTRAINT_PACKAGE (required)
- UNIT_SIZING_RULES (required; format=GAME)
- GENRE_PROFILE (optional)
- GENRE_BLEND_PROFILE (optional)
- WORLD_LAWSET (optional)
- EVENT_PACK (optional)
- CAUSAL_GRAPH (optional)

PRODUCES:
- QUEST_UNIT_MODEL
- BRANCHING_AGENCY_POLICY
- PROGRESSION_GATE_MODEL
- GAME_DELIVERABLE_SPEC
- GAME_GATES_REPORT

DEPENDS_ON:
- [07_PRODUCTION_FORMAT_ENGINES/03__FORMAT_ADAPTATION_ENG]
(soft) [05_EXPRESSION_ENGINES/02__CAUSE_EFFECT_ENG] for dependency sanity checks

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/FORMAT/GAME/
OPTIONAL:
- KB/FORMAT/GAME (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Quest Unit: interactive narrative unit (mission/quest) with objectives, gates, and outcomes.
- Branch: alternative path chosen by player or state.
- Agency: what player can decide that changes outcomes (bounded).
- Fail-State: condition that fails a quest; defines retry/alternate outcomes.
- Progression Gate: requirement to unlock next quests (state, knowledge, items, reputation, access).
- Canon-Safe: branching that does not contradict canon facts; either converges or stays within allowed variance.

Enums (baseline):
- unit_size_proxy: STEPS|SCENES|BEATS
- branch_type: CHOICE|STATE_BASED|SKILL_CHECK|RANDOM_VARIANT
- fail_policy: RETRY|FAIL_FORWARD|LOCKOUT|ALTERNATE_ROUTE
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- quest unit model and sizing proxies
- branching/agency policies and bounds
- fail-state and retry policies (narrative layer)
- progression gate model and compliance checks
- deliverable spec for a game narrative plan

OUT OF SCOPE (HARD):
- gameplay mechanics implementation (combat, crafting, economy)
- writing dialogue and scene text
- world canon changes (governance required)
- production execution (cinematics editing/camera)

COLLISION RULE:
- If request is “implement gameplay system” → outside this engine (game systems layer)
- If request is “write quest dialogue” → narrative/character engines
- If request is “world state rules for branching” → world engines + governance if canon impacted
- If request is “cinematic cutscene montage” → production engines

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: QUEST_UNIT_MODEL defines required quest fields and sizing proxy.
R2 (HARD) MUST: BRANCHING_AGENCY_POLICY defines what can branch and how it remains canon-safe.
R3 (HARD) MUST: fail-state policy exists per quest type (retry/fail-forward/lockout/alternate).
R4 (HARD) MUST: PROGRESSION_GATE_MODEL defines unlock requirements and dependencies.
R5 (HARD) FORBIDDEN: branching that creates canon contradictions without routing to governance.
R6 (SOFT) SHOULD: define convergence rules (branches rejoin) to control complexity.
R7 (HARD) MUST: gates report validates missing policies and canon-safety.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: QUEST_UNIT_MODEL
- MUST:
  - quest_model_id
  - version
  - unit_size_proxy (STEPS|SCENES|BEATS)
  - required_fields[] (non-empty)
  - checks[] (non-empty)
- REQUIRED FIELD (baseline):
  - quest_id
  - title_stub (optional)
  - objective (testable)
  - steps_or_beats[] (optional)
  - target_size (proxy number)
  - size_bounds (min,max)
  - prerequisites[] (optional: gate refs)
  - outcomes[] (non-empty)
  - fail_states[] (optional)
  - branch_points[] (optional)
  - canon_safety (CONVERGES|CONSTRAINED_VARIANCE|ISOLATED_SIDE_PATH)
  - notes
- OUTCOME (minimum):
  - outcome_id
  - type (SUCCESS|PARTIAL|FAIL_FORWARD|ALT_ROUTE)
  - resulting_state_delta (testable)
- VALIDATION:
  - outcomes non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/FORMAT/GAME/QUEST_UNIT_MODEL.md

ARTIFACT: BRANCHING_AGENCY_POLICY
- MUST:
  - policy_id
  - version
  - allowed_branch_types[] (non-empty)
  - agency_bounds[] (non-empty)
  - canon_safety_rules[] (non-empty)
  - convergence_policy (optional but recommended)
  - checks[] (non-empty)
- AGENCY BOUND (minimum):
  - bound_id
  - applies_to (quest_id or global)
  - what_can_change (testable)
  - what_cannot_change (testable; canon-safe invariant)
  - max_variants (optional)
- CANON SAFETY RULE (minimum):
  - rule_id
  - statement (testable)
  - severity_if_broken (S0|S1|S2|S3)
  - route_to (GOVERNANCE pointer if violated)
- CONVERGENCE POLICY (optional):
  - policy
  - max_parallel_branches (optional)
  - rejoin_requirement (testable)
- VALIDATION:
  - allowed_branch_types non-empty
  - canon_safety_rules non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/FORMAT/GAME/BRANCHING_AGENCY_POLICY.md

ARTIFACT: PROGRESSION_GATE_MODEL
- MUST:
  - gate_model_id
  - version
  - gates[] (non-empty)
  - dependency_rules[] (optional)
  - checks[] (non-empty)
- GATE (minimum):
  - gate_id
  - unlocks[] (quest_ids)
  - requirements[] (non-empty)
  - verification (how to test)
  - severity_if_missing (S0|S1|S2|S3)
- REQUIREMENT (minimum):
  - type (STATE|ITEM|KNOWLEDGE|ACCESS|RELATION|SKILL|TIME_WINDOW)
  - expression (testable)
- VALIDATION:
  - each gate unlocks at least one quest
  - requirements non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/FORMAT/GAME/PROGRESSION_GATE_MODEL.md

ARTIFACT: GAME_DELIVERABLE_SPEC
- MUST:
  - deliverable_id
  - version
  - required_components[] (non-empty)
  - quality_checks[] (non-empty)
- REQUIRED COMPONENT (baseline examples):
  - quest_unit_model
  - branching_agency_policy
  - progression_gate_model
  - metadata_block (title, version)
- QUALITY CHECK:
  - check_id
  - description
  - severity (S0|S1|S2|S3)
- VALIDATION:
  - required_components non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/FORMAT/GAME/GAME_DELIVERABLE_SPEC.md

ARTIFACT: GAME_GATES_REPORT
- MUST:
  - report_id
  - version
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
  - recommended_repairs[] (required if S0)
- Minimum required gates:
  - G1_SIZING_RULES_MISSING (S0)
  - G2_QUEST_MODEL_INCOMPLETE (S0)
  - G3_BRANCH_POLICY_MISSING (S0)
  - G4_CANON_SAFETY_VIOLATION (S0)
  - G5_GATE_MODEL_MISSING (S0)
  - G6_DELIVERABLE_INCOMPLETE (S0)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/FORMAT/GAME/GAME_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load format package + sizing rules (GAME).
2) Create quest unit model (fields + outcomes + bounds).
3) Define branching/agency policy (allowed branch types, canon safety, convergence).
4) Define progression gate model (requirements and unlocks).
5) Define deliverable spec and QC checks.
6) Run gates (missing policies, canon safety).
7) Emit artifacts.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: missing sizing rules or invalid bounds.
- S0-2: quest model missing outcomes or required fields.
- S0-3: branching/agency policy missing or lacks canon-safety rules.
- S0-4: progression gates missing or invalid.
- S0-5: deliverable spec incomplete or schema fields missing.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- format adaptation provides translated constraints and sizing rules

Downstream:
- narrative engines can author quest content under constraints
- game systems layer can implement mechanics (outside this engine)
- QA/consistency engines validate quest graph, canon safety, and gate logic

Governance:
- any proposed canon-breaking branch must route to change control + audit.

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family README:
  07_PRODUCTION_FORMAT_ENGINES/00__README__PRODUCTION_FORMAT_ENGINES.md
- Family template:
  07_PRODUCTION_FORMAT_ENGINES/00__TEMPLATE__ENGINE__PRODUCTION_FORMAT_ENGINES.md

--- END.

LOCK: OPEN
