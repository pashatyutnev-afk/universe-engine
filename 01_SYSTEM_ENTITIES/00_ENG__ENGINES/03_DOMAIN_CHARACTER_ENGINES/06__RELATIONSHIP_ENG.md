# 🤝 RELATIONSHIP ENGINE
## Canonical Engine Specification  
**LEVEL: L2 · DOMAIN ENGINE · BOND SYSTEM · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 06__RELATIONSHIP_ENG.md
- ENGINE_ID: L2-DOM-RELATIONSHIP-ENGINE-006
- UID: UE.ENT.ENG.DOM.CHARACTER.RELATIONSHIP
- NAME: Relationship Engine
- CLASS: Domain Engine
- DOMAIN: Character
- CATEGORY: Bonds, Trust Ladder, Conflict Loops & Relationship Dynamics
- LEVEL: L2
- STATUS: FINAL
- FAILURE_MODE: fail-closed (for relationship coherence)
- EDITABLE: true
- BYPASS_ALLOWED: false (within character pipeline)

### ABSOLUTE RULE
> Relationships are systems: they must have history, current state, and direction of change.

---

## 1. PURPOSE

Relationship Engine produces a **Relationship Map** describing how characters connect.

It guarantees:
- bond type definition (ally, rival, mentor, family, etc.)
- trust and intimacy levels over time
- power balance and dependency structure
- conflict loops (how they fight and repair)
- triggers and turning points that change the bond

It does not write scenes.
It defines relationship constraints that scenes must respect.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define relationship types and labels between characters
- Define trust ladder and intimacy ladder (0..10)
- Define power balance (who leads, who depends)
- Define attachment interaction patterns (avoidant/anxious/secure combos)
- Define conflict loop: trigger → escalation → rupture → repair style
- Define bond growth potential and break conditions
- Validate relational consistency with motives/values/psyche
- Provide repair suggestions (bridges, missing history notes)

### OUT-OF-SCOPE (FORBIDDEN)
- Dialogue writing (Dialogue Engine)
- Full behavior simulation (Behavior Engine)
- Canon authority decisions (Governance)
- World politics/economy design (World engines)

---

## 3. RELATIONSHIP MODEL

### 3.1 Bond Types (fixed set)
- FAMILY
- FRIENDSHIP
- ROMANTIC
- MENTORSHIP
- PARTNERSHIP
- ALLIANCE
- RIVALRY
- ENMITY
- AUTHORITY (boss/subordinate)
- TRANSACTIONAL (deal-based)

Multiple types may coexist (primary + secondary).

### 3.2 Ladders (fixed)
- TRUST: 0..10
- INTIMACY: 0..10
- RESENTMENT: 0..10
- DEPENDENCY: 0..10

### 3.3 Power Balance
- power_balance: A_DOMINANT | BALANCED | B_DOMINANT
- leverage_sources: status, money, secrets, strength, duty, love

### 3.4 Conflict Loop Template
- `trigger`
- `escalation_style`
- `rupture_point`
- `repair_style`
- `scar` (what never fully heals)
- `bond_upgrade_condition`

---

## 4. INPUT ARTIFACTS

### 4.1 INPUT — RELATIONSHIP_REQUEST
**REQUIRED FIELDS**
- `rel_id`
- `timestamp`
- `character_set_refs` (2+ characters)
- `char_core_profiles_refs`
- `motivation_maps_refs` (recommended)
- `value_profiles_refs` (recommended)
- `psyche_models_refs` (recommended)
- `world_constraints_refs`
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 5. OUTPUT ARTIFACTS

### 5.1 OUTPUT — RELATIONSHIP_MAP
**REQUIRED FIELDS**
- `rel_id`
- `nodes` (characters list)
- `edges` (list: relationship edges)
Each edge must include:
- `edge_id`
- `char_a`
- `char_b`
- `bond_types` (primary/secondary)
- `trust_0_10`
- `intimacy_0_10`
- `resentment_0_10`
- `dependency_0_10`
- `power_balance`
- `leverage_sources`
- `shared_history` (short)
- `current_tension` (short)
- `conflict_loop` (template fields)
- `break_conditions`
- `growth_potential`
- `scene_constraints` (non-binding rules: “A won’t confide unless…”)
- `trace_id` (if provided)

### 5.2 OUTPUT — RELATIONSHIP_VERDICT
- `rel_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 6. CORE OPERATIONS

- OP_01: IDENTIFY_BOND_TYPES
- OP_02: ASSIGN_LADDER_LEVELS
- OP_03: DEFINE_POWER_BALANCE_AND_LEVERAGE
- OP_04: BUILD_CONFLICT_LOOPS
- OP_05: CHECK_ALIGNMENT_WITH_MOTIVES_VALUES_PSYCH
- OP_06: EMIT_RELATIONSHIP_MAP

---

## 7. ACCESS MODEL

### WRITE
- Domain pipeline outputs only

### READ
- Dialogue Engine (speech intent depends on trust/power)
- Behavior Engine (conflict style shifts by bond)
- Scene Construction Engine (relationship constraints for scenes)
- Continuity Engine (relationship state deltas tracked)
- Character Evolution Engine (bond evolution over arcs)

### DELETE
- Allowed for drafts; finalization per project governance

---

## 8. DEPENDENCIES

### REQUIRED
- Character Core Profiles (identity anchors)
- World constraints (culture norms, law, taboo)

### FORBIDDEN
- Relationships with no history AND no current tension AND no direction (dead edge)
- Treating relationship map as canon authority

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- Edge missing ladders (trust/intimacy/etc.)
- No conflict loop defined for any meaningful bond
- Bond types contradict world constraints without bridge
- Power balance undefined when authority/transactional bond exists
- Relationship changes without recorded state delta (continuity break)

Reaction:
- Verdict INVALID (CRITICAL)
- Provide repairs: add ladders, add conflict loop, define leverage and repair style.

---

## 10. TRACE RULES

- trace_id optional unless orchestrator requires traced pipeline
- if present, propagate into downstream artifacts

---

## 11. NON-GOALS
- Does not write dialogue
- Does not create plot events
- Does not grant canon authority
- Does not replace continuity engine

---

## 12. FINAL STATEMENT

Relationships are living contracts.
Define the ladders, loops, and leverage — and scenes become inevitable.

---

**STATUS:** Relationship Engine v1.0  
**DOMAIN:** ACTIVE
