# 🎬 NARRATIVE ORCHESTRATOR ENGINE
## Canonical Orchestrator Specification  
**LEVEL: L3 · ORCHESTRATOR · NARRATIVE PIPELINE · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 01__NARRATIVE_ORCHESTRATOR_ENG.md
- ENGINE_ID: L3-ORCH-NARRATIVE-ORCHESTRATOR-ENGINE-001
- UID: UE.ENT.ORCH.NARRATIVE
- NAME: Narrative Orchestrator
- CLASS: Orchestrator
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (pipeline integrity)
- EDITABLE: true
- BYPASS_ALLOWED: false

### ABSOLUTE RULE
> Narrative quality is pipeline quality. Wrong order = broken story.

---

## 1. PURPOSE

Narrative Orchestrator executes the **narrative engine pipeline** in correct order.

It ensures:
- structure precedes scene writing
- stakes precede climax/resolution decisions
- continuity gates prevent silent contradictions
- outputs are assembled as a coherent narrative package

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Choose and run narrative engines in defined order
- Route artifacts between engines
- Enforce gating checks (required outputs)
- Collect and assemble narrative outputs
- Emit orchestration verdict and repair plan

### OUT-OF-SCOPE (FORBIDDEN)
- Writing canon decisions (Governance)
- Overriding world law/structure constraints
- Inventing character core without character pipeline (unless explicitly allowed)

---

## 3. REQUIRED INPUTS

### INPUT — NARRATIVE_PIPELINE_REQUEST (required fields)
- `np_id`
- `timestamp`
- `project_goal` (one paragraph)
- `constraints_refs` (genre, tone, scope)
- `world_refs` (optional but recommended: world law/structure/timeline)
- `character_refs` (optional but recommended)
- `trace_id` (recommended)

Missing required fields → REJECT.

---

## 4. PIPELINE ORDER (HARD)

### Stage A — Logic & Structure
1) Narrative Logic Engine (03_DOMAIN_NARRATIVE_ENGINES/01)
2) Story Structure Engine (03/02)
3) Dramatic Arc Engine (03/03)

**Gate A:** structure package exists

### Stage B — Scene Assembly
4) Scene Construction Engine (03/04)
5) Pacing & Rhythm Engine (03/05)
6) Tension & Stakes Engine (03/06)

**Gate B:** scene list + pacing + stakes are consistent

### Stage C — Reveal Architecture
7) Foreshadowing Engine (03/07)
8) Twist & Reveal Engine (03/08)

**Gate C:** reveals are seeded and paid for

### Stage D — Continuity & Meaning
9) Narrative Continuity Engine (03/09)
10) Theme & Meaning Engine (03/10)

**Gate D:** continuity pass + theme map exist

---

## 5. OUTPUT ARTIFACTS (ASSEMBLED)

### 5.1 OUTPUT — NARRATIVE_PACKAGE
**REQUIRED FIELDS**
- `np_id`
- `logic_ruleset_ref`
- `structure_blueprint_ref`
- `dramatic_arc_map_ref`
- `scene_list_ref`
- `pacing_profile_ref`
- `stakes_matrix_ref`
- `foreshadowing_map_ref`
- `twist_reveal_plan_ref`
- `continuity_report_ref`
- `theme_map_ref`
- `trace_id`

### 5.2 OUTPUT — ORCHESTRATION_VERDICT
- `np_id`
- `verdict` = PASS | FAIL | PARTIAL
- `missing_artifacts` (list)
- `consistency_issues` (list)
- `repair_plan` (ordered steps to fix)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 6. ROUTING RULES (HARD)

- Structure artifacts are read-only once Gate A passes.
- Scene Construction cannot run without Structure Blueprint.
- Twists cannot be approved without Foreshadowing seeds.
- Continuity engine runs after all narrative engines produce outputs.
- If continuity fails → orchestrator FAIL (no downstream packaging).

---

## 7. DEPENDENCIES

### REQUIRED
- Governance: Audit Log, Consistency (recommended gating)
- Narrative engines (03_DOMAIN_NARRATIVE_ENGINES)

### OPTIONAL (BUT RECOMMENDED)
- Character pipeline outputs (for voice and motivations)
- World pipeline outputs (laws, timeline, geopolitics)

---

## 8. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- Missing any required Stage Gate artifact
- Continuity report returns CRITICAL contradictions
- Twist plan without foreshadowing seeds
- Stakes undefined but climax/resolution attempted

Reaction:
- Verdict FAIL (CRITICAL)
- Emit repair plan with exact missing artifact list.

---

## 9. TRACE RULES

- trace_id must propagate to all outputs
- if audit log is active, record:
  - stage start/end
  - gate results
  - fail reasons

---

## 10. NON-GOALS
- Does not write prose
- Does not canonize outputs
- Does not replace governance approvals

---

## 11. FINAL STATEMENT

Narrative is an engineered sequence.
Orchestrator enforces the sequence.

---

**STATUS:** Narrative Orchestrator v1.0  
**LAYER:** ACTIVE
