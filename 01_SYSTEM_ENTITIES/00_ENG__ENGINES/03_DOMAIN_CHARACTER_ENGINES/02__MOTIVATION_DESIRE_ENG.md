# 🔥 MOTIVATION & DESIRE ENGINE
## Canonical Engine Specification  
**LEVEL: L2 · DOMAIN ENGINE · DRIVE SYSTEM · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 02__MOTIVATION_DESIRE_ENG.md
- ENGINE_ID: L2-DOM-MOTIVATION-DESIRE-ENGINE-002
- UID: UE.ENT.ENG.DOM.CHARACTER.MOTIVATION_DESIRE
- NAME: Motivation & Desire Engine
- CLASS: Domain Engine
- DOMAIN: Character
- CATEGORY: Drives, Wants/Needs, Goals & Priority Conflicts
- LEVEL: L2
- STATUS: FINAL
- FAILURE_MODE: fail-closed (for motivation validity)
- EDITABLE: true
- BYPASS_ALLOWED: false (within character pipeline)

### ABSOLUTE RULE
> If a character has no drive, their actions have no reason to exist.

---

## 1. PURPOSE

Motivation & Desire Engine produces a **Motivation Map** for a character.

It guarantees:
- explicit wants (conscious desires)
- explicit needs (often unconscious necessities)
- goal hierarchy (short/mid/long-term)
- internal conflicts (competing drives)
- decision priority rules for downstream behavior/dialogue engines

This engine explains *why* a character moves.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Derive wants/needs from Character Core invariants and context
- Build goal hierarchy (immediate → long-term)
- Define drive types and strengths
- Define “want vs need” tension
- Define internal conflicts between motives
- Provide motivation-based action tendencies (non-binding)
- Detect “motivational void” and repair suggestions

### OUT-OF-SCOPE (FORBIDDEN)
- Moral judgement (Moral & Value Engine)
- Deep psyche mechanisms (Psychology Engine)
- Observable behavior rules (Behavior Engine)
- Writing dialogue (Dialogue Engine)
- Canon authority decisions (Governance)

---

## 3. MOTIVATION MODEL

### 3.1 Core Objects
- WANT: conscious desire the character can articulate
- NEED: essential requirement (may be denied/unseen)
- GOAL: concrete objective derived from wants/needs
- DRIVE: underlying force (status, safety, love, freedom, power, meaning)
- CONFLICT: collision between drives/goals
- BLOCKER: what prevents goal achievement
- PAYOFF: what “success” gives emotionally/practically

### 3.2 Drive Types (fixed set)
- SAFETY
- CONTROL
- POWER
- FREEDOM
- LOVE/BELONGING
- STATUS/RESPECT
- JUSTICE
- REVENGE
- CURIOSITY/TRUTH
- MEANING/FAITH

### 3.3 Strength Scales
- drive_strength: 0..10
- goal_priority: 1..5 (1 = highest)
- conflict_intensity: LOW | MEDIUM | HIGH

---

## 4. INPUT ARTIFACTS

### 4.1 INPUT — MOTIVATION_REQUEST
**REQUIRED FIELDS**
- `mot_id`
- `timestamp`
- `char_core_profile_ref`
- `current_context` (one paragraph)
- `story_role` (optional if in core profile)
- `constraints_refs` (world/relationships if relevant)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 5. OUTPUT ARTIFACTS

### 5.1 OUTPUT — MOTIVATION_MAP
**REQUIRED FIELDS**
- `mot_id`
- `char_id`
- `wants` (list)
- `needs` (list)
- `drives` (list: {type, strength_0_10, evidence})
- `goals` (list: {goal_id, horizon, priority_1_5, linked_want_need, blockers, payoff})
- `want_vs_need_tension` (description + active situations)
- `internal_conflicts` (list: {conflict_id, between, intensity, typical_trigger})
- `decision_priority_rules` (ordered rules)
- `failure_triggers` (what makes character act irrationally)
- `trace_id` (if provided)

### 5.2 OUTPUT — MOTIVATION_VERDICT
- `mot_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 6. CORE OPERATIONS

- OP_01: EXTRACT_WANTS_AND_NEEDS
- OP_02: CLASSIFY_DRIVES_AND_STRENGTHS
- OP_03: BUILD_GOAL_HIERARCHY
- OP_04: DETECT_INTERNAL_CONFLICTS
- OP_05: DERIVE_DECISION_PRIORITY_RULES
- OP_06: EMIT_MOTIVATION_MAP

---

## 7. ACCESS MODEL

### WRITE
- Domain pipeline outputs only

### READ
- Moral & Value Engine (values filter motives)
- Psychology Engine (motives interact with psyche)
- Behavior Engine (motives drive actions)
- Dialogue Engine (speech intent derives from motives)
- Relationship Engine (attachment affects wants/needs)
- Character Evolution Engine (motives shift over time)

### DELETE
- Allowed for drafts; finalization per project governance

---

## 8. DEPENDENCIES

### REQUIRED
- Character Core Engine output (core profile)
- World constraints (what goals are plausible)

### FORBIDDEN
- Motivations that contradict HARD invariants without explicit evolution/trauma bridge
- Treating motive map as canon authority

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- No wants AND no needs (empty drive system)
- Drives exist but no goals (no actionable direction)
- Goals have no blockers (too easy / no story friction)
- Decision rules contradict each other with no priority order
- Wants/needs violate core boundaries without bridge

Reaction:
- Verdict INVALID (CRITICAL)
- Provide repairs: add wants/needs, add blockers, define hierarchy.

---

## 10. TRACE RULES

- trace_id optional unless orchestrator requires traced pipeline
- if present, propagate into downstream character artifacts

---

## 11. NON-GOALS
- Does not judge morality
- Does not write dialogue
- Does not simulate behavior fully
- Does not grant canon authority

---

## 12. FINAL STATEMENT

Motivation is motion.
Wants give direction; needs create depth.

---

**STATUS:** Motivation & Desire Engine v1.0  
**DOMAIN:** ACTIVE
