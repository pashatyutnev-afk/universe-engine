# 🧱 WORLD LAW ENGINE
## Canonical Engine Specification  
**LEVEL: L2 · DOMAIN ENGINE · WORLD INVARIANTS · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 02__WORLD_LAW_ENG.md
- ENGINE_ID: L2-DOM-WORLD-LAW-ENGINE-002
- UID: UE.ENT.ENG.DOM.WORLD.WORLD_LAW
- NAME: World Law Engine
- CLASS: Domain Engine
- DOMAIN: World
- CATEGORY: Physics, Magic, Social Laws & Invariants
- LEVEL: L2
- STATUS: FINAL
- FAILURE_MODE: fail-closed (for law consistency)
- EDITABLE: true
- BYPASS_ALLOWED: false (within world pipeline)

### ABSOLUTE RULE
> If laws are undefined, anything can happen — and nothing matters.

---

## 1. PURPOSE

World Law Engine defines the **rules that cannot be casually broken**.

It produces a **WORLD_LAWSET**:
- physical invariants (time, distance, energy, limits)
- magic/tech invariants (capabilities + constraints)
- social/legal invariants (what society permits/punishes)
- exception rules (rare, priced, traceable)
- exploit checks (prevent “cheat codes”)

This engine ensures the world remains logically playable.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define law categories and invariants
- Define allowed exceptions and their costs
- Define enforcement mechanisms (who/what enforces laws)
- Define contradiction detection rules across laws
- Define exploit prevention rules (no infinite loops, no free power)
- Define “consequence mapping” for law violations (non-binding but required)

### OUT-OF-SCOPE (FORBIDDEN)
- Building geography/topology (World Structure Engine)
- Building history/epochs (Timeline & Epoch Engine)
- Building culture/institutions in depth (Civilization Engine)
- Canon authority decisions (Governance)

---

## 3. LAW MODEL

### 3.1 Law Categories (fixed)
- PHYSICAL_LAWS
- TECHNOLOGICAL_LIMITS
- MAGIC_LAWS (optional)
- BIOLOGICAL_LIMITS
- SOCIAL_NORMS
- LEGAL_RULES
- INFORMATION_LAWS (secrecy, access, censorship)
- RESOURCE_CONSTRAINTS (scarcity rules)

### 3.2 Law Object (required fields)
- `law_id`
- `category`
- `statement` (one sentence)
- `invariant_strength` = HARD | MEDIUM | SOFT
- `scope` (where it applies)
- `enforcement` (who/what enforces it)
- `violation_cost` (what it costs to break)
- `violation_consequence` (what happens after break)
- `exceptions` (optional list; must include cost + limits)
- `exploit_risk` = LOW | MEDIUM | HIGH
- `notes`

### 3.3 Exception Rule (required)
An exception must specify:
- entry condition
- cost
- limit (frequency/scale)
- traceability (can it be detected)

---

## 4. INPUT ARTIFACTS

### 4.1 INPUT — WORLD_LAW_REQUEST
**REQUIRED FIELDS**
- `wl_id`
- `timestamp`
- `world_scope_ref` (from structure engine or scope description)
- `genre_constraints_refs`
- `tech_magic_presence` (none/tech/magic/both)
- `society_baseline` (one paragraph)
- `known_edge_cases` (optional list)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 5. OUTPUT ARTIFACTS

### 5.1 OUTPUT — WORLD_LAWSET
**REQUIRED FIELDS**
- `wl_id`
- `law_registry` (list of Law Objects)
- `law_priority_notes` (which laws override others and why)
- `exception_registry` (flattened list for audit)
- `enforcement_map` (enforcer → what they enforce)
- `consequence_map` (violation_type → consequence)
- `contradiction_checks` (auto-detected conflicts)
- `exploit_checks` (auto-detected loopholes + fixes)
- `trace_id` (if provided)

### 5.2 OUTPUT — WORLD_LAW_VERDICT
- `wl_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 6. CORE OPERATIONS

- OP_01: DEFINE_LAW_CATEGORIES
- OP_02: DRAFT_INVARIANTS (hard/medium/soft)
- OP_03: DEFINE_ENFORCEMENT_MECHANISMS
- OP_04: DEFINE_EXCEPTIONS_AND_COSTS
- OP_05: RUN_CONTRADICTION_AND_EXPLOIT_CHECKS
- OP_06: EMIT_WORLD_LAWSET

---

## 7. ACCESS MODEL

### WRITE
- Domain pipeline outputs only

### READ
- Technology & Magic Engine (capability bounds)
- Civilization Engine (institutions align to laws)
- Economy & Resource Engine (scarcity constraints)
- Conflict & Power Engine (what is possible in warfare/power plays)
- Narrative engines (stakes and consequences)
- Validation engines (plausibility checks)

### DELETE
- Allowed for drafts; finalization per project governance

---

## 8. DEPENDENCIES

### REQUIRED
- Genre constraints (realism level)
- World scope reference (where laws apply)

### FORBIDDEN
- Laws with no enforcement AND no consequence (dead laws)
- Exceptions with no cost/limit (free cheats)
- Contradictory HARD laws without explicit hierarchy
- Treating lawset as canon authority

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- No HARD laws (world has no invariants)
- Exceptions outnumber invariants (world is loophole soup)
- Violation has no consequence (stakes collapse)
- Exploit risk HIGH with no mitigation
- Contradiction checks show unresolved HARD conflicts

Reaction:
- Verdict INVALID (CRITICAL)
- Provide repairs: add invariants, price exceptions, add enforcement/consequences.

---

## 10. TRACE RULES

- trace_id optional unless orchestrator requires traced pipeline
- if present, propagate to downstream world artifacts and continuity

---

## 11. NON-GOALS
- Does not build maps
- Does not write history
- Does not grant canon authority

---

## 12. FINAL STATEMENT

Laws are the gravity of the world.
Exceptions must be paid for — or meaning dies.

---

**STATUS:** World Law Engine v1.0  
**DOMAIN:** ACTIVE
