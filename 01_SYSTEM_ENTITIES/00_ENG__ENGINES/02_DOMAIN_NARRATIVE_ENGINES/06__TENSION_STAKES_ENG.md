# ⚡ TENSION & STAKES ENGINE
## Canonical Engine Specification  
**LEVEL: L2 · DOMAIN ENGINE · PRESSURE CONTROL · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 06__TENSION_STAKES_ENG.md
- ENGINE_ID: L2-DOM-TENSION-STAKES-ENGINE-006
- UID: UE.ENT.ENG.DOM.NARRATIVE.TENSION_STAKES
- NAME: Tension & Stakes Engine
- CLASS: Domain Engine
- DOMAIN: Narrative
- CATEGORY: Pressure, Risk, Consequences & Escalation Ladder
- LEVEL: L2
- STATUS: FINAL
- FAILURE_MODE: fail-closed (for tension validity)
- EDITABLE: true
- BYPASS_ALLOWED: false (within narrative pipeline)

### ABSOLUTE RULE
> If nothing meaningful can be lost, tension is fake and stakes are zero.

---

## 1. PURPOSE

Tension & Stakes Engine designs and validates **pressure** across the story.

It guarantees:
- explicit stakes definition (what can be lost)
- escalating pressure ladder (risk increases)
- consequence visibility (cost of failure)
- alignment of tension with structure, arc, and pacing

It does not invent plot; it enforces *pressure logic* over the plan.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define stakes per act/sequence/scene
- Build escalation ladder (stakes increase over time)
- Map threats, deadlines, costs, and consequences
- Validate that major beats carry pressure or cost
- Detect “free victories” (no risk, no price)
- Provide tension repairs: add cost, deadline, threat proximity (non-binding)

### OUT-OF-SCOPE (FORBIDDEN)
- Causality proof (Narrative Logic Engine)
- Timing budgets (Pacing & Rhythm Engine)
- Reveal strategy (Twist & Reveal Engine)
- Theme selection (Theme & Meaning Engine)
- Canon authority (Governance)

---

## 3. TENSION MODEL

### 3.1 Stakes Types (fixed set)
- PERSONAL (identity, survival, dignity)
- RELATIONAL (love, loyalty, trust)
- MATERIAL (resources, territory, assets)
- SOCIAL (status, reputation, law)
- SYSTEMIC (world order, civilization, catastrophe)
- IDEOLOGICAL (belief, meaning, faith)

### 3.2 Pressure Sources (fixed set)
- THREAT (antagonist/force approaching)
- DEADLINE (time pressure)
- COST (price paid per attempt)
- UNCERTAINTY (unknown outcome / hidden info)
- CONFLICT (active opposition)
- SCARCITY (limited resources)
- CONSEQUENCE (punishment / loss)

### 3.3 Tension Scale
- 0..10 (integer)
- Stakes Level: LOW/MEDIUM/HIGH (derived from scale)

---

## 4. INPUT ARTIFACTS

### 4.1 INPUT — TENSION_REQUEST
**REQUIRED FIELDS**
- `tension_id`
- `timestamp`
- `structure_plan_ref`
- `arc_plan_ref` (recommended)
- `pacing_plan_ref` (optional)
- `scene_specs_refs` (recommended)
- `core_stakes_statement` (one paragraph)
- `constraints_refs` (world/character)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 5. OUTPUT ARTIFACTS

### 5.1 OUTPUT — TENSION_MAP
- `tension_id`
- `stakes_catalog` (list of stakes objects)
- `segment_tension_points` (list: {segment_id, tension_0_10, stakes_types, pressure_sources})
- `stakes_ladder` (ordered description of escalation)
- `deadlines` (if any)
- `cost_model` (if any)
- `constraints_for_scenes` (rules: must include cost, must include threat proximity, etc.)
- `trace_id` (if provided)

### 5.2 OUTPUT — TENSION_VERDICT
- `tension_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list; non-binding)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 6. CORE OPERATIONS

- OP_01: DEFINE_STAKES_CATALOG
- OP_02: MAP_PRESSURE_SOURCES_TO_SEGMENTS
- OP_03: BUILD_ESCALATION_LADDER
- OP_04: CHECK_COST_AND_CONSEQUENCE_VISIBILITY
- OP_05: DETECT_FREE_VICTORIES
- OP_06: EMIT_TENSION_MAP

---

## 7. ACCESS MODEL

### WRITE
- Domain pipeline outputs only

### READ
- Scene Construction Engine (beat pressure placement)
- Foreshadowing Engine (plant threats/costs)
- Pacing & Rhythm Engine (density and breath alignment)
- Continuity Engine (stakes persistence)

### DELETE
- Allowed for drafts; finalization per project governance

---

## 8. DEPENDENCIES

### REQUIRED
- Story Structure Engine (segments)
- Dramatic Arc Engine (peak constraints)
- Optional: Scene Construction Engine (beats)

### FORBIDDEN
- Treating tension map as canon authority
- Overriding governance locks

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED FOR TENSION)

CRITICAL:
- No explicit stakes catalog (core stakes missing)
- Stakes do not escalate (tension max ≤ 4 or flat curve)
- Climax segment not among highest tension points
- High-stakes segments without cost or consequence
- Repeated wins without loss/cost (free victories)

Reaction:
- Verdict INVALID (CRITICAL)
- Provide repairs: add cost, deadline, threat proximity, consequences.

---

## 10. TRACE RULES

- trace_id optional unless orchestrator requires traced pipeline
- if present, propagate constraints to downstream engines

---

## 11. NON-GOALS
- Does not pick plot events
- Does not decide reveals
- Does not validate truth
- Does not grant canon authority

---

## 12. FINAL STATEMENT

Stakes are what can be lost.
Tension is the pressure of loss approaching.

---

**STATUS:** Tension & Stakes Engine v1.0  
**DOMAIN:** ACTIVE
