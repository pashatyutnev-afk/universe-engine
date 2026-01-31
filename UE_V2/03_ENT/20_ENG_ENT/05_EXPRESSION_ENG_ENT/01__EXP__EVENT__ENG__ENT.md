# EVENT ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/05_EXPRESSION_ENGINES/01__EVENT_ENG.md
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
UID: UE.ENG.EXP.EVENT.001
OWNER: SYSTEM
ROLE: Defines the atomic unit of expression: EVENT. Provides deterministic event schema, event types, validation gates, and storage targets used by narrative/expression pipelines.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Event Engine created: canonical EVENT schema, event typing, severity/impact fields, and validation gates."
- REASON: "All expression/narrative pipelines require a single atomic event contract."
- IMPACT: "Events become stampable, auditable, and compatible across engines."
- CHANGE_ID: UE.CHG.2026-01-08.EXP.EVENT.001

---

## 0) PURPOSE (LAW)
This engine owns the **EVENT primitive**: a single, timestampable unit that can be chained into cause-effect, conflict, turning points, climax, and resolution.

Hard rule:
- If an artifact calls something an “event” but does not match this schema → it is NOT an event (INVALID for pipelines).

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- define why events happen (cause-effect engine)
- define conflict dynamics (conflict engine)
- define story structure / arc (narrative engines)
- define pacing/rhythm (pacing engine)
- define scene construction (scene engine)
- define production depiction (editing/cinematography/etc.)

It only defines the **atomic building block**.

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- EVENT_SEEDS (optional)
- WORLD_LAWSET (optional but recommended)
- TIMELINE_EPOCH_MODEL (optional)
- ACTOR_ENTITY_REFS (optional: character/civ/institution ids)
- LOCATION_ENTITY_REFS (optional: region/place ids)

PRODUCES:
- EVENT_SCHEMA_STANDARD
- EVENT_TYPE_REGISTRY
- EVENT_VALIDATION_GATES
- EVENT_PACK_TEMPLATE

