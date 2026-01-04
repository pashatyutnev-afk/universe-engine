# 🧭 GEOPOLITICS ENGINE
## Canonical Engine Specification  
**LEVEL: L2 · DOMAIN ENGINE · ACTORS & MOVES · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 06__GEOPOLITICS_ENG.md
- ENGINE_ID: L2-DOM-GEOPOLITICS-ENGINE-006
- UID: UE.ENT.ENG.DOM.WORLD.GEOPOLITICS
- NAME: Geopolitics Engine
- CLASS: Domain Engine
- DOMAIN: World
- CATEGORY: Actor Map, Interests, Constraints, Diplomacy & Move-Sets
- LEVEL: L2
- STATUS: FINAL
- FAILURE_MODE: fail-closed (for actor logic)
- EDITABLE: true
- BYPASS_ALLOWED: false (within world pipeline)

### ABSOLUTE RULE
> If actors have no interests and constraints, geopolitics becomes random.

---

## 1. PURPOSE

Geopolitics Engine defines **who the actors are** and **what moves they can make**.

It produces:
- **GEOPOLITICS_MAP** (actors, interests, alliances, rivalries)
- diplomacy and negotiation constraints
- strategic objectives and red lines
- move-set library (tools of influence and coercion)
- stability forecasts (non-binding)

This engine is not a simulator; it is a ruleset + map of intentions.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define geopolitical actors (states, blocs, factions, corporations, orders)
- Define interests (what they want) and constraints (what limits them)
- Define alliances, rivalries, dependencies and leverage
- Define red lines and escalation triggers
- Define diplomacy styles and negotiation patterns
- Define move-set options (trade, sabotage, treaties, proxy wars, etc.)
- Validate consistency with world structure, laws, timeline and power matrix
- Detect “free move” loopholes (actor can do anything without cost)

### OUT-OF-SCOPE (FORBIDDEN)
- Detailed war mechanics (Conflict & Power Engine owns escalation logic)
- Detailed resource flow accounting (Economy & Resource Engine)
- Deep culture construction (Civilization Engine)
- Canon authority decisions (Governance)

---

## 3. GEOPOLITICS MODEL

### 3.1 Actor Object (required fields)
- `actor_id`
- `name`
- `type` = STATE | BLOC | FACTION | CORPORATION | ORDER | NETWORK
- `home_scope` (territories/nodes reference)
- `strategic_objectives` (ranked list)
- `constraints` (hard limits: law, resources, legitimacy, tech)
- `red_lines` (what they will not tolerate)
- `diplomacy_style` (direct/covert/honor-bound/etc.)
- `influence_tools` (from move-set library)
- `dependencies` (what they rely on)
- `vulnerabilities` (what breaks them)

### 3.2 Relationship Edge (required)
- `edge_id`
- `actor_a`
- `actor_b`
- `relation_type` = ALLY | RIVAL | DEPENDENT | NEUTRAL | HOSTILE | PROXY
- `trust_level` 0..10
- `tension_level` 0..10
- `leverage` (who holds what over whom)
- `treaties` (optional list)
- `active_conflict` (optional)

### 3.3 Move-Set Library (fixed set)
- DIPLOMACY (talks, summits, recognition)
- TRADE (deals, embargo, sanctions)
- INFORMATION (propaganda, leaks, censorship)
- COVERT (sabotage, assassinations, infiltration)
- PROXY (armed groups, funding, training)
- MILITARY (posturing, strikes, occupation)
- LEGAL (courts, claims, legitimacy warfare)
- RELIGIOUS/IDEOLOGICAL (fatwas, crusades, doctrine pushes)
- TECHNOLOGICAL (tech denial, upgrades, cyber)
- HUMANITARIAN (aid as leverage)

Every move must include:
- cost profile
- plausibility constraints
- retaliation risk

---

## 4. INPUT ARTIFACTS

### 4.1 INPUT — GEOPOLITICS_REQUEST
**REQUIRED FIELDS**
- `geo_id`
- `timestamp`
- `actor_seeds` (list of minimal actor descriptions)
- `world_structure_graph_ref` (required)
- `world_lawset_ref` (required)
- `timeline_model_ref` (recommended)
- `power_conflict_matrix_ref` (recommended)
- `economy_resource_model_ref` (recommended)
- `constraints_refs` (project/genre constraints)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 5. OUTPUT ARTIFACTS

### 5.1 OUTPUT — GEOPOLITICS_MAP
**REQUIRED FIELDS**
- `geo_id`
- `actors` (list of Actor Objects)
- `relationships` (list of Relationship Edges)
- `interest_matrix` (actor → objectives ranked)
- `constraint_matrix` (actor → hard constraints)
- `red_line_registry` (actor → red lines)
- `move_set_library` (fixed set + per-actor availability)
- `active_flashpoints` (list: where tension is high + why)
- `diplomacy_patterns` (common negotiation loops)
- `loophole_checks` (auto-detected “actor can do anything” issues)
- `trace_id` (if provided)

### 5.2 OUTPUT — GEOPOLITICS_VERDICT
- `geo_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 6. CORE OPERATIONS

- OP_01: DEFINE_ACTOR_SET
- OP_02: DEFINE_INTERESTS_CONSTRAINTS_RED_LINES
- OP_03: BUILD_RELATIONSHIP_GRAPH
- OP_04: ASSIGN_MOVE_SETS_AND_COSTS
- OP_05: DETECT_FLASHPOINTS
- OP_06: RUN_LOOPHOLE_AND_CONSISTENCY_CHECKS
- OP_07: EMIT_GEOPOLITICS_MAP

---

## 7. ACCESS MODEL

### WRITE
- Domain pipeline outputs only

### READ
- Conflict & Power Engine (escalation triggers)
- Economy & Resource Engine (trade/embargo constraints)
- Timeline & Epoch Engine (historical rivalries)
- Mythology & Belief Engine (ideological drivers)
- Narrative engines (stakes in setting)

### DELETE
- Allowed for drafts; finalization per project governance

---

## 8. DEPENDENCIES

### REQUIRED
- World structure graph (where actors exist/move)
- World lawset (what moves are possible/illegal)

### FORBIDDEN
- Actors with no objectives
- Moves with no costs/retaliation risk
- Relationship edges with no tension/trust semantics
- Flashpoints without causes
- Treating geopolitics map as canon authority

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- Actor list empty or unanchored to locations
- No relationships defined (actors float in void)
- No constraints (actors can do anything)
- No move cost profiles (magic influence)
- Contradictions with power matrix (weak actor acting omnipotent) without explanation

Reaction:
- Verdict INVALID (CRITICAL)
- Provide repairs: add interests/constraints, add edges, price move-sets.

---

## 10. TRACE RULES

- trace_id optional unless orchestrator requires traced pipeline
- if present, propagate to continuity references

---

## 11. NON-GOALS
- Does not simulate turn-by-turn strategy
- Does not write wars or treaties as canon
- Does not grant canon authority

---

## 12. FINAL STATEMENT

Geopolitics is intent under constraint.
Define actors, and the world starts moving.

---

**STATUS:** Geopolitics Engine v1.0  
**DOMAIN:** ACTIVE
