# 🎬 SCENE CONSTRUCTION ENGINE
## Canonical Engine Specification  
**LEVEL: L2 · DOMAIN ENGINE · SCENE DESIGN · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 04__SCENE_CONSTRUCTION_ENG.md
- ENGINE_ID: L2-DOM-SCENE-CONSTRUCTION-ENGINE-004
- UID: UE.ENT.ENG.DOM.NARRATIVE.SCENE_CONSTRUCTION
- NAME: Scene Construction Engine
- CLASS: Domain Engine
- DOMAIN: Narrative
- CATEGORY: Scene Micro-Structure, Inputs/Outputs & Beat Assembly
- LEVEL: L2
- STATUS: FINAL
- FAILURE_MODE: fail-closed (for scene validity)
- EDITABLE: true
- BYPASS_ALLOWED: false (within narrative pipeline)

### ABSOLUTE RULE
> A scene is invalid if it does not change state: it must produce at least one meaningful output.

---

## 1. PURPOSE

Scene Construction Engine produces **Scene Specifications (SCENE_SPEC)**.

It guarantees:
- scenes have clear purpose and function
- every scene has inputs and outputs (state change)
- conflict/friction exists when required
- beats are ordered and serve structure + arc constraints

This engine turns structure segments into scene-level buildable plans.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Generate SCENE_SPEC from structure + arc constraints
- Define scene goal, obstacle, conflict vector
- Define entry state and exit state (inputs/outputs)
- Compose beat list for the scene (beats + functions)
- Provide dialogue intention notes (not actual dialogue)
- Validate scene necessity (remove or merge suggestions)
- Detect “static scenes” (no change) and repair suggestions

### OUT-OF-SCOPE (FORBIDDEN)
- Writing final prose or dialogue (Dialogue Engine in character realm)
- Pacing optimization across the whole story (Pacing Engine)
- Reveal strategy (Twist & Reveal Engine)
- Continuity truth policing (Continuity Engine)
- Canon authority (Governance)

---

## 3. SCENE MODEL

### 3.1 Required Scene Fields (minimum)
- `scene_id`
- `scene_type` (ACTION | DIALOGUE | DISCOVERY | TRANSITION | SETPIECE | MONTAGE)
- `function_tag` (from structure tags)
- `setting` (where/when)
- `participants` (uids/names)
- `scene_goal` (what must be achieved)
- `obstacle` (what blocks)
- `conflict_vector` (who/what opposes and how)
- `entry_state` (what is true on entry)
- `exit_state` (what must be true on exit)
- `stakes_level` (LOW/MEDIUM/HIGH)
- `beats` (ordered list)

### 3.2 Beat Fields (minimum)
Each beat:
- `beat_id`
- `beat_function` (SETUP | PRESSURE | REVEAL | REVERSAL | COST | DECISION | EXIT)
- `beat_summary`
- `state_delta` (what changes)

### 3.3 Scene Validity Requirements
- exit_state must differ from entry_state (at least one delta)
- at least 3 beats for normal scenes (exceptions allowed for micro scenes)
- if stakes_level is MEDIUM/HIGH → must contain PRESSURE or COST beat
- if function_tag is REVERSAL/MIDPOINT_SHIFT/CRISIS/CLIMAX → must include DECISION or REVERSAL beat

---

## 4. INPUT ARTIFACTS

### 4.1 INPUT — SCENE_BUILD_REQUEST
**REQUIRED FIELDS**
- `request_id`
- `timestamp`
- `structure_segment_ref` (sequence/scene slot id)
- `arc_constraints_ref` (optional but recommended)
- `logic_constraints_ref` (optional but recommended)
- `continuity_constraints_ref` (optional)
- `world_constraints_refs`
- `character_constraints_refs`
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 5. OUTPUT ARTIFACTS

### 5.1 OUTPUT — SCENE_SPEC
- fully populated scene specification (fields from section 3)
- includes `inputs_refs` and `outputs_refs` if referencing entities/events
- includes `constraints_used` (what constraints were applied)
- includes `repair_notes` if any

### 5.2 OUTPUT — SCENE_VERDICT
- `scene_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list; non-binding)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 6. CORE OPERATIONS

- OP_01: READ_SLOT_AND_CONSTRAINTS
- OP_02: DEFINE_SCENE_GOAL_AND_OBSTACLE
- OP_03: BUILD_ENTRY_EXIT_STATE
- OP_04: COMPOSE_BEATS
- OP_05: CHECK_STATE_CHANGE_AND_PRESSURE
- OP_06: EMIT_SCENE_SPEC

---

## 7. ACCESS MODEL

### WRITE
- Domain pipeline outputs only

### READ
- Pacing & Rhythm Engine (scene timing)
- Tension & Stakes Engine (pressure mapping)
- Foreshadowing Engine (plant beats)
- Twist & Reveal Engine (reveal placement)
- Continuity Engine (thread integrity)

### DELETE
- Allowed for drafts; finalization per project governance

---

## 8. DEPENDENCIES

### REQUIRED
- Story Structure Engine (slot tags)
- Dramatic Arc Engine (turning constraints)
- Optional: Narrative Logic Engine (causal bridges)

### FORBIDDEN
- Treating SCENE_SPEC as canon authority
- Overriding governance locks

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED FOR SCENE)

CRITICAL:
- No state change (entry_state == exit_state)
- Stakes declared MEDIUM/HIGH but no pressure/cost beats
- Climax/crisis/reversal tag but no decision/reversal beat
- Participants act against constraints with no bridge (logic gap)

Reaction:
- Verdict INVALID (CRITICAL)
- Provide minimal repairs: add delta; add pressure; add decision.

---

## 10. TRACE RULES

- trace_id optional unless orchestrator requires traced pipeline
- if present, propagate through scene specs and downstream

---

## 11. NON-GOALS
- Does not write final dialogue
- Does not enforce global continuity (only uses constraints)
- Does not decide theme
- Does not grant canon authority

---

## 12. FINAL STATEMENT

Scenes are the engine room of story.
No change in a scene means no story movement.

---

**STATUS:** Scene Construction Engine v1.0  
**DOMAIN:** ACTIVE
