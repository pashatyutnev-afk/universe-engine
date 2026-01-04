# 🌀 TWIST & REVEAL ENGINE
## Canonical Engine Specification  
**LEVEL: L2 · DOMAIN ENGINE · REVEAL ORCHESTRATION · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 08__TWIST_REVEAL_ENG.md
- ENGINE_ID: L2-DOM-TWIST-REVEAL-ENGINE-008
- UID: UE.ENT.ENG.DOM.NARRATIVE.TWIST_REVEAL
- NAME: Twist & Reveal Engine
- CLASS: Domain Engine
- DOMAIN: Narrative
- CATEGORY: Reveal Design, Twist Typology & Disclosure Scheduling
- LEVEL: L2
- STATUS: FINAL
- FAILURE_MODE: fail-closed (for fairness/clarity)
- EDITABLE: true
- BYPASS_ALLOWED: false (within narrative pipeline)

### ABSOLUTE RULE
> A reveal is invalid if it is unfair (no setup) or incomprehensible (no clarity path).

---

## 1. PURPOSE

Twist & Reveal Engine designs **information disclosure**.

It guarantees:
- explicit reveal schedule (when what is learned)
- twist typology (what kind of reversal it is)
- fairness constraints via plant/payoff linkage
- clarity path (audience can reconstruct meaning)
- spoiler control (avoid premature full disclosure)

It does not create the story’s canon; it shapes how knowledge is released.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define reveal units (what info is hidden vs known)
- Assign reveal timing to segments (acts/scenes/beats)
- Design twist events (re-contextualization) and their delivery
- Validate fairness via Foreshadowing registry links
- Validate clarity: “after reveal, audience can understand why”
- Detect over-exposition or reveal spam
- Provide repairs: delay/advance, split reveals, add bridging beats (non-binding)

### OUT-OF-SCOPE (FORBIDDEN)
- Creating plants (Foreshadowing Engine registers)
- Pacing budgets (Pacing & Rhythm Engine)
- Causality proof (Narrative Logic Engine)
- Global continuity policing (Continuity Engine)
- Canon authority decisions (Governance)

---

## 3. REVEAL MODEL

### 3.1 Core Objects
- REVEAL_UNIT: a chunk of information that changes understanding
- TWIST_EVENT: a reveal that flips interpretation (re-contextualizes prior data)
- DISCLOSURE_STATE: what audience/characters know at a point

### 3.2 Twist Types (fixed set)
- IDENTITY (who someone is)
- MOTIVE (why someone acted)
- CAUSALITY (what actually caused events)
- ALLIANCE (who is with/against whom)
- RULE (how the world actually works)
- PERSPECTIVE (unreliable narrator / misdirection)
- STAKES (what is truly at risk)

### 3.3 Reveal Strength (fixed)
- MICRO (small clarification)
- MAJOR (big new info)
- NUCLEAR (reframes large parts of story; use sparingly)

### 3.4 Fairness & Clarity Rules
- Every MAJOR/NUCLEAR reveal must link to ≥1 plant before it triggers
- After reveal, there must be a clarity beat or consequence beat within 1–2 segments
- If reveal changes stakes, tension map must reflect escalation/reframe

---

## 4. INPUT ARTIFACTS

### 4.1 INPUT — REVEAL_REQUEST
**REQUIRED FIELDS**
- `reveal_id`
- `timestamp`
- `structure_plan_ref`
- `scene_specs_refs` (recommended)
- `plant_payoff_registry_ref` (required for MAJOR/NUCLEAR)
- `arc_plan_ref` (optional)
- `pacing_plan_ref` (optional)
- `tension_map_ref` (optional)
- `target_reveals_list` (non-empty list)
- `constraints_refs` (world/character)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 5. OUTPUT ARTIFACTS

### 5.1 OUTPUT — REVEAL_SCHEDULE
- `reveal_id`
- `reveal_units` (list: {unit_id, type, strength, summary})
- `twist_events` (list: {twist_id, twist_type, strength, linked_plants})
- `placement_map` (list: {unit_id/twist_id, segment_id, delivery_mode})
- `disclosure_states` (map: segment_id → what is known)
- `clarity_path` (list of required clarity beats after key reveals)
- `constraints_for_scenes` (rules to implement delivery)
- `trace_id` (if provided)

### 5.2 OUTPUT — REVEAL_VERDICT
- `reveal_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list; non-binding)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 6. DELIVERY MODES (fixed)
- DIALOGUE_DISCLOSURE
- VISUAL_EVIDENCE
- ACTION_CONSEQUENCE
- DOCUMENT/LOG/RECORD
- ENVIRONMENTAL_CLUE
- INTERNAL_REALIZATION

---

## 7. CORE OPERATIONS

- OP_01: DEFINE_REVEAL_UNITS
- OP_02: CLASSIFY_TWIST_TYPES
- OP_03: MAP_REVEALS_TO_STRUCTURE
- OP_04: VALIDATE_FAIRNESS_WITH_PLANTS
- OP_05: VALIDATE_CLARITY_PATH
- OP_06: DETECT_EXPOSITION_OR_SPAM
- OP_07: EMIT_REVEAL_SCHEDULE

---

## 8. ACCESS MODEL

### WRITE
- Domain pipeline outputs only

### READ
- Scene Construction Engine (delivery beats)
- Foreshadowing Engine (alignment + fairness)
- Continuity Engine (knowledge-state consistency)
- Pacing & Rhythm Engine (avoid reveal clustering)

### DELETE
- Allowed for drafts; finalization per project governance

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- MAJOR/NUCLEAR reveal with no linked plant
- Reveal placed after payoff (retroactive twist)
- Nuclear reveal occurs with no clarity path within 1–2 segments
- Reveal spam: ≥3 MAJOR reveals in one sequence without breath
- Twist contradicts world rules with no bridge justification

Reaction:
- Verdict INVALID (CRITICAL)
- Provide repairs: add plants, redistribute reveals, add clarity beats, split nuclear reveals.

---

## 10. TRACE RULES

- trace_id optional unless orchestrator requires traced pipeline
- if present, propagate to continuity constraints

---

## 11. NON-GOALS
- Does not create plants
- Does not write prose
- Does not validate truth
- Does not grant canon authority

---

## 12. FINAL STATEMENT

Reveals are controlled access to meaning.
Twists must be fair, clear, and earned.

---

**STATUS:** Twist & Reveal Engine v1.0  
**DOMAIN:** ACTIVE
