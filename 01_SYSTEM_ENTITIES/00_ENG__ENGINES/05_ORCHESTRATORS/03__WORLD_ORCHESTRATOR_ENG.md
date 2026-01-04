# 🌍 WORLD ORCHESTRATOR ENGINE
## Canonical Orchestrator Specification  
**LEVEL: L3 · ORCHESTRATOR · WORLD PIPELINE · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 03__WORLD_ORCHESTRATOR_ENG.md
- ENGINE_ID: L3-ORCH-WORLD-ORCHESTRATOR-ENGINE-003
- UID: UE.ENT.ORCH.WORLD
- NAME: World Orchestrator
- CLASS: Orchestrator
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (world coherence)
- EDITABLE: true
- BYPASS_ALLOWED: false

### ABSOLUTE RULE
> The world must be built in dependency order, or every downstream system becomes hallucination.

---

## 1. PURPOSE

World Orchestrator executes the **world-building pipeline** in correct dependency order.

It ensures:
- structure precedes laws
- laws constrain timeline
- timeline constrains civilizations
- civilizations + scarcity constrain conflict and geopolitics
- technology/magic is priced and bounded
- belief systems are mapped to societies and epochs
- ecology sets hard limits and collapse dynamics

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Run world domain engines in defined order
- Route artifacts between world engines
- Enforce gating checks (required outputs)
- Detect contradictions and fail-closed
- Assemble World Package for narrative/production use

### OUT-OF-SCOPE (FORBIDDEN)
- Canon authority decisions (Governance)
- Writing narrative plots (Narrative pipeline)
- Writing character psychology (Character pipeline)
- Silent edits of engine outputs (must emit repair plan)

---

## 3. REQUIRED INPUTS

### INPUT — WORLD_PIPELINE_REQUEST (required fields)
- `wp_id`
- `timestamp`
- `project_goal` (one paragraph)
- `world_seed` (short description of setting)
- `constraints_refs` (genre, realism, scope)
- `required_domains` (list: which world subsystems must exist)
- `trace_id` (recommended)

Missing required fields → REJECT.

---

## 4. PIPELINE ORDER (HARD)

### Stage A — Structural Base
1) World Structure Engine (05_DOMAIN_WORLD_ENGINES/01)

**Gate A:** WORLD_STRUCTURE_GRAPH exists

### Stage B — World Invariants
2) World Law Engine (05/02)

**Gate B:** WORLD_LAWSET exists and contradictions resolved

### Stage C — Time & History
3) Timeline & Epoch Engine (05/03)

**Gate C:** TIMELINE_MODEL exists with anchors + causal links

### Stage D — Societies
4) Civilization Engine (05/04)

**Gate D:** CIVILIZATION_PASSPORTS exist and mapped to epochs

### Stage E — Power & Conflict
5) Conflict & Power Engine (05/05)

**Gate E:** POWER_CONFLICT_MATRIX exists with costs + escalation ladders

### Stage F — Actor Moves
6) Geopolitics Engine (05/06)

**Gate F:** GEOPOLITICS_MAP exists (actors, interests, edges, move costs)

### Stage G — Scarcity & Flows
7) Economy & Resource Engine (05/07)

**Gate G:** RESOURCE_FLOW_MODEL exists (scarcity + bottlenecks + allocation)

### Stage H — Capability Bounds
8) Technology & Magic Engine (05/08)

**Gate H:** CAPABILITY_MATRIX exists (limits + costs + counters)

### Stage I — Meaning Systems
9) Mythology & Belief Engine (05/09)

**Gate I:** BELIEF_SYSTEM_MAP exists (distribution + truth layers)

### Stage J — Environmental Limits
10) Environment & Ecology Engine (05/10)

**Gate J:** ECOLOGY_MODEL exists (capacity + hazards + feedback loops)

---

## 5. OUTPUT ARTIFACTS (ASSEMBLED)

### 5.1 OUTPUT — WORLD_PACKAGE
**REQUIRED FIELDS**
- `wp_id`
- `world_structure_graph_ref`
- `world_lawset_ref`
- `timeline_model_ref`
- `civilization_passports_refs`
- `power_conflict_matrix_ref`
- `geopolitics_map_ref`
- `resource_flow_model_ref`
- `capability_matrix_ref`
- `belief_system_map_ref`
- `ecology_model_ref`
- `world_consistency_report_ref`
- `trace_id`

### 5.2 OUTPUT — ORCHESTRATION_VERDICT
- `wp_id`
- `verdict` = PASS | FAIL | PARTIAL
- `missing_artifacts` (list)
- `consistency_issues` (list)
- `repair_plan` (ordered steps to fix)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 6. ROUTING RULES (HARD)

- Stage outputs are read-only after their gate passes.
- World Lawset constrains ALL downstream artifacts.
- Timeline must reference law-consistent events; impossible events require explicit exception rules.
- Economy must reflect ecology capacity + regeneration; no infinite growth.
- Tech/Magic must align to scarcity + world laws; “unstoppable” requires counters or prohibition.
- Geopolitics moves must be priced (cost + retaliation risk).
- Belief truth layers must be explicit (CONFIRMED/PLAUSIBLE/LEGEND/UNKNOWN).
- Any unresolved CRITICAL contradiction at any gate → FAIL.

---

## 7. REQUIRED CONSISTENCY CHECKS (WORLD)

World Orchestrator MUST run a final WORLD_CONSISTENCY pass:
- law contradictions (HARD laws cannot be violated)
- timeline breaks (cause/effect gaps)
- economy/ecology mismatch (capacity, regeneration)
- power mismatch (weak actor acting omnipotent)
- tech exploit loopholes (infinite energy/instant travel)
- belief distribution mismatch (belief with no carriers/institutions)

Output must list:
- issues
- severity
- repair steps (which engine to rerun)

---

## 8. DEPENDENCIES

### REQUIRED
- World domain engines (05_DOMAIN_WORLD_ENGINES)

### OPTIONAL (BUT RECOMMENDED)
- Governance engines: Audit Log, Consistency, Change Control
- Validation engines: Scientific Plausibility, Historical Accuracy, Fact Consistency

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- Any stage gate missing artifact
- Lawset contradictions unresolved
- Timeline anchors missing
- Economy model lacks scarcity/bottlenecks
- Tech/Magic has HIGH exploit risk without mitigation
- Ecology has no carrying capacity/feedback loops

Reaction:
- Verdict FAIL (CRITICAL)
- Emit repair plan listing exact stage(s) to rerun and why.

---

## 10. TRACE RULES

- trace_id must propagate to all outputs
- if audit log is active, record:
  - stage start/end
  - gate results
  - fail reasons
  - final package emission

---

## 11. NON-GOALS
- Does not write plot or scenes
- Does not canonize world facts
- Does not replace governance approvals

---

## 12. FINAL STATEMENT

Worldbuilding is dependency order.
Orchestrator enforces the order.

---

**STATUS:** World Orchestrator v1.0  
**LAYER:** ACTIVE
