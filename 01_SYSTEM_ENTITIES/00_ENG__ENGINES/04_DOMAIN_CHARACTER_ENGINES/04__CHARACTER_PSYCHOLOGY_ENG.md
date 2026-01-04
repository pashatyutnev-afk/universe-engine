# 🧠 CHARACTER PSYCHOLOGY ENGINE
## Canonical Engine Specification  
**LEVEL: L2 · DOMAIN ENGINE · INTERNAL DYNAMICS · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 04__CHARACTER_PSYCHOLOGY_ENG.md
- ENGINE_ID: L2-DOM-CHARACTER-PSYCHOLOGY-ENGINE-004
- UID: UE.ENT.ENG.DOM.CHARACTER.CHARACTER_PSYCHOLOGY
- NAME: Character Psychology Engine
- CLASS: Domain Engine
- DOMAIN: Character
- CATEGORY: Internal Parts, Triggers, Defenses & Emotion Regulation
- LEVEL: L2
- STATUS: FINAL
- FAILURE_MODE: fail-closed (for psyche coherence)
- EDITABLE: true
- BYPASS_ALLOWED: false (within character pipeline)

### ABSOLUTE RULE
> If internal dynamics are undefined, behavior becomes random and unearned.

---

## 1. PURPOSE

Character Psychology Engine produces a **Psyche Model** describing internal mechanisms.

It guarantees:
- internal “parts” or modes (protectors, vulnerable core, etc.)
- trigger map (what activates reactions)
- defense strategies (avoidance, control, aggression, humor, etc.)
- coping behaviors (adaptive/maladaptive)
- emotion regulation profile (how fast they escalate/calm)
- linkages to motives and values (why a defense is chosen)

It does not diagnose real humans.
It provides narrative-grade psychology for consistent character simulation.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define internal modes/parts and their roles
- Define trigger categories and intensity
- Define defense and coping patterns
- Define stress response profile (fight/flight/freeze/fawn)
- Define shame/guilt sensitivity and pride/anger thresholds
- Map how motives/values interact with defenses
- Detect contradictions: “calm always” vs “rage instantly” without conditions
- Provide repair suggestions (non-binding)

### OUT-OF-SCOPE (FORBIDDEN)
- Moral judgement (Moral & Value Engine)
- Motivation hierarchy (Motivation Engine)
- Observable behavior rules (Behavior Engine)
- Dialogue writing (Dialogue Engine)
- Canon authority decisions (Governance)

---

## 3. PSYCHE MODEL

### 3.1 Internal Modes (recommended set)
- CORE_SELF (vulnerable truth, needs)
- PROTECTOR (prevents pain; control/anger/avoidance)
- ACHIEVER (performance, competence armor)
- CARETAKER (pleasing, fawning, loyalty)
- SHADOW (repressed impulses, taboo desires)
- RATIONALIZER (logic mask)
- CHILD_MODE (regression under stress)

Modes are optional but must cover at least:
- one vulnerable core
- one protection strategy

### 3.2 Stress Responses (fixed)
- FIGHT
- FLIGHT
- FREEZE
- FAWN

### 3.3 Trigger Types (fixed)
- ABANDONMENT
- HUMILIATION
- LOSS_OF_CONTROL
- BETRAYAL
- FAILURE
- THREAT_TO_IDENTITY
- THREAT_TO_LOVED_ONES
- MORAL_INJURY

### 3.4 Regulation Parameters
- arousal_baseline: 0..10
- escalation_speed: SLOW | MEDIUM | FAST
- recovery_speed: SLOW | MEDIUM | FAST
- dissociation_risk: LOW | MEDIUM | HIGH

---

## 4. INPUT ARTIFACTS

### 4.1 INPUT — PSYCHE_REQUEST
**REQUIRED FIELDS**
- `psy_id`
- `timestamp`
- `char_core_profile_ref`
- `motivation_map_ref` (recommended)
- `value_profile_ref` (recommended)
- `history_context` (one paragraph; can be partial/unknown)
- `world_constraints_refs`
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 5. OUTPUT ARTIFACTS

### 5.1 OUTPUT — PSYCHE_MODEL
**REQUIRED FIELDS**
- `psy_id`
- `char_id`
- `modes` (list: {mode_id, name, role, protects, cost})
- `stress_response_profile` (primary + secondary)
- `trigger_map` (list: {trigger_type, intensity_0_10, typical_situation, mode_activated})
- `defenses` (list: {defense, when_used, cost, conflicts_with_values?})
- `coping_patterns` (list: {coping, adaptive?, short_term_gain, long_term_cost})
- `emotion_regulation` (baseline, escalation_speed, recovery_speed, dissociation_risk)
- `shame_guilt_profile` (guilt_threshold, shame_sensitivity, repair_style)
- `anger_profile` (anger_threshold, expression_style, cooldown_style)
- `attachment_tendencies` (avoidant/anxious/secure/mixed; narrative-grade)
- `integration_notes` (links to motives/values/invariants)
- `trace_id` (if provided)

### 5.2 OUTPUT — PSYCHE_VERDICT
- `psy_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 6. CORE OPERATIONS

- OP_01: DEFINE_INTERNAL_MODES
- OP_02: DEFINE_TRIGGER_MAP
- OP_03: DEFINE_DEFENSES_AND_COPING
- OP_04: DEFINE_REGULATION_PARAMETERS
- OP_05: CHECK_INTERNAL_CONSISTENCY
- OP_06: EMIT_PSYCHE_MODEL

---

## 7. ACCESS MODEL

### WRITE
- Domain pipeline outputs only

### READ
- Behavior Engine (observable output under stress)
- Dialogue Engine (speech shifts by mode)
- Relationship Engine (attachment + triggers affect bonds)
- Growth & Trauma Engine (trauma locks/unlocks modes)
- Character Evolution Engine (integration over time)

### DELETE
- Allowed for drafts; finalization per project governance

---

## 8. DEPENDENCIES

### REQUIRED
- Character Core Profile
- Motivation Map and Value Profile (recommended for coherence)

### FORBIDDEN
- Treating psyche model as medical diagnosis
- Overriding core invariants without evolution/trauma bridge

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- No vulnerable core AND no protector mode (no internal dynamics)
- Trigger map empty (no reactivity rules)
- Defenses listed but no costs (invincible psyche)
- Regulation parameters missing (no stability model)
- Contradictions between motives/values and defenses without explanation

Reaction:
- Verdict INVALID (CRITICAL)
- Provide repairs: add modes, add triggers, add costs, clarify regulation.

---

## 10. TRACE RULES

- trace_id optional unless orchestrator requires traced pipeline
- if present, propagate into downstream character artifacts

---

## 11. NON-GOALS
- Does not diagnose real humans
- Does not write dialogue
- Does not simulate full behavior alone
- Does not grant canon authority

---

## 12. FINAL STATEMENT

Psychology is the invisible machine behind choices.
Define it, and the character becomes inevitable.

---

**STATUS:** Character Psychology Engine v1.0  
**DOMAIN:** ACTIVE
