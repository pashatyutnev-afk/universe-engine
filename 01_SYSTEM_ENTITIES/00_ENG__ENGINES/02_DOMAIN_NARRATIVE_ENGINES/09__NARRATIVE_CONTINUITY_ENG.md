# 🔗 NARRATIVE CONTINUITY ENGINE
## Canonical Engine Specification  
**LEVEL: L2 · DOMAIN ENGINE · CONTINUITY TRUTH · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 09__NARRATIVE_CONTINUITY_ENG.md
- ENGINE_ID: L2-DOM-NARRATIVE-CONTINUITY-ENGINE-009
- UID: UE.ENT.ENG.DOM.NARRATIVE.NARRATIVE_CONTINUITY
- NAME: Narrative Continuity Engine
- CLASS: Domain Engine
- DOMAIN: Narrative
- CATEGORY: Thread Registry, State Continuity & Knowledge Consistency
- LEVEL: L2
- STATUS: FINAL
- FAILURE_MODE: fail-closed (for continuity validity)
- EDITABLE: true
- BYPASS_ALLOWED: false (within narrative pipeline)

### ABSOLUTE RULE
> If continuity breaks without an explicit bridge, the narrative loses trust.

---

## 1. PURPOSE

Narrative Continuity Engine maintains **story coherence over time**.

It guarantees:
- continuity of world state and character state
- continuity of knowledge states (who knows what when)
- continuity of threads (plants, promises, goals, unresolved conflicts)
- explicit handling of retcons and contradictions

This engine is the “memory police” of the narrative layer.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Build and maintain a Continuity Registry (threads + states)
- Track:
  - world state deltas
  - character state deltas
  - relationship deltas
  - knowledge state deltas
  - open threads and closures
- Detect continuity breaks (teleports, missing injuries, vanished objects, etc.)
- Detect knowledge leaks (character knows what they shouldn’t)
- Validate plant/payoff closures (thread closure coverage)
- Provide repair suggestions (bridges, inserts, clarifications)

### OUT-OF-SCOPE (FORBIDDEN)
- Causality proof (Narrative Logic Engine)
- Twist design decisions (Twist & Reveal Engine)
- Pacing budgets (Pacing & Rhythm Engine)
- Theme selection (Theme & Meaning Engine)
- Canon authority decisions (Governance)

---

## 3. CONTINUITY MODEL

### 3.1 Continuity Domains (fixed)
- WORLD_STATE
- CHARACTER_STATE
- RELATIONSHIP_STATE
- INVENTORY/OBJECT_STATE
- LOCATION/GEOGRAPHY_STATE
- TIME_STATE (timeline order)
- KNOWLEDGE_STATE (info distribution)
- THREADS (open loops: promises, plants, goals)

### 3.2 Thread Types (fixed)
- PROMISE (stated expectation)
- PLANT (setup)
- GOAL (explicit objective)
- CONFLICT (active opposition)
- MYSTERY (unknown that must be resolved)
- RULE (world rule that must remain consistent)
- DEBT (owed cost / consequence)

### 3.3 Continuity Break Types (fixed)
- STATE_GAP (missing delta)
- CONTRADICTION (A and not-A)
- TELEPORT (location/time jump without bridge)
- OBJECT_VANISH (inventory inconsistency)
- KNOWLEDGE_LEAK (unearned knowledge)
- THREAD_DROP (open thread never referenced again)
- RETCON (explicit revision of earlier established fact)

---

## 4. INPUT ARTIFACTS

### 4.1 INPUT — CONTINUITY_CHECK_REQUEST
**REQUIRED FIELDS**
- `cont_id`
- `timestamp`
- `structure_plan_ref`
- `scene_specs_refs` (recommended)
- `reveal_schedule_ref` (recommended for knowledge states)
- `plant_payoff_registry_ref` (recommended for threads)
- `constraints_refs` (world/character)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 5. OUTPUT ARTIFACTS

### 5.1 OUTPUT — CONTINUITY_REGISTRY
- `cont_id`
- `state_timeline` (segment_id → state deltas by domain)
- `knowledge_timeline` (segment_id → who knows what)
- `threads_open` (list)
- `threads_closed` (list)
- `thread_links` (thread_id → segments where referenced/closed)
- `continuity_breaks` (list)
- `constraints_for_scenes` (non-binding fixes)
- `trace_id` (if provided)

### 5.2 OUTPUT — CONTINUITY_VERDICT
- `cont_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list; non-binding)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 6. CORE OPERATIONS

- OP_01: BUILD_STATE_TIMELINE
- OP_02: BUILD_KNOWLEDGE_TIMELINE
- OP_03: BUILD_THREAD_REGISTRY (open/close tracking)
- OP_04: DETECT_BREAKS_AND_LEAKS
- OP_05: CHECK_THREAD_CLOSURE_COVERAGE
- OP_06: EMIT_CONTINUITY_REGISTRY

---

## 7. RETCON RULES (DOMAIN STRICT)

### 7.1 Retcon Definition
A retcon is any change that revises an established prior fact.

### 7.2 Retcon Handling
- Retcons must be:
  - explicit
  - recorded as RETCON break type
  - bridged (explainable path) OR approved as a deliberate revision in project governance

This engine does not approve retcons; it flags them.

---

## 8. ACCESS MODEL

### WRITE
- Domain pipeline outputs only

### READ
- Scene Construction Engine (bridges/fix beats)
- Foreshadowing Engine (thread lifecycle)
- Twist & Reveal Engine (knowledge-state alignment)
- Pacing Engine (avoid dropping threads through cuts)

### DELETE
- Allowed for drafts; finalization per project governance

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- Contradiction with no bridge and no retcon flag
- Knowledge leak on major reveal
- Timeline order broken (impossible sequence)
- Dropped critical thread (core promise/mystery) with no closure plan
- Teleport jump for a major transition without bridge

Reaction:
- Verdict INVALID (CRITICAL)
- Provide repairs: add bridge scene/beat, adjust reveal timing, add closure hooks.

---

## 10. TRACE RULES

- trace_id optional unless orchestrator requires traced pipeline
- if present, propagate to downstream outputs

---

## 11. NON-GOALS
- Does not decide reveals
- Does not write prose
- Does not validate truth
- Does not grant canon authority

---

## 12. FINAL STATEMENT

Continuity is narrative trust.
Break it without a bridge, and the audience exits.

---

**STATUS:** Narrative Continuity Engine v1.0  
**DOMAIN:** ACTIVE
