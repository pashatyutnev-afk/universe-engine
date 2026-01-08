# WORLD LAW ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/02__WORLD_LAW_ENG.md
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 04_DOMAIN_WORLD_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.DOM.WORLD.LAW.001
OWNER: SYSTEM
ROLE: Defines the world lawset: what is possible / impossible, causality constraints, invariants, exceptions, and verification rules that all downstream engines and narrative must respect.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "World Law Engine created: lawset schema, causality constraints, possibility matrix, exception protocol, and S0 gates."
- REASON: "World must have explicit 'physics' (including magic rules) to prevent arbitrary events."
- IMPACT: "Narrative and production consume deterministic possibility constraints; canon consistency improves."
- CHANGE_ID: UE.CHG.2026-01-08.DOM.WORLD.LAW.001

---

## 0) PURPOSE (LAW)
This engine owns **WORLD LAW** as deterministic constraints:
- defines what the world allows / forbids (possibility domain)
- defines causality rules (cause → effect constraints)
- defines invariants and hard limits (non-negotiable)
- defines exception protocol (when a law can be bent and what it costs)
- defines validation checks for downstream engines (timeline/civilization/tech/ecology) and for narrative consumption

Output must be **testable** (not vibes).

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- define world structure containers/topology (belongs to `01__WORLD_STRUCTURE_ENG`)
- define story beats, scenes, pacing, twists (narrative family)
- define character psychology/morality/dialogue (character family)
- define production execution (camera/editing/audio)
- define economy/civilization details as primary (downstream world engines own specifics)
- create “special rules for one scene” without registering as an exception under protocol

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- WORLD_STRUCTURE_MODEL
- WORLD_INVARIANTS
- WORLD_LAW_SEEDS (optional; initial sketch)
- CANON_CONSTRAINTS (optional; system-level constraints)

PRODUCES:
- WORLD_LAWSET
- CAUSALITY_CONSTRAINTS
- POSSIBILITY_MATRIX

DEPENDS_ON:
- [04_DOMAIN_WORLD_ENGINES/01__WORLD_STRUCTURE_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/WORLD/LAWS/
OPTIONAL:
- KB/WORLD_LAWS (if project mirrors into KB)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- World Law: any rule that constrains what can happen in the world.
- Hard Law: invariant constraint; violation is impossible unless governance-approved canon change.
- Soft Law: default constraint; violation allowed only via registered exception protocol.
- Causality Constraint: rule linking cause → effect and preventing impossible chains.
- Possibility Matrix: structured map of allowed actions/phenomena by layer/scale/context.
- Exception: a formally registered deviation (temporary or local) with triggers, costs, and aftermath.

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- possibility limits (can/can’t)
- causality constraints (if X then Y cannot/ must)
- law invariants (hard/soft)
- exception protocol + verification checks

OUT OF SCOPE (HARD):
- topology/places/regions (structure engine)
- timeline content (timeline & epoch engine)
- civilizations and geopolitics content (their engines)
- resource accounting (economy engine)
- tech/magic detailed catalogs (tech/magic engine) — BUT it must respect this lawset

COLLISION RULE:
- If question is “where/what exists” → route to `01__WORLD_STRUCTURE_ENG`
- If question is “when in world-state” → route to `03__TIMELINE_EPOCH_ENG`
- If question is “specific tech/magic system details” → route to `08__TECHNOLOGY_MAGIC_ENG` (must comply with lawset)
- If question is “story-only convenience” → forbidden unless registered as exception

---

## 5) RULESET (THE LAW)

R1 (HARD) MUST: WORLD_LAWSET must declare hard laws and soft laws separately.
R2 (HARD) MUST: CAUSALITY_CONSTRAINTS must include at least one cause→effect rule per owned layer (PHYSICAL/SOCIAL/SYSTEMS) if applicable.
R3 (HARD) MUST: POSSIBILITY_MATRIX must define allowed phenomena/actions by layer and scale (GLOBAL/REGIONAL/LOCAL).
R4 (HARD) FORBIDDEN: introducing narrative constructs (acts/beats/scenes) as laws.
R5 (HARD) FORBIDDEN: “handwave magic” — any non-physical phenomenon must be expressed as rules + constraints + costs.
R6 (HARD) MUST: exception protocol exists; any bending of soft laws MUST be recorded as exceptions (with cost + aftermath).
R7 (HARD) MUST: laws must be testable: each hard law has violation example + detection check.
R8 (SOFT) SHOULD: laws include clarity tags (e.g., TIME, ENERGY, INFORMATION, MOBILITY) for search and validation.
R9 (HARD) MUST: if a hard law changes → route to governance change control + audit (canon-impacting).

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: WORLD_LAWSET
- MUST:
  - lawset_id (string)
  - version (string)
  - scope (global / project / realm)
  - hard_laws[] (non-empty or explicit rationale if none)
  - soft_laws[] (optional)
  - definitions[] (optional local)
  - exception_protocol_ref (pointer)
  - validation_ref (pointer to checks)
  - notes
- HARD LAW (minimum):
  - law_id
  - statement (testable)
  - domain_tag (e.g., TIME/ENERGY/INFO/MOBILITY/IDENTITY)
  - layer (PHYSICAL|SOCIAL|SYSTEMS)
  - scale (GLOBAL|REGIONAL|LOCAL|ALL)
  - implications[] (what it forces)
  - forbidden_examples[] (what cannot occur)
  - detection_check (how to detect violation)
- SOFT LAW (minimum):
  - law_id
  - statement
  - default_behavior
  - allowed_exception_types[] (references)
  - cost_baseline (what it usually costs)
  - detection_check
- VALIDATION:
  - no vague prose (“usually”, “somehow”) without measurable constraints
  - hard laws include forbidden examples + detection check
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/LAWS/WORLD_LAWSET.md

ARTIFACT: CAUSALITY_CONSTRAINTS
- MUST:
  - causality_id
  - version
  - constraints[] (non-empty)
  - paradox_rules[] (optional but recommended)
  - checks[] (non-empty)
- CONSTRAINT (minimum):
  - c_id
  - if_cause (structured condition)
  - then_effect (structured effect)
  - forbidden_chain[] (what chain is invalid)
  - required_chain[] (what must follow if relevant)
  - severity (S0|S1|S2|S3)
  - notes
- PARADOX RULE (minimum):
  - p_id
  - paradox_type (TIME_LOOP|INFORMATION|IDENTITY|ENERGY)
  - rule
  - resolution_rule (what the system does)
- CHECK (minimum):
  - check_id
  - description
  - severity
- VALIDATION:
  - each constraint must define either forbidden_chain or required_chain
  - any S0 constraint must have a concrete check
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/LAWS/CAUSALITY_CONSTRAINTS.md

ARTIFACT: POSSIBILITY_MATRIX
- MUST:
  - matrix_id
  - version
  - axes (layer, scale, domain_tag)
  - cells[] (non-empty)
  - global_limits[] (optional)
  - open_unknowns[] (optional)
- CELL (minimum):
  - cell_id
  - layer (PHYSICAL|SOCIAL|SYSTEMS)
  - scale (GLOBAL|REGIONAL|LOCAL)
  - domain_tag
  - allowed[] (what can happen)
  - forbidden[] (what cannot happen)
  - conditional[] (allowed only if conditions true)
  - required_costs[] (if conditional)
  - references (law_id list)
- VALIDATION:
  - every allowed/forbidden item references at least one law_id OR explicitly marked “UNKNOWN” and routed to open_unknowns
  - no contradictions inside a cell
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/LAWS/POSSIBILITY_MATRIX.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Input validation:
   - confirm structure outputs exist (WORLD_STRUCTURE_MODEL, WORLD_INVARIANTS)
2) Draft law candidates:
   - convert seeds into testable statements