DEPENDS_ON:
- []  (Event is a base primitive; may reference law/timeline but does not require them)

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/EXPRESSION/EVENTS/
OPTIONAL:
- KB/EVENTS (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Event: a discrete occurrence with actors, context, and observable change.
- Event Pack: a set/list of events built under the same context.
- Event Type: classification for routing and validation (not “genre”).
- Impact: what changed as a result of the event (must be explicit).
- Evidence/Signals: what can be observed in-world (or in narrative output) to justify event occurrence.

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- event identity, fields, and validation
- event typing registry
- minimal storage conventions for events and packs

OUT OF SCOPE (HARD):
- causal explanation (belongs to 02__CAUSE_EFFECT_ENG)
- escalation/turning points/climax (other expression engines)
- narrative ordering rules and arcs (domain narrative engines)
- pacing calculations (pacing engine)

COLLISION RULE:
- If it contains “why this caused that” → cause-effect engine.
- If it contains “stakes/tension escalation” → conflict engine.
- If it contains “turning point/climax resolution label” → respective expression engines.
- This engine only labels an event with type and impact, not its deeper function in the arc.

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: every event has unique `event_id` and single `event_time` representation (even if approximate).
R2 (HARD) MUST: event has explicit `change_delta` (what changed).
R3 (HARD) MUST: event declares `actors` and `location_context` or explicitly marks them unknown.
R4 (HARD) MUST: event declares `signals` (what indicates it happened). If none → INVALID unless flagged as “hidden”.
R5 (HARD) FORBIDDEN: “event” as vague prose without structured fields.
R6 (HARD) MUST: event severity is one of S0|S1|S2|S3 (consistent scale).
R7 (SOFT) SHOULD: include constraints refs if event could violate world laws (optional world law binding).
R8 (HARD) MUST: event cannot embed full scenes; it is an atomic unit (no multi-beat structure inside one event).

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: EVENT_SCHEMA_STANDARD
- MUST:
  - schema_id
  - version
  - event_fields[] (non-empty)
  - enums (severity/type/visibility)
  - validation_gates_ref
  - storage_rule
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/EXPRESSION/EVENTS/EVENT_SCHEMA_STANDARD.md

### Canon EVENT object schema (minimum)
EVENT:
- event_id (string; unique)
- title (short)
- event_type (from EVENT_TYPE_REGISTRY)
- event_time:
  - mode (enum: EXACT|RANGE|RELATIVE|UNKNOWN)
  - value (string; ISO date/time if EXACT, or structured text)
  - epoch_id (optional; if timeline model exists)
- location_context:
  - mode (enum: KNOWN|PARTIAL|UNKNOWN)
  - location_refs[] (optional)
  - description (optional)
- actors:
  - primary[] (optional)
  - secondary[] (optional)
  - unknown_allowed (bool)
- intent_context (optional):
  - stated_intent (optional)
  - hidden_intent (optional)
- preconditions (optional):
  - constraints[] (optional)
  - known_state_refs[] (optional)
- change_delta (MANDATORY):
  - what_changed (non-empty)
  - before (optional)
  - after (optional)
  - reversibility (enum: REVERSIBLE|IRREVERSIBLE|UNKNOWN)
- impact:
  - scope (enum: PERSONAL|LOCAL|REGIONAL|GLOBAL|SYSTEM)
  - severity (S0|S1|S2|S3)
  - affected_refs[] (optional)
- signals (MANDATORY unless visibility=HIDDEN):
  - visibility (enum: PUBLIC|PRIVATE|HIDDEN)
  - evidence[] (non-empty if not HIDDEN)
- tags[] (optional)
- notes (optional)

VALIDATION:
- event_id non-empty
- event_type ∈ registry
- change_delta.what_changed non-empty
- severity valid enum
- if visibility != HIDDEN → evidence non-empty

---

ARTIFACT: EVENT_TYPE_REGISTRY
- MUST:
  - registry_id
  - version
  - event_types[] (non-empty)
  - routing_hints[] (optional)
- EVENT TYPE (minimum):
  - type_id
  - name
  - description (testable)
  - typical_inputs[] (optional)
  - typical_outputs[] (optional)
  - disallowed_collisions[] (optional; pointers to engines)
- Minimal required types (baseline set):
  - STATE_CHANGE
  - DISCOVERY
  - DECISION
  - ACTION
  - REACTION
  - LOSS
  - GAIN
  - ARRIVAL
  - DEPARTURE
  - REVEAL
  - WARNING
  - BREACH
  - CREATION
  - DESTRUCTION
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/EXPRESSION/EVENTS/EVENT_TYPE_REGISTRY.md

VALIDATION:
- type_id unique
- baseline set exists (unless explicitly overridden)

---

ARTIFACT: EVENT_VALIDATION_GATES
- MUST:
  - gates_id
  - version
  - gates[] (non-empty)
- GATE (minimum):
  - gate_id
  - name
  - rule (testable)
  - severity_if_fail (S0|S1|S2|S3)
  - auto_fix_hint (optional)
- Required gates (baseline):
  - G0_ID_TIME: event_id exists; time mode valid
  - G1_TYPE: event_type in registry
  - G2_CHANGE: change_delta.what_changed non-empty
  - G3_SIGNALS: evidence present unless hidden
  - G4_SCOPE_SEVERITY: scope and severity valid
  - G5_ATOMICITY: no multi-scene beats inside one event
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/EXPRESSION/EVENTS/EVENT_VALIDATION_GATES.md

---

ARTIFACT: EVENT_PACK_TEMPLATE
- MUST:
  - pack_id
  - version
  - pack_context
  - events[] (non-empty)
  - pack_checks[] (non-empty)
- PACK CONTEXT (minimum):
  - project_id (optional)
  - narrative_window (optional)
  - epoch_id (optional)
  - location_focus (optional)
  - actor_focus (optional)
  - constraints_refs[] (optional)
- PACK CHECKS (minimum):
  - check_id
  - description
  - severity (S0|S1|S2|S3)
- Storage:
  - PROJECT_ARTIFACTS/<project>/EXPRESSION/EVENTS/EVENT_PACK_<id>.md

Pack validation (minimum):
- event_id uniqueness within pack
- no contradictory time ordering without explicit “UNKNOWN/RELATIVE” note

---

## 7) PIPELINE (DETERMINISTIC)
1) Load registry + schema + gates.
2) Generate/ingest events (from seeds or upstream engines).
3) Normalize:
   - ids, time modes, actor/location modes
4) Validate gates:
   - fail-fast on S0
5) Emit:
   - event files (optional) and/or event pack artifact
6) Provide routing hints for downstream engines (cause-effect/conflict/etc.)

---

## 8) S0 BLOCKERS (STOP)
- S0-1: event missing `event_id` or invalid `event_type`.
- S0-2: event missing `change_delta.what_changed`.
- S0-3: event visibility not hidden but evidence empty.
- S0-4: severity out of allowed enum set.
- S0-5: event contains multiple beats/scenes (atomicity violation).

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- any engines producing occurrences (narrative/world/character) can emit events, but must conform to schema.

Downstream consumers:
- 02__CAUSE_EFFECT_ENG (links events with causal relations)
- 03__CONFLICT_ENG (selects events that form conflicts)
- 04__TURNING_POINT_ENG (detects turning points in sequences)
- 05__CLIMAX_ENG (selects peak event(s))
- 06__RESOLUTION_ENG (produces closure events)
- narrative continuity engine (uses events as continuity anchors)

Governance:
- schema changes are canon-impacting if this engine is relied on by multiple families.

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family template:
  05_EXPRESSION_ENGINES/00__TEMPLATE__ENGINE__EXPRESSION_ENGINES.md

--- END.

LOCK: OPEN
