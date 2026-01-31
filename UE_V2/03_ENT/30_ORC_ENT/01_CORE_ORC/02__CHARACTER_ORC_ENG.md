# 🧑‍🎭 CHARACTER ORCHESTRATOR ENGINE
## Canonical Orchestrator Specification  
**LEVEL: L3 · ORCHESTRATOR · CHARACTER PIPELINE · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 02__CHARACTER_ORCHESTRATOR_ENG.md
- ENGINE_ID: L3-ORCH-CHARACTER-ORCHESTRATOR-ENGINE-002
- UID: UE.ENT.ORCH.CHARACTER
- NAME: Character Orchestrator
- CLASS: Orchestrator
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (character integrity)
- EDITABLE: true
- BYPASS_ALLOWED: false

### ABSOLUTE RULE
> If a character has no internal logic, every scene becomes random acting.

---

## 1. PURPOSE

Character Orchestrator executes the **character engine pipeline** in correct order.

It ensures:
- core identity precedes motivations
- values constrain psychology and behavior
- relationships derive from needs and history
- trauma/growth produce evolution (not teleport changes)
- final character profile is consistent and usable across narrative production

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Choose and run character engines in defined order
- Route artifacts between engines
- Enforce gating checks (required outputs)
- Detect contradictions and fail-closed
- Assemble final Character Package ready for downstream narrative/orchestration usage

### OUT-OF-SCOPE (FORBIDDEN)
- Canon authority decisions (Governance)
- Overriding world laws and timeline constraints
- “Fixing” characters by rewriting outputs silently (must emit repair plan)

---

## 3. REQUIRED INPUTS

### INPUT — CHARACTER_PIPELINE_REQUEST (required fields)
- `cp_id`
- `timestamp`
- `project_goal` (one paragraph)
- `character_seed_list` (list: minimal character concepts)
- `constraints_refs` (genre, tone, target realism)
- `world_refs` (recommended: world law/timeline/civilizations)
- `trace_id` (recommended)

Missing required fields → REJECT.

---

## 4. PIPELINE ORDER (HARD)

### Stage A — Identity Core
1) Character Core Engine (04_DOMAIN_CHARACTER_ENGINES/01)

**Gate A:** character identity anchor exists per character

### Stage B — Motivation & Values
2) Motivation & Desire Engine (04/02)
3) Moral & Value Engine (04/03)

**Gate B:** desires + value constraints exist

### Stage C — Psychology & Behavior
4) Character Psychology Engine (04/04)
5) Character Behavior Engine (04/05)

**Gate C:** psyche explains behavior patterns

### Stage D — Social Fabric & Voice
6) Relationship Engine (04/06)
7) Dialogue Engine (04/07)
8) Speech Naturalization Engine (04/08)

**Gate D:** relationships + voice model exist

### Stage E — Change Over Time
9) Growth & Trauma Engine (04/09)
10) Character Evolution Engine (04/10)

**Gate E:** evolution is causally linked (no teleport arcs)

---

## 5. OUTPUT ARTIFACTS (ASSEMBLED)

### 5.1 OUTPUT — CHARACTER_PACKAGE
**REQUIRED FIELDS**
- `cp_id`
- `character_profiles` (list of Character Profile refs)
- `core_anchors_ref`
- `motivation_maps_ref`
- `value_maps_ref`
- `psychology_models_ref`
- `behavior_patterns_ref`
- `relationship_graph_ref`
- `dialogue_profile_ref`
- `speech_style_profile_ref`
- `growth_trauma_map_ref`
- `evolution_arcs_ref`
- `cross_character_consistency_report_ref`
- `trace_id`

### 5.2 OUTPUT — ORCHESTRATION_VERDICT
- `cp_id`
- `verdict` = PASS | FAIL | PARTIAL
- `missing_artifacts` (list)
- `consistency_issues` (list)
- `repair_plan` (ordered steps to fix)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 6. ROUTING RULES (HARD)

- Character Core is read-only after Gate A.
- Motivation must not contradict Core anchors without explicit retcon flags.
- Values constrain behavior; behavior cannot violate values repeatedly without psychological mechanism.
- Relationships require motives/history references.
- Dialogue profile must be derived from psychology + social position.
- Evolution must reference Growth/Trauma triggers and timeline constraints.
- If cross-character consistency fails (two characters occupy impossible roles/relations) → FAIL.

---

## 7. DEPENDENCIES

### REQUIRED
- Character engines (04_DOMAIN_CHARACTER_ENGINES)

### OPTIONAL (BUT RECOMMENDED)
- Timeline model (for evolution pacing)
- Civilization passports (for norms and roles)
- Governance audit/consistency gates

---

## 8. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- Missing any Stage Gate artifact
- Psyche does not explain behavior (behavior is random list)
- Relationships contradict core motivations with no bridge
- Dialogue/voice contradicts psychology/social position without explanation
- Evolution arc changes traits with no causal triggers
- Multiple character profiles contradict each other structurally

Reaction:
- Verdict FAIL (CRITICAL)
- Emit repair plan listing exactly which stage to rerun and why.

---

## 9. TRACE RULES

- trace_id must propagate to all outputs
- if audit log is active, record:
  - stage start/end
  - gate results
  - fail reasons

---

## 10. NON-GOALS
- Does not write dialogue scenes
- Does not canonize character facts
- Does not replace narrative orchestrator

---

## 11. FINAL STATEMENT

Characters are systems.
Orchestrator makes the system coherent.

---

**STATUS:** Character Orchestrator v1.0  
**LAYER:** ACTIVE
