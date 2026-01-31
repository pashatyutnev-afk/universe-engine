# SYSTEM SHOCK ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/05_EXPRESSION_ENGINES/07__SYSTEM_SHOCK_ENG.md
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 05_EXPRESSION_ENGINES
CLASS: EXPRESSION (L3)
LEVEL: L3
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.EXP.SYSTEM.SHOCK.001
OWNER: SYSTEM
ROLE: Models system-level shocks as expression primitives: destabilizing events that propagate across domains (world/civ/economy/relationships). Produces shock specs, propagation rules, and recovery constraints.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "System Shock Engine created: shock schema, propagation graph, severity gates, and recovery constraints."
- REASON: "Need a standardized way to represent cascading disruptions beyond normal conflict."
- IMPACT: "Large-scale disruption becomes deterministic; downstream engines can react consistently."
- CHANGE_ID: UE.CHG.2026-01-08.EXP.SYSTEM.SHOCK.001

---

## 0) PURPOSE (LAW)
This engine owns the **SYSTEM_SHOCK primitive**:
- defines a shock as an event (or event cluster) that causes cascading changes
- specifies propagation rules (what spreads, where, and why)
- defines impact surfaces (world/civ/economy/conflict/relationships)
- defines recovery constraints (what must be done before stability returns)

Hard rule:
- A shock must be modeled as explicit propagation, not “everything is worse now”.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- define base events (event engine owns)
- replace world environmental shocks modeling (world ecology engine owns world-state; this engine models shock as expression layer)
- define narrative pacing/structure (narrative family)
- define conflict escalation as primary (conflict engine)
- define geopolitics/economy/tech internals (world engines)
- define production depiction

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- EVENT_PACK
- EVENT_TYPE_REGISTRY
- CAUSAL_GRAPH (optional but recommended)
- WORLD_LAWSET (optional)
- TIMELINE_EPOCH_MODEL (optional)
- SYSTEM_CONTEXT_MAP (optional: which subsystems exist)

PRODUCES:
- SYSTEM_SHOCK_SET
- SHOCK_PROPAGATION_RULES
- SHOCK_RECOVERY_CONSTRAINTS
- SHOCK_VALIDATION_REPORT

