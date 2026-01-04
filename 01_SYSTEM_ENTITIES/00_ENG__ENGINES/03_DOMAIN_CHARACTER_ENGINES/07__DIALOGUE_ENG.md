# 🗣️ DIALOGUE ENGINE
## Canonical Engine Specification  
**LEVEL: L2 · DOMAIN ENGINE · SPEECH INTENT · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 07__DIALOGUE_ENG.md
- ENGINE_ID: L2-DOM-DIALOGUE-ENGINE-007
- UID: UE.ENT.ENG.DOM.CHARACTER.DIALOGUE
- NAME: Dialogue Engine
- CLASS: Domain Engine
- DOMAIN: Character
- CATEGORY: Dialogue Intent, Subtext, Power Moves & Conversational Beats
- LEVEL: L2
- STATUS: FINAL
- FAILURE_MODE: fail-closed (for dialogue coherence)
- EDITABLE: true
- BYPASS_ALLOWED: false (within character pipeline)

### ABSOLUTE RULE
> Dialogue is action: if it does not change power, knowledge, or emotion, it is filler.

---

## 1. PURPOSE

Dialogue Engine produces a **Dialogue Intent Spec** (not final lines).

It guarantees:
- conversational objectives for each participant
- subtext (what is meant vs what is said)
- power dynamics and tactics per exchange
- knowledge transfer and concealment mapping
- dialogue beat structure aligned to scene goals and relationship state

This engine creates the *plan* for dialogue; wording is handled later (Speech Naturalization).

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define dialogue goals per character in a scene
- Define conversational tactics (pressure, charm, threat, evade)
- Define subtext layers and what is masked
- Define turn-by-turn beat plan (exchange beats)
- Ensure alignment with motives/values/relationship constraints
- Ensure knowledge continuity (no leaks)
- Detect filler dialogue and repair suggestions
- Produce constraints for “how it must sound” (not the actual phrasing)

### OUT-OF-SCOPE (FORBIDDEN)
- Writing final dialogue lines (Speech Naturalization Engine)
- Full scene assembly (Scene Construction Engine)
- Reveal scheduling (Twist & Reveal Engine) beyond applying constraints
- Canon authority decisions (Governance)

---

## 3. DIALOGUE MODEL

### 3.1 Dialogue Beats (fixed set)
- OPEN (enter conversation)
- PROBE (ask/test)
- DEFLECT (avoid)
- PRESSURE (increase stakes)
- REVEAL (share info)
- LIE/MISDIRECT (conceal/redirect)
- CONCESSION (give ground)
- THREAT (explicit/implicit)
- DEAL (propose exchange)
- EMOTIONAL_SHIFT (vulnerability/anger)
- DECISION (commit)
- EXIT (close)

### 3.2 Tactics (fixed set)
- CHARM
- INTIMIDATE
- BARGAIN
- GUILT
- FLATTERY
- LOGIC_TRAP
- HUMOR_MASK
- SILENCE
- AUTHORITY
- VULNERABILITY

### 3.3 Power and Knowledge
- power_delta per beat: -2..+2
- knowledge_delta per beat: NONE | HINT | PARTIAL | FULL
- trust_delta per beat: -2..+2 (relationship ladder impact)

---

## 4. INPUT ARTIFACTS

### 4.1 INPUT — DIALOGUE_REQUEST
**REQUIRED FIELDS**
- `dlg_id`
- `timestamp`
- `scene_spec_ref`
- `relationship_map_ref` (required)
- `motivation_maps_refs` (recommended)
- `value_profiles_refs` (recommended)
- `psyche_models_refs` (recommended)
- `reveal_schedule_ref` (optional but recommended if secrets exist)
- `continuity_registry_ref` (optional)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 5. OUTPUT ARTIFACTS

### 5.1 OUTPUT — DIALOGUE_INTENT_SPEC
**REQUIRED FIELDS**
- `dlg_id`
- `scene_id`
- `participants`
- `objectives` (map character → goal)
- `subtext_map` (map character → hidden agenda)
- `constraints` (what must not be said; what must be achieved)
- `beat_plan` (ordered list of beats)
Each beat includes:
- `beat_id`
- `speaker`
- `beat_type`
- `tactic`
- `surface_intent` (what they appear to do)
- `true_intent` (subtext)
- `power_delta`
- `knowledge_delta`
- `trust_delta`
- `expected_response` (what it pressures the other to do)
- `resulting_state_delta` (what changes after beat)
- `risk` (what could go wrong)

- `dialogue_outcomes` (what must change by end)
- `leak_checks` (knowledge continuity checks)
- `trace_id` (if provided)

### 5.2 OUTPUT — DIALOGUE_VERDICT
- `dlg_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 6. CORE OPERATIONS

- OP_01: READ_SCENE_AND_RELATIONSHIP_STATE
- OP_02: DEFINE_OBJECTIVES_AND_SUBTEXT
- OP_03: BUILD_BEAT_PLAN
- OP_04: APPLY_REVEAL_AND_CONTINUITY_CONSTRAINTS
- OP_05: CHECK_FILER_AND_STATE_CHANGE
- OP_06: EMIT_DIALOGUE_INTENT_SPEC

---

## 7. ACCESS MODEL

### WRITE
- Domain pipeline outputs only

### READ
- Speech Naturalization Engine (turns intent spec into natural lines)
- Scene Construction Engine (dialogue beats integrated as scene beats)
- Continuity Engine (knowledge-state updates)
- Relationship Engine (trust/power deltas recorded)

### DELETE
- Allowed for drafts; finalization per project governance

---

## 8. DEPENDENCIES

### REQUIRED
- Scene Spec (scene goal + participants)
- Relationship Map (trust/power context)

### FORBIDDEN
- Final dialogue wording generation inside this engine
- Knowledge leaks that violate reveal schedule
- Dialogue that contradicts value taboos without explicit cost/tradeoff

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- No dialogue outcomes (end state unchanged)
- Beat plan missing power/knowledge/emotion shifts in a high-stakes scene
- Knowledge leak (character reveals info they shouldn’t have)
- Participants have no objectives (talking for nothing)
- Dialogue contradicts relationship ladders with no bridge

Reaction:
- Verdict INVALID (CRITICAL)
- Provide repairs: define objectives, add pressure beats, insert outcome deltas.

---

## 10. TRACE RULES

- trace_id optional unless orchestrator requires traced pipeline
- if present, propagate into naturalization constraints

---

## 11. NON-GOALS
- Does not write final lines
- Does not set global reveals
- Does not grant canon authority

---

## 12. FINAL STATEMENT

Dialogue is a battlefield of meaning.
Plan the intent and tactics — and the words will follow.

---

**STATUS:** Dialogue Engine v1.0  
**DOMAIN:** ACTIVE
