# 🏛️ CIVILIZATION ENGINE
## Canonical Engine Specification  
**LEVEL: L2 · DOMAIN ENGINE · SOCIETY SYSTEMS · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 04__CIVILIZATION_ENG.md
- ENGINE_ID: L2-DOM-CIVILIZATION-ENGINE-004
- UID: UE.ENT.ENG.DOM.WORLD.CIVILIZATION
- NAME: Civilization Engine
- CLASS: Domain Engine
- DOMAIN: World
- CATEGORY: Culture, Institutions, Norms & Social Structure
- LEVEL: L2
- STATUS: FINAL
- FAILURE_MODE: fail-closed (for civilization coherence)
- EDITABLE: true
- BYPASS_ALLOWED: false (within world pipeline)

### ABSOLUTE RULE
> Civilization is constraint + meaning: without institutions and norms, society is noise.

---

## 1. PURPOSE

Civilization Engine defines **how societies actually function**.

It produces a **CIVILIZATION_PASSPORT** per civilization, faction-society, or major culture block.

It guarantees:
- institutions (who does what, with what authority)
- norms and taboos (what is permitted/punished)
- class/role structures (who has power and why)
- governance forms (how decisions are made)
- cultural identity markers (language, rituals, aesthetics)
- stability and fracture points (what can collapse it)

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define civilization identity + boundaries
- Define governance model + enforcement organs
- Define institutions (military, law, religion, science, trade, guilds)
- Define norms/taboos and social rewards/punishments
- Define class hierarchy and mobility rules
- Define education/knowledge distribution
- Define family, marriage, inheritance patterns (if relevant)
- Define cultural aesthetics (architecture, clothing, symbols) as tags
- Define stability/failure modes and reform/collapse triggers
- Validate compatibility with world laws and timeline epochs

### OUT-OF-SCOPE (FORBIDDEN)
- Full geopolitics simulation (Geopolitics Engine)
- Direct conflict planning (Conflict & Power Engine)
- Economy flow modeling (Economy & Resource Engine) beyond institutional notes
- Canon authority decisions (Governance)

---

## 3. CIVILIZATION MODEL

### 3.1 Core Objects
- CIVILIZATION: society block (may be empire, city-state network, nomad culture, station society)
- INSTITUTION: persistent org with mandate + power
- NORM: expected behavior rule
- TABOO: strong forbidden behavior
- CLASS: social tier with privileges/constraints
- LEGITIMACY_SOURCE: why power is accepted (bloodline, merit, faith, fear, law, tradition)
- STABILITY_PROFILE: what holds it together / what breaks it

### 3.2 Governance Forms (fixed set)
- MONARCHY
- OLIGARCHY
- THEOCRACY
- DEMOCRACY
- AUTOCRACY
- MERITOCRACY
- CORPORATE_STATE
- TRIBAL_COUNCIL
- ANARCHIC_NETWORK

### 3.3 Social Control Tools (tags)
- LAW
- RELIGION
- FORCE
- DEBT
- PROPAGANDA
- SURVEILLANCE
- HONOR_SHAME
- RITUAL

---

## 4. INPUT ARTIFACTS

### 4.1 INPUT — CIVILIZATION_REQUEST
**REQUIRED FIELDS**
- `civ_id`
- `timestamp`
- `world_structure_graph_ref` (recommended)
- `world_lawset_ref` (required)
- `timeline_model_ref` (recommended)
- `civilization_seed` (one paragraph: who they are)
- `scale_type` (city/region/empire/network/station)
- `constraints_refs` (genre/project constraints)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 5. OUTPUT ARTIFACTS

### 5.1 OUTPUT — CIVILIZATION_PASSPORT
**REQUIRED FIELDS**
- `civ_id`
- `name`
- `scope` (where they exist; nodes/regions if available)
- `epoch_presence` (which epochs they exist in)
- `identity_markers` (tags: language, symbols, aesthetics)
- `legitimacy_source`
- `governance_form`
- `institutions` (list: {inst_id, name, mandate, power_tools, enforcement})
- `law_and_justice` (how law works, punishments, due process)
- `norms` (list: key norms)
- `taboos` (list: key taboos + consequence)
- `class_structure` (list: {class_id, name, privileges, constraints, mobility_rule})
- `economy_notes` (light: what they value, how they trade; flows handled elsewhere)
- `knowledge_distribution` (who knows what; literacy/education)
- `military_security_notes` (light: who controls violence)
- `stability_profile` (cohesion factors, fracture points)
- `reform_and_collapse_triggers` (list)
- `external_relations_notes` (light: allies/enemies posture)
- `trace_id` (if provided)

### 5.2 OUTPUT — CIVILIZATION_VERDICT
- `civ_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 6. CORE OPERATIONS

- OP_01: DEFINE_IDENTITY_AND_SCOPE
- OP_02: SELECT_GOVERNANCE_AND_LEGITIMACY
- OP_03: BUILD_INSTITUTION_SET
- OP_04: DEFINE_NORMS_TABOOS_AND_CLASS_STRUCTURE
- OP_05: BUILD_STABILITY_AND_FAILURE_MODES
- OP_06: CHECK_COMPATIBILITY_WITH_LAWS_AND_TIMELINE
- OP_07: EMIT_CIVILIZATION_PASSPORT

---

## 7. ACCESS MODEL

### WRITE
- Domain pipeline outputs only

### READ
- Geopolitics Engine (actors + institutions)
- Economy & Resource Engine (institutional flow constraints)
- Conflict & Power Engine (who can mobilize power)
- Mythology & Belief Engine (belief systems often integrated)
- Narrative engines (social stakes, norms pressure)
- Validation engines (cultural accuracy / plausibility)

### DELETE
- Allowed for drafts; finalization per project governance

---

## 8. DEPENDENCIES

### REQUIRED
- World Lawset (what society must obey)
- Civilization seed (minimal identity)

### FORBIDDEN
- Institutions with no enforcement mechanism (paper institutions)
- Norms/taboos with no consequences (dead norms)
- Governance form with no legitimacy source (power unexplained)
- Civilization present in timeline with no epoch mapping
- Treating civilization passport as canon authority

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- No institutions defined
- No norms/taboos (cultureless society)
- No class/mobility rule (social structure undefined)
- Governance has no enforcement and no legitimacy
- Contradictions with world laws (e.g., outlawed tech as core institution) without exception/black-market bridge

Reaction:
- Verdict INVALID (CRITICAL)
- Provide repairs: add institutions, define enforcement, add norms/taboos, clarify legitimacy.

---

## 10. TRACE RULES

- trace_id optional unless orchestrator requires traced pipeline
- if present, propagate into geopolitics/economy/conflict dependencies

---

## 11. NON-GOALS
- Does not run geopolitics simulation
- Does not produce full economy model
- Does not grant canon authority

---

## 12. FINAL STATEMENT

Civilization is a machine of rules and meanings.
Define its institutions, and its people become understandable.

---

**STATUS:** Civilization Engine v1.0  
**DOMAIN:** ACTIVE
