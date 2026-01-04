# ⏱️ PACING & RHYTHM ENGINE
## Canonical Engine Specification  
**LEVEL: L2 · DOMAIN ENGINE · TIMING CONTROL · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 05__PACING_RHYTHM_ENG.md
- ENGINE_ID: L2-DOM-PACING-RHYTHM-ENGINE-005
- UID: UE.ENT.ENG.DOM.NARRATIVE.PACING_RHYTHM
- NAME: Pacing & Rhythm Engine
- CLASS: Domain Engine
- DOMAIN: Narrative
- CATEGORY: Timing, Density, Breath & Flow
- LEVEL: L2
- STATUS: FINAL
- FAILURE_MODE: fail-closed (for pacing validity)
- EDITABLE: true
- BYPASS_ALLOWED: false (within narrative pipeline)

### ABSOLUTE RULE
> If pacing is uncontrolled, the story loses attention: either it drags or it overwhelms.

---

## 1. PURPOSE

Pacing & Rhythm Engine controls **time feel** of the narrative plan.

It guarantees:
- explicit timing budgets per act/sequence/scene
- rhythm patterning (push / release / breath)
- density control (events per minute / per page / per scene)
- compatibility with structure and dramatic arc constraints

It does not change what happens — it changes **how fast and with what spacing** it happens.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Assign timing budgets to structure segments and scenes
- Detect pacing issues: drag, rush, monotony, uneven density
- Produce rhythm patterns: FAST / MEDIUM / SLOW segments
- Insert “breath” beats where needed (non-binding suggestions)
- Enforce format constraints (shorts, mini-episode, episode, book chapter)
- Output pacing constraints for scene construction and tension engines

### OUT-OF-SCOPE (FORBIDDEN)
- Changing causal logic (Narrative Logic Engine)
- Choosing turning points (Dramatic Arc Engine)
- Designing tension content (Tension & Stakes Engine)
- Reveal strategy (Twist & Reveal Engine)
- Canon authority decisions (Governance)

---

## 3. PACING MODEL

### 3.1 Timing Units
- TIME_BUDGET: seconds/minutes/pages (depends on format_target)
- SEGMENT_DURATION: allocated duration per segment
- BEAT_RATE: beats per segment duration
- EVENT_DENSITY: meaningful events per unit time

### 3.2 Rhythm States (fixed)
- PUSH (accelerate)
- HOLD (sustain)
- RELEASE (relief)
- BREATH (quiet processing)

### 3.3 Pacing Profiles (examples)
- SHORT (6–22s): high density, minimal breath, single arc spike
- MINI (1–3m): density waves, one main peak, controlled breath
- EPISODE (20–60m): multiple waves, mid-peak + climax
- BOOK_CHAPTER: larger breath windows, deeper holds, slower ramps

---

## 4. INPUT ARTIFACTS

### 4.1 INPUT — PACING_REQUEST
**REQUIRED FIELDS**
- `pacing_id`
- `timestamp`
- `format_target`
- `structure_plan_ref`
- `scene_specs_refs` (optional but recommended)
- `arc_plan_ref` (recommended)
- `target_length` (time/pages)
- `style_constraints` (optional: fast/slow preference)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 5. OUTPUT ARTIFACTS

### 5.1 OUTPUT — PACING_PLAN
- `pacing_id`
- `format_target`
- `target_length`
- `segment_budgets` (list: {segment_id, duration, rhythm_state})
- `density_map` (list: {segment_id, beat_rate, event_density})
- `rhythm_waves` (high-level wave description)
- `constraints_for_scenes` (rules to apply per scene)
- `repair_suggestions` (non-binding)
- `trace_id` (if provided)

### 5.2 OUTPUT — PACING_VERDICT
- `pacing_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 6. CORE OPERATIONS

- OP_01: MAP_TARGET_LENGTH_TO_STRUCTURE
- OP_02: ALLOCATE_SEGMENT_BUDGETS
- OP_03: COMPUTE_DENSITY_MAP
- OP_04: DETECT_DRAG_RUSH_MONOTONY
- OP_05: DESIGN_RHYTHM_WAVES
- OP_06: EMIT_PACING_PLAN

---

## 7. ACCESS MODEL

### WRITE
- Domain pipeline outputs only

### READ
- Scene Construction Engine (scene timing + beat count)
- Tension & Stakes Engine (pressure distribution)
- Continuity Engine (avoid cutting required threads accidentally)
- Production Format engines (if used for runtime constraints)

### DELETE
- Allowed for drafts; finalization per project governance

---

## 8. DEPENDENCIES

### REQUIRED
- Story Structure Engine (structure plan)
- Dramatic Arc Engine (peak placement constraints)
- Optional: Scene Construction Engine (scene beat lists)

### FORBIDDEN
- Treating pacing plan as canon authority
- Overriding governance locks

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED FOR PACING)

CRITICAL:
- Total allocated duration deviates >10% from target_length without justification
- Long monotony: >3 consecutive segments with same rhythm_state + same density
- No RELEASE/BREATH segments in long formats (episode/book)
- Peak intensity segments allocated too little time (climax starved)
- Excessive density: beat_rate above format maximum

Reaction:
- Verdict INVALID (CRITICAL)
- Provide repairs: reallocate budgets, insert breath, reshape waves.

---

## 10. TRACE RULES

- trace_id optional unless orchestrator requires traced pipeline
- if present, propagate into downstream constraints

---

## 11. NON-GOALS
- Does not change story events
- Does not decide reveals
- Does not validate truth
- Does not grant canon authority

---

## 12. FINAL STATEMENT

Pacing is attention management.
Without rhythm control, structure and arc cannot land.

---

**STATUS:** Pacing & Rhythm Engine v1.0  
**DOMAIN:** ACTIVE
