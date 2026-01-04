# 🗓️ EVENT SCHEDULING ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · EXPRESSION ENGINE · TEMPORAL ORDER · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 08__EVENT_SCHEDULING_ENG.md
- ENGINE_ID: L3-EXP-EVENT-SCHEDULING-ENGINE-008
- UID: UE.ENT.ENG.EXP.EVENT_SCHEDULING
- NAME: Event Scheduling Engine
- CLASS: Expression Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (temporal integrity)
- EDITABLE: true

### ABSOLUTE RULE
> If the order is wrong, causality breaks even when events are correct.

---

## 1. PURPOSE

Event Scheduling Engine assigns events into a **temporal plan** while preserving:
- causality constraints
- dependency order
- pacing windows
- deadline pressure
- collision rules (mutually exclusive events)

It produces:
- **EVENT_SCHEDULE**
- time windows (not necessarily exact timestamps)
- conflict escalation pacing plan
- collision detection report
- schedule repair suggestions

This engine prevents “events happen when convenient”.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define scheduling schema (windows, anchors, locks)
- Place events into ordered schedule respecting dependencies
- Enforce time constraints, cooldowns, travel time (if relevant)
- Detect collisions and impossible overlaps
- Allocate pacing windows (buildup → pivot → climax → aftermath)
- Emit schedule for narrative/production pipelines

### OUT-OF-SCOPE (FORBIDDEN)
- Creating events (Event Engine)
- Building causal links (Cause–Effect Engine)
- Deciding climax/resolution content
- Writing scenes/prose
- Canon authority decisions

---

## 3. SCHEDULING MODEL

### 3.1 Schedule Object — EVENT_SCHEDULE (required fields)
- `sch_id`
- `schedule_mode` = WINDOWED | ANCHORED | TIMESTAMPED
- `anchors` (list of anchor points)
- `event_slots` (ordered list of scheduled event placements)
- `time_constraints` (global + per event)
- `collision_report` (overlaps/impossibilities)
- `pacing_windows` (buildup/pivot/peak/aftermath)
- `integrity_report` (issues + fixes)
- `trace_id` (optional)

### 3.2 Anchor Object (required fields)
- `anchor_id`
- `name`
- `type` = START | END | DEADLINE | MIDPOINT | CLIMAX_WINDOW | AFTERMATH_WINDOW
- `time_ref` (can be symbolic: “Day 0”, “Week 3”, “End of Arc”)
- `lock` = HARD | SOFT
- `notes`

### 3.3 Scheduled Placement — EVENT_SLOT (required fields)
- `slot_id`
- `event_id`
- `order_index`
- `time_window` (start/end symbolic or numeric)
- `lock` = HARD | SOFT
- `prerequisites` (event_ids that must occur before)
- `cooldowns` (optional: minimum separation)
- `travel_or_transition_time` (optional)
- `collision_group` (optional: mutually exclusive group)
- `notes`

Missing any required field → REJECT.

---

## 4. HARD RULES (TEMPORAL INTEGRITY)

- Causality order is mandatory:
  - if A causes B, then A must be scheduled before B.
- Turning point triggers must precede their pivot consequences.
- Climax window must occur after:
  - core escalation steps
  - required setups (foreshadow/promise seeds)
- Aftermath window must occur after climax.
- Collisions:
  - events in same collision_group cannot overlap.

---

## 5. INPUT ARTIFACTS

### 5.1 INPUT — SCHEDULING_REQUEST
**REQUIRED FIELDS**
- `sch_req_id`
- `timestamp`
- `event_spec_library_ref` (required)
- `cause_effect_graph_ref` (required)
- `turning_point_map_ref` (recommended)
- `climax_blueprint_ref` (recommended)
- `resolution_plan_ref` (optional)
- `constraints_refs` (required)
- `world_package_ref` (optional: travel/physics constraints)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 6. OUTPUT ARTIFACTS

### 6.1 OUTPUT — EVENT_SCHEDULE
(see model above)

### 6.2 OUTPUT — SCHEDULING_VERDICT
- `sch_req_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 7. CORE OPERATIONS

- OP_01: INGEST_EVENT_AND_CAUSAL_ARTIFACTS
- OP_02: BUILD_DEPENDENCY_ORDER (topological ordering)
- OP_03: DEFINE_ANCHORS_AND_WINDOWS (pacing + constraints)
- OP_04: PLACE_EVENTS_INTO_SLOTS (order + windows)
- OP_05: ENFORCE_COOLDOWNS_AND_TRANSITION_TIMES
- OP_06: DETECT_COLLISIONS_AND_IMPOSSIBLE_OVERLAPS
- OP_07: ALIGN_WITH_TURNINGPOINT_CLIMAX_RESOLUTION (if provided)
- OP_08: EMIT_EVENT_SCHEDULE

---

## 8. COLLISION DETECTION RULES

Collisions flagged when:
- two events require same actor exclusively in different locations same window
- hard-locked windows overlap illegally
- travel/transition time makes sequence impossible
- collision_group overlap

Collision report must include:
- events involved
- reason
- minimal repair options (move, widen window, add transition event)

---

## 9. DEPENDENCIES

### REQUIRED
- Event Spec Library
- Cause–Effect Graph
- Constraints refs

### OPTIONAL
- Turning point map / climax blueprint / resolution plan
- World package (travel/physics/capabilities)

### FORBIDDEN
- Schedules that violate causal order
- Climax before setups
- No aftermath window for high-cost climax
- Hard locks everywhere (no flexibility) unless explicitly required

---

## 10. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- Many causal order violations
- Climax window occurs before required setups/escalation
- Unresolved collision clusters
- Impossible travel/transition sequences (when world constraints provided)
- Schedule has no pacing windows (no structure)

Reaction:
- Verdict INVALID (CRITICAL)
- Emit repair plan:
  - reorder dependent events
  - widen windows
  - add transition/cooldown events
  - adjust anchors

---

## 11. TRACE RULES

- trace_id optional unless pipeline requires traced execution
- if present, propagate into production packaging for timing metadata

---

## 12. NON-GOALS
- Does not create new story content (only places events)
- Does not decide which events are “best”
- Does not write scenes

---

## 13. FINAL STATEMENT

Time is causality made visible.
Schedule it — or the story breaks.

---

**STATUS:** Event Scheduling Engine v1.0  
**REALM:** ACTIVE
