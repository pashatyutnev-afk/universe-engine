# 🕯️ FORESHADOWING ENGINE
## Canonical Engine Specification  
**LEVEL: L2 · DOMAIN ENGINE · PLANT/PAYOFF CONTROL · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 07__FORESHADOWING_ENG.md
- ENGINE_ID: L2-DOM-FORESHADOWING-ENGINE-007
- UID: UE.ENT.ENG.DOM.NARRATIVE.FORESHADOWING
- NAME: Foreshadowing Engine
- CLASS: Domain Engine
- DOMAIN: Narrative
- CATEGORY: Plant/Payoff Registry, Signal Placement & Fair Setup
- LEVEL: L2
- STATUS: FINAL
- FAILURE_MODE: fail-closed (for fairness/completeness)
- EDITABLE: true
- BYPASS_ALLOWED: false (within narrative pipeline)

### ABSOLUTE RULE
> Major payoffs must be prepared: if a payoff has no plant, it becomes a cheat.

---

## 1. PURPOSE

Foreshadowing Engine manages **setup → payoff integrity**.

It guarantees:
- explicit registry of planted signals
- traceability from plant to payoff
- controlled placement across structure (early/mid/late)
- fairness rules (audience could have noticed)

It does not decide the twist; it ensures the story doesn’t “spawn miracles”.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Create and maintain Plant/Payoff registry for a story plan
- Tag plants by strength and visibility
- Schedule plants across acts/sequences/scenes
- Validate that major payoffs have earlier plants
- Detect over-telegraphed plants (too obvious too early)
- Suggest distribution repairs (non-binding)

### OUT-OF-SCOPE (FORBIDDEN)
- Writing scene prose (only constraints/notes)
- Designing reveal timing (Twist & Reveal Engine)
- Global continuity policing (Continuity Engine)
- Logic causality proof (Narrative Logic Engine)
- Canon authority decisions (Governance)

---

## 3. FORESHADOWING MODEL

### 3.1 Core Objects

- PLANT: a signal, clue, hint, pattern, rule mention
- PAYOFF: a later event/reveal consequence that uses the plant
- LINK: explicit mapping plant_id → payoff_id

### 3.2 Plant Strength (fixed)
- SUBTLE
- MODERATE
- STRONG

### 3.3 Visibility (fixed)
- BACKGROUND (easy to miss)
- FOREGROUND (noticeable)
- EMPHASIZED (hard to miss; use carefully)

### 3.4 Fairness Rule Set (fixed)
- FAIR: plant exists before payoff and is perceivable
- BORDERLINE: plant exists but too subtle/too late
- UNFAIR: payoff has no plant or contradicts declared constraints

---

## 4. INPUT ARTIFACTS

### 4.1 INPUT — FORESHADOWING_REQUEST
**REQUIRED FIELDS**
- `fs_id`
- `timestamp`
- `structure_plan_ref`
- `scene_specs_refs` (recommended)
- `tension_map_ref` (optional)
- `arc_plan_ref` (optional)
- `major_payoffs_list` (non-empty list)
- `constraints_refs` (world/character)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 5. OUTPUT ARTIFACTS

### 5.1 OUTPUT — PLANT_PAYOFF_REGISTRY
- `fs_id`
- `plants` (list)
- `payoffs` (list)
- `links` (list plant_id → payoff_id)
- `placement_map` (list: {plant_id, segment_id, visibility, strength})
- `fairness_verdicts` (list per payoff)
- `constraints_for_scenes` (non-binding rules to insert/adjust plants)
- `trace_id` (if provided)

### 5.2 OUTPUT — FORESHADOWING_VERDICT
- `fs_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list; non-binding)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 6. CORE OPERATIONS

- OP_01: REGISTER_MAJOR_PAYOFFS
- OP_02: GENERATE_REQUIRED_PLANTS (minimal set)
- OP_03: PLACE_PLANTS_ACROSS_STRUCTURE
- OP_04: LINK_PLANTS_TO_PAYOFFS
- OP_05: CHECK_FAIRNESS_AND_TELEGRAPHING
- OP_06: EMIT_REGISTRY

---

## 7. ACCESS MODEL

### WRITE
- Domain pipeline outputs only

### READ
- Scene Construction Engine (inject plant beats/props/lines as notes)
- Twist & Reveal Engine (fairness constraints)
- Continuity Engine (track planted threads)
- Pacing & Rhythm Engine (avoid plant clustering)

### DELETE
- Allowed for drafts; finalization per project governance

---

## 8. DEPENDENCIES

### REQUIRED
- Story Structure Engine (segment map)
- Optional: Scene Construction Engine (where plants can live)
- Optional: Tension & Stakes Engine (pressure-aligned hints)

### FORBIDDEN
- Treating foreshadowing registry as canon authority
- Using unregistered “miracle” plants after payoff

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED FOR FAIRNESS)

CRITICAL:
- Any major payoff with no prior plant
- Payoff contradicts declared constraints with no bridge
- Plants placed only after payoff (retroactive setup)
- Over-telegraphing: emphasized strong plant repeated ≥3 times before midpoint

Reaction:
- Verdict INVALID (CRITICAL)
- Provide repairs: add earlier plants; reduce emphasis; redistribute.

---

## 10. TRACE RULES

- trace_id optional unless orchestrator requires traced pipeline
- if present, propagate to reveal and continuity constraints

---

## 11. NON-GOALS
- Does not decide twist content
- Does not write prose
- Does not validate truth
- Does not grant canon authority

---

## 12. FINAL STATEMENT

Foreshadowing is the contract of fairness.
Plants earn payoffs.

---

**STATUS:** Foreshadowing Engine v1.0  
**DOMAIN:** ACTIVE
