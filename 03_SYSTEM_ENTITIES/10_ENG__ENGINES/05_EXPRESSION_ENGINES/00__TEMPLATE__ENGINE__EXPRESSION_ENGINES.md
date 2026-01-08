# EXPRESSION ENGINES — ENGINE TEMPLATE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/05_EXPRESSION_ENGINES/00__TEMPLATE__ENGINE__EXPRESSION_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: TEMPLATE
FAMILY: 05_EXPRESSION_ENGINES
CLASS: EXPRESSION (L3)
LEVEL: L3
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.EXP.TPL.ENGINE.001
OWNER: SYSTEM
ROLE: Mandatory template for EXPRESSION engines. Defines event-mechanics primitives (event/cause-effect/conflict/turning points), enforces strict boundaries, mini-contract law, output schemas, and prevents overlaps with Narrative/Character/World/Production and Governance/CORE.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Expression engine template standardized: canonical header schema, strict mini-contract, event-mechanics boundaries, output schemas, and S0 blockers."
- REASON: "Stop confusion between story structure (Narrative) and event mechanics (Expression)."
- IMPACT: "Expression engines become deterministic building blocks for ORC pipelines and production outputs."
- CHANGE_ID: UE.CHG.2026-01-08.EXP.TPL.ENGINE.001

---

## 0) HOW TO USE (MANDATORY)

1) Copy this template to create a new engine file in this family.
2) Replace placeholders strictly (title, FILE path, UID, ROLE).
3) Fill MINI-CONTRACT with concrete artifacts (no vague words).
4) Declare boundaries to avoid overlap with:
   - CORE (system identity/state/lifecycle)
   - GOVERNANCE (authority/pipeline/audit)
   - NARRATIVE (meaning/structure/continuity)
   - CHARACTER (psychology/motivation/dialogue)
   - WORLD (laws/economy/tech/ecology)
   - PRODUCTION (camera/editing/sound implementation)
5) Add raw-only references where index navigation requires it.

Rule:
- Missing required sections => engine is incomplete (non-canon).

---

## 1) ENGINE FILE TEMPLATE (COPY FROM HERE)

# <ENGINE TITLE> (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/05_EXPRESSION_ENGINES/NN__<ENGINE_NAME>_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 05_EXPRESSION_ENGINES
CLASS: EXPRESSION (L3)
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 0.1.0
UID: UE.ENG.EXP.<ENGINE_KEY>.001
OWNER: SYSTEM
ROLE: <one sentence: what event-mechanics capability this engine defines and guarantees>

CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR|MIGRATION|EMERGENCY
- SUMMARY: "<what changed / what was defined>"
- REASON: "<why>"
- IMPACT: "<what this affects>"
- CHANGE_ID: UE.CHG.YYYY-MM-DD.EXP.<ENGINE_KEY>.<SEQ>

---

## 0) PURPOSE (LAW)

- Define the mechanics capability this engine owns (strict).
- Define guarantees (bullets).
- Define non-goals (explicit).

---

## 1) NON-GOALS (HARD)

This engine does NOT:
- define story meaning/structure/continuity as primary (NARRATIVE owns)
- define character psyche/motivation/dialogue as primary (CHARACTER owns)
- define world laws/constraints as primary (WORLD owns)
- define production implementation (camera/editing/sound) as primary (PRODUCTION owns)
- define authority/approvals/pipeline/audit/memory (GOVERNANCE owns)
- define system identity/state/lifecycle (CORE owns)

---

## 2) MINI-CONTRACT (MANDATORY)

CONSUMES:
- <1–7 inputs; named artifacts>
  - Example: SCENE_BLUEPRINT, CHARACTER_CONSTRAINTS, WORLD_RULES, TIMELINE_CONTEXT

PRODUCES:
- <1–7 outputs; reusable mechanics artifacts>
  - Example: EVENT_LIST, CAUSE_EFFECT_GRAPH, CONFLICT_MODEL, TURNING_POINT_SET

DEPENDS_ON:
- <engine paths> or []
  - (Expression may consume Narrative/Character/World outputs, but must not redefine them)

OUTPUT_TARGET:
MANDATORY:
- <project storage targets, e.g. 05_PROJECTS/...>

OPTIONAL:
- <assistive notes; never overrides canon>

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)

Expression defines mechanics primitives:
- EVENT (atomic happening)
- CAUSE_EFFECT (causal relationship)
- CONFLICT (opposing forces over a stake)
- TURNING_POINT (state-changing event)
- CLIMAX / RESOLUTION (mechanical phases, not meaning by themselves)

Do not redefine narrative meaning or theme: that belongs to Narrative family.

---

## 4) BOUNDARIES (ANTI-DUPLICATION)

IN SCOPE:
- mechanics of events, causality, conflict dynamics, escalation/de-escalation
- scheduling/ordering constraints (as mechanics)

OUT OF SCOPE (HARD):
- “why it matters” (theme/meaning) → Narrative
- “who the person is” (psyche) → Character
- “what the world allows” (laws) → World
- “how it looks/sounds on screen” → Production

Collision rule:
- If a mechanic requires meaning, accept meaning as an input artifact, not a definition.

---

## 5) RULESET (THE LAW)

Write numbered rules using MUST/FORBIDDEN/ALLOWED:
- R1 (HARD): ...
- R2 (HARD): ...
- R3 (SOFT): ...

Include:
- strict sets (allowed event types if any)
- invariants (graph must be acyclic unless justified)
- stop conditions (blockers)

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

For each produced artifact:

ARTIFACT: <NAME>
- MUST: <fields list>
- OPTIONAL: <fields list>
- VALIDATION: <how to detect missing/invalid>
- STORAGE: <target path rule>

Examples:
ARTIFACT: CAUSE_EFFECT_GRAPH
- MUST: nodes[], edges[], edge_type, assumptions[], confidence?
- VALIDATION: missing nodes => invalid; dangling edges => invalid

---

## 7) PIPELINE (DETERMINISTIC)

1) Validate inputs (constraints from Narrative/Character/World)
2) Generate mechanics structure (events/edges/conflicts)
3) Validate mechanics invariants
4) Emit output artifacts with schema
5) Provide integration notes for ORC sequencing (optional)

---

## 8) S0 BLOCKERS (STOP)

- S0-1: Engine claims ownership of narrative meaning/structure.
- S0-2: Engine outputs violate world law constraints (must be rejected or routed).
- S0-3: Output artifacts missing required schema fields.
- S0-4: Hidden dependencies not declared in MINI-CONTRACT.

---

## 9) INTEGRATION (SYSTEM FIT)

- Inputs typically come from Narrative/Character/World families.
- Outputs feed Narrative continuity checks and Production realization steps.
- ORC pipelines often sequence Expression after Narrative blueprints.

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)

- <raw links>

--- END.

---

## 2) TEMPLATE QUALITY CHECK (FAST)

Before setting a new engine ACTIVE:
- [ ] Header schema correct
- [ ] MINI-CONTRACT concrete
- [ ] Boundaries explicit (Narrative vs Expression clearly separated)
- [ ] Output schemas defined
- [ ] S0 blockers listed
