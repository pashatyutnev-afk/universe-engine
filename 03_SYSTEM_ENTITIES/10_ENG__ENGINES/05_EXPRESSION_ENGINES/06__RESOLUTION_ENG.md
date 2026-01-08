# RESOLUTION ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/05_EXPRESSION_ENGINES/06__RESOLUTION_ENG.md
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
UID: UE.ENG.EXP.RESOLUTION.001
OWNER: SYSTEM
ROLE: Produces deterministic resolution artifacts: conflict closure, obligation payment, aftermath state changes, and unresolved thread registry. Ensures climax/turning-point obligations are satisfied or explicitly deferred.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Resolution Engine created: closure schema, obligation payment ledger, aftermath state mapping, and unresolved threads registry."
- REASON: "Climax without explicit closure produces holes; pipelines need deterministic payoff tracking."
- IMPACT: "Continuity becomes auditable; endings become consistent and reusable."
- CHANGE_ID: UE.CHG.2026-01-08.EXP.RESOLUTION.001

---

## 0) PURPOSE (LAW)
This engine owns the **RESOLUTION primitive**:
- closes conflicts (win/lose/shift/stalemate/abandon)
- pays obligations emitted by turning points and climax
- records aftermath as explicit state change deltas
- registers unresolved threads intentionally (with due markers)

Hard rule:
- “Ending” is invalid if obligations exist and are neither paid nor explicitly deferred.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- select turning points/climax (those engines do)
- create conflicts (conflict engine)
- write full scenes/dialogue (narrative/character engines)
- define pacing/montage (pacing/editing engines)
- define world law truths (world law engine)

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- CONFLICT_OBJECT_SET
- TURNING_POINT_SET (optional but recommended)
- TURNING_POINT_OBLIGATIONS (recommended)
- CLIMAX_SET (recommended)
- CLIMAX_OBLIGATIONS (recommended)
- EVENT_PACK
- CAUSAL_GRAPH (optional)
- WORLD_LAWSET (optional)
- CONTINUITY_CONSTRAINTS (optional)

PRODUCES:
- RESOLUTION_SET
- OBLIGATION_PAYMENT_LEDGER
- AFTERMATH_STATE_MAP
- UNRESOLVED_THREAD_REGISTRY

