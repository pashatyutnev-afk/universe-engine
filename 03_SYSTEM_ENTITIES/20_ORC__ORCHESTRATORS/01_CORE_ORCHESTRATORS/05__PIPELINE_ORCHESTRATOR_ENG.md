# 🧩 MULTI-ENGINE PIPELINE ORCHESTRATOR ENGINE
## Canonical Orchestrator Specification  
**LEVEL: L3 · ORCHESTRATOR · META-PIPELINE · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 05__PIPELINE_ORCHESTRATOR_ENG.md
- ENGINE_ID: L3-ORCH-PIPELINE-ORCHESTRATOR-ENGINE-005
- UID: UE.ENT.ORCH.PIPELINE
- NAME: Multi-Engine Pipeline Orchestrator
- CLASS: Orchestrator
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (system integrity)
- EDITABLE: true
- BYPASS_ALLOWED: false

### ABSOLUTE RULE
> If the meta-pipeline is not explicit, the system becomes improvisation and cannot be trusted.

---

## 1. PURPOSE

Multi-Engine Pipeline Orchestrator is the **meta-orchestrator**.

It routes and coordinates:
- World Orchestrator
- Character Orchestrator
- Narrative Orchestrator
- Production Orchestrator

It enforces:
- dependency graph order
- global gates
- repair loops (rerun only what must be rerun)
- final packaging rules for “release-ready” and “register-ready” outputs

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Build and execute a dependency graph across orchestrators
- Select which orchestrators run based on target output and constraints
- Enforce global gates and cross-package consistency checks
- Produce a unified Pipeline Package (single artifact bundle)
- Emit a deterministic repair plan on failure (minimal reruns)

### OUT-OF-SCOPE (FORBIDDEN)
- Editing engine content silently
- Overriding Governance decisions
- Declaring canon truth (only governance can register canon)

---

## 3. REQUIRED INPUTS

### INPUT — PIPELINE_REQUEST (required fields)
- `pl_id`
- `timestamp`
- `project_goal`
- `target_output` = WORLD_ONLY | STORY_ONLY | STORY_WITH_WORLD | FULL_PRODUCTION
- `constraints_refs` (genre, realism, platform)
- `seeds` (world_seed, character_seed_list, narrative_seed optional)
- `trace_id` (recommended)

Missing required fields → REJECT.

---

## 4. META-PIPELINE DEPENDENCY GRAPH (DEFAULT)

### Default Dependency Order
A) World Orchestrator → produces WORLD_PACKAGE  
B) Character Orchestrator → uses WORLD refs → produces CHARACTER_PACKAGE  
C) Narrative Orchestrator → uses WORLD + CHARACTER → produces NARRATIVE_PACKAGE  
D) Production Orchestrator → uses NARRATIVE (+ optional WORLD/CHARACTER) → produces PRODUCTION_PACKAGE

### Allowed Variants (must be explicit)
- WORLD_ONLY: run A only
- STORY_ONLY: run C with minimal world/character refs (must be declared “light”)
- STORY_WITH_WORLD: run A then C (B optional if character depth not required)
- FULL_PRODUCTION: run A + B + C + D

---

## 5. GLOBAL GATES (HARD)

### Gate G1 — Canon/Standards Compliance
- Inputs reference required standards
- No orchestrator attempts to modify L1 canon

### Gate G2 — Cross-Package Consistency
- World laws not violated by narrative stakes or tech
- Timeline constraints respected in character evolution and plot
- Scarcity and capability bounds respected in conflicts and resolutions

### Gate G3 — Trace Integrity (if trace_id provided)
- trace_id propagated across packages
- missing trace_id in downstream outputs → FAIL (if trace required)

### Gate G4 — Output Declaration Safety
- “FINAL” may only be declared if:
  - all required gates passed
  - QA report exists for production outputs
  - repair plan is empty

---

## 6. OUTPUT ARTIFACTS (ASSEMBLED)

### 6.1 OUTPUT — PIPELINE_PACKAGE
**REQUIRED FIELDS**
- `pl_id`
- `target_output`
- `world_package_ref` (optional based on variant)
- `character_package_ref` (optional based on variant)
- `narrative_package_ref` (optional based on variant)
- `production_package_ref` (optional based on variant)
- `cross_package_consistency_report_ref`
- `global_gate_results_ref`
- `release_or_registration_ready` = true/false
- `trace_id`

### 6.2 OUTPUT — PIPELINE_VERDICT
- `pl_id`
- `verdict` = PASS | FAIL | PARTIAL
- `failed_gates` (list)
- `missing_packages` (list)
- `issues` (list)
- `repair_plan` (minimal rerun steps)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 7. REPAIR LOOP LOGIC (MINIMAL RERUN)

Repair plan must follow:
- rerun the smallest possible unit
- never rerun downstream until upstream gates pass

Examples:
- If world law contradiction → rerun World pipeline only
- If character evolution violates timeline → rerun Character stages E only (if supported)
- If twist plan has no foreshadowing → rerun Narrative Stage C
- If QA fails in production → rerun Production QA + affected generation stage

---

## 8. ROUTING RULES (HARD)

- Orchestrators are treated as black boxes producing packages.
- Meta-orchestrator routes references, not raw internals.
- Cross-package checks must not mutate packages; only report issues.
- Any CRITICAL issue → FAIL with explicit repair steps.

---

## 9. DEPENDENCIES

### REQUIRED
- World Orchestrator (06/03) when target requires world grounding
- Narrative Orchestrator (06/01) for story outputs
- Production Orchestrator (06/04) for release outputs

### OPTIONAL
- Character Orchestrator (06/02) when deep character consistency is required
- Governance audit/consistency/change-control for traced production

---

## 10. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- Global gate failure (G1/G2)
- Missing required package for selected target_output
- Cross-package contradictions with no valid repair path
- Declaring final without passing gates

Reaction:
- Verdict FAIL (CRITICAL)
- Emit repair plan with minimal reruns.

---

## 11. TRACE RULES

- trace_id must propagate to:
  - all orchestrator requests
  - all packages
  - final pipeline package

If trace is required and broken → FAIL.

---

## 12. NON-GOALS
- Does not produce story/world content itself
- Does not act as governance authority
- Does not replace QA engines

---

## 13. FINAL STATEMENT

A system is only real if its pipeline is explicit.
Meta-orchestrator makes the pipeline explicit.

---

**STATUS:** Multi-Engine Pipeline Orchestrator v1.0  
**LAYER:** ACTIVE
