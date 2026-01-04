# 🩹 GROWTH & TRAUMA ENGINE
## Canonical Engine Specification  
**LEVEL: L2 · DOMAIN ENGINE · CHANGE THROUGH PAIN · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 09__GROWTH_TRAUMA_ENG.md
- ENGINE_ID: L2-DOM-GROWTH-TRAUMA-ENGINE-009
- UID: UE.ENT.ENG.DOM.CHARACTER.GROWTH_TRAUMA
- NAME: Growth & Trauma Engine
- CLASS: Domain Engine
- DOMAIN: Character
- CATEGORY: Wounds, Scars, Coping Shifts & Growth Through Events
- LEVEL: L2
- STATUS: FINAL
- FAILURE_MODE: fail-closed (for change validity)
- EDITABLE: true
- BYPASS_ALLOWED: false (within character pipeline)

### ABSOLUTE RULE
> Change requires cost: growth without pain, loss, or consequence is cosmetic.

---

## 1. PURPOSE

Growth & Trauma Engine models **how characters change** through harm, loss, pressure, and recovery.

It produces:
- **TRAUMA_PROFILE** (wounds, triggers, defenses, scars)
- **GROWTH_MODEL** (what can change, how, and at what cost)

It guarantees:
- explicit wound → coping → behavior shift mapping
- regression/relapse rules (backsliding under stress)
- recovery conditions and costs
- narrative-grade scar map (what remains forever)

It does not diagnose real humans.
It encodes consistent change dynamics for storytelling.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define wounds (what hurt them) and scars (what remains)
- Define trauma triggers and threat patterns
- Define coping shifts (adaptive/maladaptive) over time
- Define belief updates (what they conclude about world/self)
- Define regression/relapse conditions
- Define healing actions (what helps) and their costs
- Validate alignment with Character Core invariants (HARD invariants resist)
- Provide repair suggestions: missing cost, missing scar, implausible recovery

### OUT-OF-SCOPE (FORBIDDEN)
- Creating base identity (Character Core Engine)
- Motivation hierarchy (Motivation Engine) beyond mapping changes
- Moral judgement (Moral & Value Engine)
- Full behavior simulation (Behavior Engine)
- Canon authority decisions (Governance)

---

## 3. TRAUMA & GROWTH MODEL

### 3.1 Core Objects
- WOUND: event/pattern that caused harm
- TRIGGER: stimulus that reactivates wound
- DEFENSE_SHIFT: new protective behavior
- BELIEF_UPDATE: new conclusion about self/world
- SCAR: persistent limitation or sensitivity
- HEALING_ACTION: what reduces impact
- RELAPSE_RULE: condition that causes regression
- INTEGRATION_MARKER: sign of real growth

### 3.2 Wound Types (fixed set)
- ABANDONMENT
- BETRAYAL
- HUMILIATION
- VIOLENCE
- LOSS
- FAILURE_CATASTROPHE
- MORAL_INJURY
- POWERLESSNESS

### 3.3 Severity
- wound_severity: 1..5 (5 = extreme)
- recovery_difficulty: 1..5
- scar_permanence: SOFT | MEDIUM | HARD

---

## 4. INPUT ARTIFACTS

### 4.1 INPUT — TRAUMA_GROWTH_REQUEST
**REQUIRED FIELDS**
- `gt_id`
- `timestamp`
- `char_core_profile_ref`
- `psyche_model_ref` (required)
- `motivation_map_ref` (recommended)
- `value_profile_ref` (recommended)
- `behavior_profile_ref` (recommended)
- `history_events_ref` (can be partial/unknown, but must exist)
- `world_constraints_refs`
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 5. OUTPUT ARTIFACTS

### 5.1 OUTPUT — TRAUMA_PROFILE
**REQUIRED FIELDS**
- `gt_id`
- `char_id`
- `wounds` (list: {wound_id, type, origin, severity_1_5, active?})
- `trigger_map` (list: {trigger, intensity_0_10, linked_wound_id})
- `defense_shifts` (list: {shift_id, defense, when_activated, short_gain, long_cost})
- `belief_updates` (list: {belief_id, belief, formed_when, cost})
- `scar_map` (list: {scar_id, description, permanence, impact})
- `relapse_rules` (list: {rule_id, condition, regression_mode, recovery_requirement})
- `healing_actions` (list: {action_id, action, effectiveness, cost, time_scale})
- `integration_markers` (list: what “real progress” looks like)
- `trace_id` (if provided)

### 5.2 OUTPUT — GROWTH_MODEL
**REQUIRED FIELDS**
- `gt_id`
- `growth_axes` (list: {axis, from_state, to_state, difficulty_1_5})
- `change_constraints` (what cannot change easily; HARD invariants)
- `turning_points_needed` (list: required events/choices for growth)
- `cost_requirements` (what must be paid for change to be earned)
- `regression_map` (map: stress_level → likely backslide)
- `scene_constraints` (non-binding rules for scenes)
- `trace_id` (if provided)

### 5.3 OUTPUT — GROWTH_VERDICT
- `gt_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 6. CORE OPERATIONS

- OP_01: EXTRACT_WOUNDS_FROM_HISTORY
- OP_02: BUILD_TRIGGER_AND_DEFENSE_MAP
- OP_03: DEFINE_BELIEF_UPDATES_AND_SCARS
- OP_04: DEFINE_HEALING_AND_RELAPSE_RULES
- OP_05: BUILD_GROWTH_AXES_AND_TURNING_POINTS
- OP_06: EMIT_TRAUMA_PROFILE_AND_GROWTH_MODEL

---

## 7. ACCESS MODEL

### WRITE
- Domain pipeline outputs only

### READ
- Behavior Engine (stress behavior and relapse)
- Dialogue Engine (mode shifts in speech intent)
- Speech Naturalization Engine (stress voice)
- Relationship Engine (attachment wounds shape bonds)
- Character Evolution Engine (long-term integration)

### DELETE
- Allowed for drafts; finalization per project governance

---

## 8. DEPENDENCIES

### REQUIRED
- Psyche Model (internal dynamics)
- History events reference (even if incomplete)

### FORBIDDEN
- “Instant healing” without cost/time
- Growth that violates HARD invariants without explicit catastrophic turning point
- Treating trauma model as medical diagnosis

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- No wounds and no scars (no change logic)
- No triggers (no reactivation rules)
- Defenses listed with no costs (invincible coping)
- Healing actions with no costs/time scale
- No relapse rules for high-trauma characters
- Growth axes exist with no turning points/cost requirements

Reaction:
- Verdict INVALID (CRITICAL)
- Provide repairs: add wounds/scars, add costs, define relapse & turning points.

---

## 10. TRACE RULES

- trace_id optional unless orchestrator requires traced pipeline
- if present, propagate into evolution records

---

## 11. NON-GOALS
- Does not diagnose real humans
- Does not create plot events as canon
- Does not grant canon authority

---

## 12. FINAL STATEMENT

Trauma leaves a scar.
Growth is learning to live with the scar without letting it rule you.

---

**STATUS:** Growth & Trauma Engine v1.0  
**DOMAIN:** ACTIVE