DEPENDS_ON:
- [05_EXPRESSION_ENGINES/01__EVENT_ENG, 05_EXPRESSION_ENGINES/02__CAUSE_EFFECT_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/EXPRESSION/SYSTEM_SHOCK/
OPTIONAL:
- KB/SYSTEM_SHOCK (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- System Shock: destabilizing disturbance that propagates across multiple subsystems.
- Subsystem: a domain surface (WORLD_ENV, CIV, GEO, ECONOMY, TECH, INFO, RELATIONSHIPS).
- Propagation: rule mapping shock impact from one subsystem/scope to another.
- Shock Window: minimal set of events defining the shock onset.
- Recovery Constraint: requirement to return to stable regime.

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- shock specification from events
- propagation rules and scope mapping
- recovery constraints and stop conditions
- validation report

OUT OF SCOPE (HARD):
- designing world epoch transitions (timeline engine)
- defining environment/ecology laws (world ecology engine)
- defining conflict/climax/resolution primitives (other expression engines)
- defining resource economy mechanics (economy engine)

COLLISION RULE:
- If shock is fundamentally world-state regime shift → world timeline/ecology engines own the state model; this engine emits expression-layer shock artifacts linked to them.
- If shock is a conflict peak → climax engine; shock can exist but must not duplicate climax ownership.

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: each shock references source event_ids (onset window).
R2 (HARD) MUST: shock defines impacted subsystems (>=2) and propagation rules.
R3 (HARD) MUST: shock defines severity and scope (LOCAL/REGIONAL/GLOBAL/SYSTEM).
R4 (HARD) MUST: recovery constraints exist for S0/S1 shocks.
R5 (HARD) FORBIDDEN: shock described without propagation (“and then chaos everywhere”).
R6 (HARD) MUST: propagation rules are testable and cite conditions/constraints.
R7 (SOFT) SHOULD: include damping factors (resilience, buffers).
R8 (HARD) MUST: if world lawset provided, shock cannot require impossible causes/effects.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: SYSTEM_SHOCK_SET
- MUST:
  - set_id
  - version
  - shocks[] (non-empty)
  - checks[] (non-empty)
- SHOCK (minimum):
  - shock_id
  - title
  - onset_window:
    - event_ids[] (1..5)
    - window_mode (SINGLE|CLUSTER)
  - shock_type (enum: ENVIRONMENTAL|BIOLOGICAL|TECH_FAILURE|MAGIC_BACKLASH|POLITICAL_COLLAPSE|RESOURCE_CRASH|INFO_BLACKOUT|WAR_EXPANSION|SOCIAL_RUPTURE)
  - scope (LOCAL|REGIONAL|GLOBAL|SYSTEM)
  - severity (S0|S1|S2|S3)
  - impacted_subsystems[] (non-empty; >=2)
  - propagation_ref
  - recovery_ref
  - notes
- CHECK (minimum):
  - check_id
  - description
  - severity
- VALIDATION:
  - onset events exist
  - impacted_subsystems >=2
  - S0/S1 have recovery_ref
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/EXPRESSION/SYSTEM_SHOCK/SYSTEM_SHOCK_SET.md

---

ARTIFACT: SHOCK_PROPAGATION_RULES
- MUST:
  - propagation_id
  - version
  - rules[] (non-empty)
  - checks[] (non-empty)
- RULE (minimum):
  - rule_id
  - shock_id
  - from_subsystem (WORLD_ENV|CIV|GEO|ECONOMY|TECH|INFO|RELATIONSHIPS)
  - to_subsystem (WORLD_ENV|CIV|GEO|ECONOMY|TECH|INFO|RELATIONSHIPS)
  - mechanism (testable description)
  - conditions[] (optional but recommended)
  - expected_effects[] (non-empty)
  - time_delay_proxy (optional)
  - damping_factors[] (optional)
  - severity_if_missing (S0|S1|S2|S3)
- CONDITION (minimum):
  - type (THRESHOLD|DEPENDENCY|CAPACITY|LAW|CONTROL)
  - expression (testable)
- VALIDATION:
  - every shock has at least one propagation rule
  - expected_effects non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/EXPRESSION/SYSTEM_SHOCK/SHOCK_PROPAGATION_RULES.md

---

ARTIFACT: SHOCK_RECOVERY_CONSTRAINTS
- MUST:
  - recovery_id
  - version
  - constraints[] (non-empty for S0/S1 shocks)
  - phases[] (optional)
  - checks[] (non-empty)
- CONSTRAINT (minimum):
  - constraint_id
  - shock_id
  - requirement (testable)
  - subsystem (WORLD_ENV|CIV|GEO|ECONOMY|TECH|INFO|RELATIONSHIPS)
  - severity_if_unmet (S0|S1|S2|S3)
  - verification (how to know it’s met)
  - route_to (engine pointer; e.g., world engines/economy/conflict)
- PHASE (minimum):
  - phase_id
  - name
  - entry_conditions[]
  - exit_conditions[]
  - expected_state (short)
- VALIDATION:
  - any S0 constraint includes verification + route_to
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/EXPRESSION/SYSTEM_SHOCK/SHOCK_RECOVERY_CONSTRAINTS.md

---

ARTIFACT: SHOCK_VALIDATION_REPORT
- MUST:
  - report_id
  - version
  - issues[] (can be empty)
  - severity_summary
  - recommended_repairs[] (required if S0 issues exist)
- ISSUE (minimum):
  - issue_id
  - type (MISSING_PROPAGATION|MISSING_RECOVERY|UNKNOWN_EVENTS|LAW_VIOLATION|VAGUE_EFFECTS)
  - ref_ids[] (shock/rule/event ids)
  - severity (S0|S1|S2|S3)
  - description
  - fix_route (engine pointer)
- REPAIR (minimum):
  - issue_id
  - suggestion
  - route_to (engine pointer)
- VALIDATION:
  - S0 issues must have repairs
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/EXPRESSION/SYSTEM_SHOCK/SHOCK_VALIDATION_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Validate input events (Event gates).
2) Detect shock candidates:
   - high-severity events
   - multi-subsystem impacts
   - cascading causal patterns (if causal graph exists)
3) Define shock onset window and type.
4) Define propagation rules:
   - from subsystem to subsystem with conditions and effects
5) Define recovery constraints:
   - minimum requirements per subsystem
6) Validate against world lawset (if present).
7) Emit artifacts (set + propagation + recovery + report).

---

## 8) S0 BLOCKERS (STOP)
- S0-1: shock references unknown onset event ids.
- S0-2: impacted_subsystems has fewer than 2 entries.
- S0-3: missing propagation rules for a shock.
- S0-4: S0/S1 shock missing recovery constraints.
- S0-5: propagation implies impossible effects under world lawset (if provided).

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- event engine (onset window)
- cause-effect engine (optional propagation evidence)

Downstream:
- economy/resource engine (scarcity and bottleneck reactions)
- geopolitics/conflict engines (escalation responses)
- world timeline/ecology engines (if shock becomes epoch regime shift)
- narrative engines (use shock as driver while respecting propagation and recovery)

Governance:
- if a shock redefines canon world invariants, route via governance pipeline.

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family template:
  05_EXPRESSION_ENGINES/00__TEMPLATE__ENGINE__EXPRESSION_ENGINES.md

--- END.

LOCK: OPEN