DEPENDS_ON:
- [05_EXPRESSION_ENGINES/03__CONFLICT_ENG, 05_EXPRESSION_ENGINES/04__TURNING_POINT_ENG, 05_EXPRESSION_ENGINES/05__CLIMAX_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/EXPRESSION/RESOLUTION/
OPTIONAL:
- KB/RESOLUTION (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Resolution: explicit closure of a conflict with outcome + proof (events).
- Obligation: required payoff/consequence emitted earlier.
- Payment: event(s) that satisfy an obligation.
- Aftermath: state deltas after resolution (relationships, power, resources, location status).
- Unresolved Thread: deferred obligation or open question intentionally left for future.

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- closure outcomes for conflicts
- mapping obligations → payments (or deferrals)
- aftermath state changes and open thread registry

OUT OF SCOPE (HARD):
- building conflicts (conflict engine)
- selecting climax (climax engine)
- pacing and rhythm design (pacing engine)
- world-level geopolitics design (world engines)
- author theme evaluation (theme engine)

COLLISION RULE:
- If you need “what the climax is” → climax engine.
- If you need “what changed in continuity” beyond aftermath mapping → continuity engines consume aftermath.
- If you need “why obligation exists” → turning point/climax engines are sources.

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: each resolution references at least one conflict_id and at least one proof event_id.
R2 (HARD) MUST: all incoming obligations are either PAID or DEFERRED with explicit registry entry.
R3 (HARD) MUST: closure outcome is from allowed enum set.
R4 (HARD) MUST: aftermath state deltas are explicit and testable.
R5 (HARD) FORBIDDEN: “everything worked out” without mapping to events and state changes.
R6 (HARD) MUST: unresolved threads have due markers and ownership (who carries it).
R7 (SOFT) SHOULD: tie resolution to causal chain completion (if causal graph exists).
R8 (HARD) MUST: if world lawset provided, resolution cannot introduce impossible states as facts.

Allowed outcomes (strict):
- WIN_A
- WIN_B
- MIXED
- SHIFT (goal changes / conflict transforms)
- STALEMATE
- ABANDON
- COLLAPSE (system breakdown)

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: OBLIGATION_PAYMENT_LEDGER
- MUST:
  - ledger_id
  - version
  - incoming_obligations[] (non-empty if any input obligations exist)
  - entries[] (can be empty only if no incoming obligations)
  - checks[] (non-empty)
- INCOMING OBLIGATION (minimum):
  - obligation_id
  - source (TURNING_POINT|CLIMAX)
  - source_ref (tp_id or climax_id)
  - statement
  - severity_if_unpaid (S0|S1|S2|S3)
- ENTRY (minimum):
  - obligation_id
  - status (PAID|DEFERRED|CANCELLED_BY_REFRAME)
  - payment_event_ids[] (non-empty if PAID)
  - deferral_ref (required if DEFERRED)
  - notes
- CHECK (minimum):
  - check_id
  - description
  - severity
- VALIDATION:
  - any S0 obligation must not be left without PAID/DEFERRED entry
  - if status=PAID → payment_event_ids non-empty and exist
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/EXPRESSION/RESOLUTION/OBLIGATION_PAYMENT_LEDGER.md

---

ARTIFACT: AFTERMATH_STATE_MAP
- MUST:
  - aftermath_id
  - version
  - deltas[] (non-empty)
  - checks[] (non-empty)
- DELTA (minimum):
  - delta_id
  - scope (PERSONAL|LOCAL|REGIONAL|GLOBAL|SYSTEM)
  - affected_refs[] (optional)
  - what_changed (testable)
  - before (optional)
  - after (required)
  - caused_by (resolution_id or event_ids)
  - permanence (TEMPORARY|LASTING|UNKNOWN)
- CHECK (minimum):
  - check_id
  - description
  - severity
- VALIDATION:
  - each delta has after
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/EXPRESSION/RESOLUTION/AFTERMATH_STATE_MAP.md

---

ARTIFACT: UNRESOLVED_THREAD_REGISTRY
- MUST:
  - registry_id
  - version
  - threads[] (can be empty)
  - checks[] (non-empty)
- THREAD (minimum):
  - thread_id
  - originated_from (OBLIGATION|QUESTION|MISSING_INFO)
  - source_ref (obligation_id or narrative ref)
  - statement (testable)
  - carrier_refs[] (who/what holds it)
  - due_by (epoch/segment marker or NEXT_ARC)
  - severity_if_unresolved (S0|S1|S2|S3)
  - routing_hint (engine pointer for future handling)
  - notes
- VALIDATION:
  - any DEFERRED obligation must have a thread entry
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/EXPRESSION/RESOLUTION/UNRESOLVED_THREAD_REGISTRY.md

---

ARTIFACT: RESOLUTION_SET
- MUST:
  - set_id
  - version
  - resolutions[] (non-empty)
  - checks[] (non-empty)
- RESOLUTION (minimum):
  - resolution_id
  - title
  - conflict_ids[] (non-empty)
  - outcome (WIN_A|WIN_B|MIXED|SHIFT|STALEMATE|ABANDON|COLLAPSE)
  - proof_event_ids[] (non-empty)
  - paid_obligations_ref (ledger pointer)
  - aftermath_ref (after-math pointer)
  - unresolved_threads_ref (registry pointer)
  - notes
- CHECK (minimum):
  - check_id
  - description
  - severity
- VALIDATION:
  - conflict_ids exist
  - proof events exist
  - if incoming obligations exist → ledger non-empty and complete
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/EXPRESSION/RESOLUTION/RESOLUTION_SET.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load conflicts, climax/turning points, obligations, and events.
2) For each major conflict cluster:
   - decide closure outcome from allowed enum set
3) Map obligations:
   - PAID via event_ids
   - or DEFERRED → create thread entry
4) Create aftermath deltas:
   - explicit before/after changes
5) Validate:
   - no unpaid obligations without defer registry
   - proofs exist for outcomes
6) Emit:
   - ledger + aftermath map + unresolved registry + resolution set

---

## 8) S0 BLOCKERS (STOP)
- S0-1: resolution references unknown conflict_id or proof event_id.
- S0-2: any S0 obligation not PAID or DEFERRED.
- S0-3: outcome not in allowed enum.
- S0-4: aftermath deltas missing explicit “after”.
- S0-5: deferred obligations without thread registry entry.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- conflict, turning point, and climax engines provide obligations and peak anchors.
- events provide proof and payment vehicles.

Downstream:
- narrative continuity engine (anchors aftermath and unresolved threads)
- story structure engines (place resolution blocks)
- pacing engine (uses closure points as rhythm anchors)
- world engines (may consume aftermath for world-state evolution)

Governance:
- if resolution rules change across canon, route via governance change control + audit.

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family template:
  05_EXPRESSION_ENGINES/00__TEMPLATE__ENGINE__EXPRESSION_ENGINES.md

--- END.

LOCK: OPEN
