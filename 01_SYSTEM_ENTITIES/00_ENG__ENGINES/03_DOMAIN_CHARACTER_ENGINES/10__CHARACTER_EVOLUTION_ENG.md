# 🧿 CHARACTER EVOLUTION ENGINE
## Canonical Engine Specification  
**LEVEL: L2 · DOMAIN ENGINE · VERSIONED CHARACTER STATES · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 10__CHARACTER_EVOLUTION_ENG.md
- ENGINE_ID: L2-DOM-CHARACTER-EVOLUTION-ENGINE-010
- UID: UE.ENT.ENG.DOM.CHARACTER.CHARACTER_EVOLUTION
- NAME: Character Evolution Engine
- CLASS: Domain Engine
- DOMAIN: Character
- CATEGORY: Versioning, Snapshots, Arc Phases & Evolution Ledger
- LEVEL: L2
- STATUS: FINAL
- FAILURE_MODE: fail-closed (for evolution traceability)
- EDITABLE: true
- BYPASS_ALLOWED: false (within character pipeline)

### ABSOLUTE RULE
> If evolution is not recorded as deltas, the character becomes a retcon machine.

---

## 1. PURPOSE

Character Evolution Engine records and manages **character change over time** as explicit, traceable evolution.

It produces:
- **EVOLUTION_LEDGER** (versioned log of character state snapshots + deltas)
- **ARC_PHASE_MAP** (phase progression and expected change gates)

It guarantees:
- stable baseline (v0)
- discrete evolution steps (v1, v2, …)
- explicit reasons for change (turning point, trauma, choice, relationship shift)
- prevention of silent retcons (changes without record)

This engine is the character-layer equivalent of continuity + version control.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define baseline snapshot (v0) from Character Core
- Define arc phases (setup → pressure → break → rebuild → integration)
- Record state snapshots with deltas across:
  - motives
  - values
  - psyche
  - behavior tendencies
  - relationships
  - scars/growth axes
- Validate that changes are earned (must reference turning points/costs)
- Detect silent retcons and flag them
- Provide evolution repair suggestions (missing gate, missing cost, missing bridge)

### OUT-OF-SCOPE (FORBIDDEN)
- Creating character core (Core Engine)
- Defining plot events as canon
- Approving retcons (Governance required)
- Writing scenes/dialogue

---

## 3. EVOLUTION MODEL

### 3.1 Arc Phases (fixed set)
- PHASE_0_BASELINE
- PHASE_1_SETUP
- PHASE_2_PRESSURE
- PHASE_3_BREAK
- PHASE_4_REBUILD
- PHASE_5_INTEGRATION

Phases may be skipped only if justified and recorded.

### 3.2 Snapshot Domains (fixed)
- CORE (anchors/invariants/boundaries)
- MOTIVES (wants/needs/drives/goals)
- VALUES (hierarchy/taboos/exceptions)
- PSYCHE (modes/triggers/defenses/regulation)
- BEHAVIOR (rules/tendencies/stress behaviors)
- RELATIONSHIPS (edge ladders/power loops)
- SCARS_GROWTH (wounds/scars/growth axes)

### 3.3 Delta Types (fixed)
- SHIFT (gradual change)
- BREAK (sudden rupture)
- INTEGRATION (stable improvement)
- REGRESSION (backslide)
- RETCON_FLAG (revision without bridge; requires governance handling)

---

## 4. INPUT ARTIFACTS

### 4.1 INPUT — EVOLUTION_REQUEST
**REQUIRED FIELDS**
- `evo_id`
- `timestamp`
- `char_core_profile_ref`
- `motivation_map_ref`
- `value_profile_ref`
- `psyche_model_ref`
- `behavior_profile_ref`
- `relationship_map_ref` (optional if solo character)
- `growth_trauma_refs` (recommended)
- `structure_plan_ref` (recommended for phase mapping)
- `continuity_registry_ref` (recommended)
- `trace_id` (optional)

Missing required fields → REJECT.

### 4.2 INPUT — EVOLUTION_UPDATE
**REQUIRED FIELDS**
- `evo_id`
- `timestamp`
- `char_id`
- `from_version`
- `to_version`
- `phase`
- `delta_summary`
- `trigger_event_ref` (turning point / choice / loss / reveal)
- `cost_paid` (explicit)
- `domains_changed` (list)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 5. OUTPUT ARTIFACTS

### 5.1 OUTPUT — EVOLUTION_LEDGER
**REQUIRED FIELDS**
- `evo_id`
- `char_id`
- `baseline_version` = v0
- `versions` (ordered list)
Each version entry includes:
- `version_id` (v0, v1, ...)
- `phase`
- `snapshot` (domains from 3.2; may be partial but must be declared)
- `deltas` (list: {domain, delta_type, what_changed, why, cost, references})
- `earned_check` (PASS | BORDERLINE | FAIL)
- `retcon_flags` (if any)
- `timestamp`
- `trace_id` (if provided)

### 5.2 OUTPUT — ARC_PHASE_MAP
- `evo_id`
- `phase_plan` (phase → expected evolution gates)
- `gate_checks` (what must happen before advancing)
- `regression_policy` (when regression is expected/allowed)
- `integration_conditions` (what counts as stable change)

### 5.3 OUTPUT — EVOLUTION_VERDICT
- `evo_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 6. CORE OPERATIONS

- OP_01: BUILD_BASELINE_SNAPSHOT (v0)
- OP_02: MAP_ARC_PHASES_TO_STRUCTURE
- OP_03: APPLY_GROWTH_TRAUMA_TURNING_POINTS
- OP_04: RECORD_VERSION_DELTAS
- OP_05: CHECK_EARNED_CHANGE (cost + bridge)
- OP_06: DETECT_SILENT_RETCONS
- OP_07: EMIT_LEDGER_AND_PHASE_MAP

---

## 7. SILENT RETCON RULE (HARD)

A change is a SILENT_RETCON if:
- a HARD invariant/boundary shifts
- without recorded delta + trigger + cost

Reaction:
- Mark RETCON_FLAG
- Verdict INVALID unless governance explicitly approves revision.

This engine does not approve retcons; it enforces traceability.

---

## 8. ACCESS MODEL

### WRITE
- Domain pipeline outputs only

### READ
- Narrative Continuity Engine (character state deltas)
- Scene Construction Engine (phase-consistent scenes)
- Dialogue/Speech Engines (voice drift constraints)
- Governance (if retcon flags require approval)

### DELETE
- Allowed for drafts; finalized ledger entries should be append-only in project context

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- No baseline v0
- Version jumps with no delta_summary/trigger/cost
- Phase changes with no gate checks
- Major domain changes without references
- Silent retcon detected (RETCON_FLAG) with no governance record

Reaction:
- Verdict INVALID (CRITICAL)
- Provide repairs: add deltas, add turning point refs, add costs, fix phase gates.

---

## 10. TRACE RULES

- trace_id optional unless orchestrator requires traced pipeline
- if present, propagate to continuity and governance trace

---

## 11. NON-GOALS
- Does not write scenes
- Does not grant canon authority
- Does not approve retcons
- Does not replace project governance

---

## 12. FINAL STATEMENT

A character is not a paragraph — it is a versioned system.
Evolution must be recorded, earned, and traceable.

---

**STATUS:** Character Evolution Engine v1.0  
**DOMAIN:** ACTIVE
