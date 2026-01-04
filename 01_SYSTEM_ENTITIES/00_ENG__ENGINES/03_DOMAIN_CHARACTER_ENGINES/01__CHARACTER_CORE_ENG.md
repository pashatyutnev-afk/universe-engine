# 🧬 CHARACTER CORE ENGINE
## Canonical Engine Specification  
**LEVEL: L2 · DOMAIN ENGINE · CHARACTER IDENTITY · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 01__CHARACTER_CORE_ENG.md
- ENGINE_ID: L2-DOM-CHARACTER-CORE-ENGINE-001
- UID: UE.ENT.ENG.DOM.CHARACTER.CHARACTER_CORE
- NAME: Character Core Engine
- CLASS: Domain Engine
- DOMAIN: Character
- CATEGORY: Identity, Invariants, Role & Baseline
- LEVEL: L2
- STATUS: FINAL
- FAILURE_MODE: fail-closed (for character validity)
- EDITABLE: true
- BYPASS_ALLOWED: false (within character pipeline)

### ABSOLUTE RULE
> If a character has no invariants, they cannot remain the same person across time.

---

## 1. PURPOSE

Character Core Engine produces the **Character Core Profile** — the stable foundation for a character.

It guarantees:
- identity anchors (who this is)
- invariants (what does not change easily)
- role definition (function in story/world)
- baseline traits (default state before evolution)
- constraints hooks for motivation/values/psychology/behavior engines

This engine defines the *person model*, not the plot.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define identity anchors (name/uid/age range/background)
- Define invariants (core fears, core needs, core boundaries)
- Define role and archetype (optional)
- Define baseline traits (strengths, weaknesses)
- Define baseline state (before story begins)
- Define constraint envelope (what the character cannot do plausibly)
- Detect “empty character” (no anchors) and repair suggestions

### OUT-OF-SCOPE (FORBIDDEN)
- Choosing motivations in detail (Motivation & Desire Engine)
- Defining moral system (Moral & Value Engine)
- Deep psyche dynamics (Psychology Engine)
- Behavioral simulation rules (Behavior Engine)
- Dialogue writing (Dialogue Engine)
- Canon authority (Governance)

---

## 3. CHARACTER CORE MODEL

### 3.1 Core Objects

- IDENTITY_ANCHORS: stable identifiers and origin facts
- INVARIANTS: traits/beliefs/fears that resist change
- BOUNDARIES: hard limits (won’t/ can’t)
- ROLE: narrative/social function
- BASELINE_STATE: default emotional/physical/social state
- CAPABILITIES: skills/resources
- VULNERABILITIES: weaknesses/needs

### 3.2 Invariant Strength (fixed)
- HARD (rarely changes; only via major trauma/evolution)
- MEDIUM (can change over long arc)
- SOFT (can shift in a few scenes)

---

## 4. INPUT ARTIFACTS

### 4.1 INPUT — CHARACTER_CORE_REQUEST
**REQUIRED FIELDS**
- `char_id`
- `timestamp`
- `display_name`
- `story_role` (protagonist/antagonist/etc.)
- `world_constraints_refs`
- `initial_context` (one paragraph)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 5. OUTPUT ARTIFACTS

### 5.1 OUTPUT — CHARACTER_CORE_PROFILE
**REQUIRED FIELDS**
- `char_id`
- `display_name`
- `role`
- `identity_anchors`
- `invariants` (list with strength HARD/MEDIUM/SOFT)
- `boundaries` (list)
- `baseline_state`
- `capabilities`
- `vulnerabilities`
- `constraint_envelope`
- `open_questions` (what is intentionally unknown)
- `trace_id` (if provided)

### 5.2 OUTPUT — CHARACTER_CORE_VERDICT
- `char_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 6. CORE OPERATIONS

- OP_01: DEFINE_IDENTITY_ANCHORS
- OP_02: DEFINE_INVARIANTS_AND_BOUNDARIES
- OP_03: DEFINE_BASELINE_STATE
- OP_04: DEFINE_CAPABILITIES_AND_VULNERABILITIES
- OP_05: BUILD_CONSTRAINT_ENVELOPE
- OP_06: EMIT_CHARACTER_CORE_PROFILE

---

## 7. ACCESS MODEL

### WRITE
- Domain pipeline outputs only

### READ
- Motivation & Desire Engine (drives must respect invariants)
- Moral & Value Engine (values anchored by identity)
- Psychology Engine (internal dynamics anchored)
- Behavior Engine (outputs constrained)
- Relationship Engine (attachment style inputs)
- Continuity Engine (track identity stability)

### DELETE
- Allowed for drafts; finalization per project governance

---

## 8. DEPENDENCIES

### REQUIRED
- World constraints (culture, laws, tech level)
- Optional: Narrative constraints (arc stakes)

### FORBIDDEN
- Treating character core as canon authority
- Retroactive changes to identity anchors without explicit evolution/retcon flag

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- No invariants
- No boundaries
- No baseline_state
- Identity anchors contradict world constraints without bridge
- Character can do anything (constraint_envelope empty)

Reaction:
- Verdict INVALID (CRITICAL)
- Provide repairs: add invariants/boundaries, define constraints, clarify role.

---

## 10. TRACE RULES

- trace_id optional unless orchestrator requires traced pipeline
- if present, propagate to downstream character artifacts

---

## 11. NON-GOALS
- Does not write dialogue
- Does not set morals
- Does not simulate behavior
- Does not grant canon authority

---

## 12. FINAL STATEMENT

Identity is the anchor.
Invariants are the glue that keeps a character the same person.

---

**STATUS:** Character Core Engine v1.0  
**DOMAIN:** ACTIVE
