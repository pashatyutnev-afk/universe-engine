# ⚖️ MORAL & VALUE ENGINE
## Canonical Engine Specification  
**LEVEL: L2 · DOMAIN ENGINE · VALUE SYSTEM · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 03__MORAL_VALUE_ENG.md
- ENGINE_ID: L2-DOM-MORAL-VALUE-ENGINE-003
- UID: UE.ENT.ENG.DOM.CHARACTER.MORAL_VALUE
- NAME: Moral & Value Engine
- CLASS: Domain Engine
- DOMAIN: Character
- CATEGORY: Values, Ethics, Taboo Lines & Moral Decision Filters
- LEVEL: L2
- STATUS: FINAL
- FAILURE_MODE: fail-closed (for value coherence)
- EDITABLE: true
- BYPASS_ALLOWED: false (within character pipeline)

### ABSOLUTE RULE
> If a character has no values or boundaries, their choices have no moral identity.

---

## 1. PURPOSE

Moral & Value Engine produces a **Value Profile** that defines how a character evaluates choices.

It guarantees:
- explicit value hierarchy (what matters most)
- moral boundaries (lines they won’t cross)
- taboos and exceptions (what breaks under pressure)
- ethical style (duty vs outcome, loyalty vs justice, etc.)
- decision filter rules for behavior/dialogue engines

This engine does not judge “correctness”.
It defines the character’s moral operating system.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Derive values from Character Core + culture/world constraints
- Build value hierarchy and protected principles
- Define taboo lines and “break conditions”
- Define moral dilemmas typical to this character
- Validate consistency: values must match behavior tendencies
- Provide repairs: clarify priorities, add exceptions, resolve contradictions

### OUT-OF-SCOPE (FORBIDDEN)
- Motivation design (Motivation Engine)
- Psyche mechanisms (Psychology Engine)
- Full behavior simulation (Behavior Engine)
- Dialogue writing (Dialogue Engine)
- Canon authority decisions (Governance)

---

## 3. VALUE MODEL

### 3.1 Core Objects
- VALUE: principle that guides choices
- PRIORITY: ranking weight
- TABOO_LINE: action the character refuses
- EXCEPTION_RULE: condition under which taboo may break
- ETHICAL_STYLE: the “decision philosophy”
- DILEMMA_TEMPLATE: recurring moral conflict

### 3.2 Ethical Styles (fixed set)
- DEONTOLOGICAL (duty/rules)
- CONSEQUENTIALIST (outcomes)
- VIRTUE_BASED (identity/character)
- LOYALTY_BASED (ingroup priority)
- JUSTICE_BASED (fairness/order)
- SURVIVAL_BASED (existence first)

### 3.3 Scales
- value_priority: 1..5 (1 = highest)
- taboo_strength: HARD | MEDIUM | SOFT
- guilt_threshold: LOW | MEDIUM | HIGH (how fast remorse triggers)

---

## 4. INPUT ARTIFACTS

### 4.1 INPUT — VALUE_REQUEST
**REQUIRED FIELDS**
- `val_id`
- `timestamp`
- `char_core_profile_ref`
- `motivation_map_ref` (recommended)
- `culture_world_constraints_refs`
- `role_context` (one paragraph)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 5. OUTPUT ARTIFACTS

### 5.1 OUTPUT — VALUE_PROFILE
**REQUIRED FIELDS**
- `val_id`
- `char_id`
- `ethical_style` (one or blend with weights)
- `values` (list: {value, priority_1_5, evidence})
- `protected_principles` (subset of values)
- `taboo_lines` (list: {taboo, strength, break_conditions})
- `exceptions` (list: {exception_id, allows, condition, cost})
- `guilt_threshold`
- `moral_dilemmas` (list: {dilemma_id, choice_a, choice_b, what_value_conflicts})
- `decision_filter_rules` (ordered rules applied before action)
- `alignment_notes` (with motives and core invariants)
- `trace_id` (if provided)

### 5.2 OUTPUT — VALUE_VERDICT
- `val_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 6. CORE OPERATIONS

- OP_01: EXTRACT_VALUE_CANDIDATES
- OP_02: ASSIGN_PRIORITY_HIERARCHY
- OP_03: DEFINE_TABOO_LINES_AND_EXCEPTIONS
- OP_04: SELECT_ETHICAL_STYLE
- OP_05: GENERATE_DILEMMA_TEMPLATES
- OP_06: EMIT_VALUE_PROFILE

---

## 7. ACCESS MODEL

### WRITE
- Domain pipeline outputs only

### READ
- Psychology Engine (guilt/shame dynamics)
- Behavior Engine (action filters)
- Relationship Engine (loyalty vs justice rules)
- Dialogue Engine (speech intent aligned to values)
- Character Evolution Engine (value shifts tracked)

### DELETE
- Allowed for drafts; finalization per project governance

---

## 8. DEPENDENCIES

### REQUIRED
- Character Core Profile (identity anchors/invariants)
- Culture/World constraints (value plausibility)

### FORBIDDEN
- Values that contradict HARD invariants without evolution/trauma bridge
- Treating value profile as canon authority

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- No values listed
- No taboo lines (character has no moral boundary)
- Priorities missing or all equal (no hierarchy)
- Taboo contradictions without break conditions
- Ethical style undefined (no decision philosophy)
- Decision rules unordered or mutually exclusive with no precedence

Reaction:
- Verdict INVALID (CRITICAL)
- Provide repairs: define hierarchy, add taboos, clarify exceptions.

---

## 10. TRACE RULES

- trace_id optional unless orchestrator requires traced pipeline
- if present, propagate to downstream character artifacts

---

## 11. NON-GOALS
- Does not judge “right vs wrong”
- Does not write dialogue
- Does not simulate behavior fully
- Does not grant canon authority

---

## 12. FINAL STATEMENT

Values are the character’s compass.
Taboos are the lines that define who they refuse to become.

---

**STATUS:** Moral & Value Engine v1.0  
**DOMAIN:** ACTIVE