3) Split into hard vs soft:
   - hard = invariants / non-negotiable limits
   - soft = default rules with exception types
4) Build causality constraints:
   - define cause→effect rules and paradox handling
5) Build possibility matrix:
   - map allowed/forbidden by layer + scale + domain tag
6) Define exception protocol:
   - exception types, triggers, costs, aftermath, and logging
7) Run validation checks:
   - contradictions, vagueness, missing checks, unreferenced matrix entries
8) Emit artifacts

---

## 8) S0 BLOCKERS (STOP)
- S0-1: Hard law lacks forbidden examples or detection check.
- S0-2: Causality constraint marked S0 has no concrete check.
- S0-3: Possibility matrix contains contradictions (same phenomenon allowed and forbidden under same conditions).
- S0-4: Any “magic/exception” is introduced without rule + cost + aftermath.
- S0-5: Engine claims ownership of narrative beats/scenes as laws.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- consumes world structure + invariants from `01__WORLD_STRUCTURE_ENG`

Downstream consumers (typical):
- `03__TIMELINE_EPOCH_ENG` (world-state changes must respect laws)
- `04__CIVILIZATION_ENG` (social/system rules must comply)
- `05__CONFLICT_POWER_ENG` (power mechanics must fit possibility constraints)
- `06__GEOPOLITICS_ENG` (actions/mobility/info constraints)
- `07__ECONOMY_RESOURCE_ENG` (resource realism + constraints; no law contradictions)
- `08__TECHNOLOGY_MAGIC_ENG` (tech/magic must be a specialization under lawset)
- `10__ENVIRONMENT_ECOLOGY_ENG` (ecology must obey physical/energy constraints)

Narrative consumption:
- narrative engines may propose events, but events MUST pass possibility checks or declare an exception type.

Governance:
- changes to hard laws = canon-impacting; must route to change control + audit.

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- ENGINE TEMPLATE (family):
  04_DOMAIN_WORLD_ENGINES/00__TEMPLATE__ENGINE__DOMAIN_WORLD_ENGINES.md

--- END.

LOCK: OPEN
