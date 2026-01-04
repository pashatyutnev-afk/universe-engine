# 💓 EMOTIONAL RESONANCE ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · STYLE ENGINE · CATHARSIS DESIGN · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 03__EMOTIONAL_RESONANCE_ENG.md
- ENGINE_ID: L3-STYLE-EMOTIONAL-RESONANCE-ENGINE-003
- UID: UE.ENT.ENG.STYLE.EMOTIONAL_RESONANCE
- NAME: Emotional Resonance Engine
- CLASS: Style Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (emotional payoff integrity)
- EDITABLE: true

### ABSOLUTE RULE
> Emotion must be earned by causality. Unpaid emotion is manipulation and breaks trust.

---

## 1. PURPOSE

Emotional Resonance Engine designs **what the audience should feel** and **why**:
- emotional targets per arc/sequence
- resonance anchors (characters, symbols, memories, motifs)
- catharsis placement and pricing
- fatigue control (avoid constant peaks)
- emotional payoff mapping aligned to climax/resolution

It produces:
- **EMOTIONAL_RESONANCE_MAP**
- catharsis plan
- resonance anchor registry
- emotional integrity checks

This engine prevents “random tears” and “constant intensity burnout”.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define emotional target schemas and controlled vocabulary
- Build resonance map aligned with tone/mood and story mechanics
- Define catharsis points (release moments) and prerequisites
- Define emotional anchors and recurrence rules
- Validate emotion is causally earned (events/conflicts support it)
- Define fatigue control windows (recovery / silence / numbness)
- Emit resonance constraints for scene/dialogue production

### OUT-OF-SCOPE (FORBIDDEN)
- Plot decisions (events/conflicts)
- Canon authority decisions
- Writing full prose (only maps and constraints)

---

## 3. RESONANCE MODEL

### 3.1 Resonance Map — EMOTIONAL_RESONANCE_MAP (required fields)
- `er_id`
- `scope` = ARC | SEQUENCE | PROJECT
- `primary_emotional_thesis` (one sentence)
- `targets_by_window` (ordered windows with emotion targets)
- `resonance_anchors` (registry)
- `catharsis_points` (list)
- `fatigue_control_rules` (hard rules)
- `payoff_alignment` (map: setup → emotional payoff)
- `integrity_report` (issues + fixes)
- `trace_id` (optional)

Missing any required field → REJECT.

### 3.2 Window Target (required fields)
- `window_id`
- `time_ref` (symbolic ok)
- `target_emotions` (1–3)
- `intensity_scale` (0–10)
- `earned_by` (refs: event_ids / conflict_ids / turning_point_ids)
- `allowed_expression_modes` (list)
- `forbidden_expression_modes` (list)
- `notes`

Missing any required field → REJECT.

### 3.3 Resonance Anchor (required fields)
- `anchor_id`
- `type` = CHARACTER | RELATIONSHIP | PLACE | OBJECT | SOUND | SYMBOL | MEMORY | IDEA
- `meaning` (what it evokes)
- `activation_triggers` (when it appears)
- `recurrence_rule` (how often + constraints)
- `decay_rule` (when it should stop to avoid spam)
- `notes`

Missing any required field → REJECT.

### 3.4 Catharsis Point (required fields)
- `cp_id`
- `target_release` (what gets released)
- `prerequisites` (what must be paid/earned before)
- `release_mode` = QUIET | EXPLOSIVE | BITTERSWEET | TRAGIC | TRIUMPHANT
- `post_release_state` (what changes)
- `notes`

Missing any required field → REJECT.

---

## 4. CONTROLLED VOCABULARY (STANDARD)

Standard emotion tags:
- AWE
- WONDER
- DREAD
- SUSPENSE
- GRIEF
- TENDERNESS
- HOPE
- DESPAIR
- ANGER
- SHAME
- PRIDE
- RELIEF
- TRIUMPH
- MELANCHOLY
- UNEASE
- LOVE
- LONELINESS

Standard expression modes:
- SILENCE
- SUBTEXT
- DIALOGUE
- ACTION
- SYMBOLIC_MIRROR
- MUSIC_PUSH
- VISUAL_COMPOSITION_PUSH
- INTERNAL_MONOLOGUE (if allowed)

---

## 5. HARD RULES (EARNED EMOTION)

- Every target emotion must reference `earned_by` causes:
  - event/conflict/turning point support is mandatory.
- Catharsis must have prerequisites:
  - release cannot happen “for free”.
- Fatigue control:
  - after intensity ≥ 8, next window must drop by at least 2 points unless horror mode forbids relief.
- Anchor recurrence is bounded:
  - every anchor must have decay_rule.

---

## 6. INPUT ARTIFACTS

### 6.1 INPUT — EMOTIONAL_RESONANCE_REQUEST
**REQUIRED FIELDS**
- `er_req_id`
- `timestamp`
- `tone_profile_ref` (required)
- `mood_curve_ref` (required)
- `event_spec_library_ref` (recommended)
- `conflict_model_ref` (recommended)
- `turning_point_map_ref` (recommended)
- `climax_blueprint_ref` (recommended)
- `resolution_plan_ref` (optional)
- `constraints_refs` (required)
- `character_package_ref` (recommended)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 7. OUTPUT ARTIFACTS

### 7.1 OUTPUT — EMOTIONAL_RESONANCE_MAP
(see model above)

### 7.2 OUTPUT — EMOTIONAL_RESONANCE_VERDICT
- `er_req_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 8. CORE OPERATIONS

- OP_01: INGEST_TONE_MOOD_AND_STORY_ARTIFACTS
- OP_02: DEFINE_PRIMARY_EMOTIONAL_THESIS
- OP_03: BUILD_TARGETS_BY_WINDOW (1–3 emotions each)
- OP_04: REGISTER_RESONANCE_ANCHORS (bounded recurrence)
- OP_05: DESIGN_CATHARSIS_POINTS (with prerequisites)
- OP_06: APPLY_FATIGUE_CONTROL_RULES
- OP_07: BUILD_PAYOFF_ALIGNMENT (setup → emotional payoff)
- OP_08: RUN_EARNED_EMOTION_CHECKS
- OP_09: EMIT_EMOTIONAL_RESONANCE_MAP

---

## 9. DRIFT / MANIPULATION DETECTION

Hard violations (INVALID):
- high intensity with no causal support in `earned_by`
- catharsis without prerequisites
- repeated music_push as primary mode when prohibited by constraints

Soft violations (PARTIAL):
- anchor appears too often (violates recurrence rule)
- intensity curve too flat (monotone)

Repair suggestions:
- add bridge events
- move catharsis to earned window
- reduce anchor frequency
- change expression mode to subtext/action

---

## 10. DEPENDENCIES

### REQUIRED
- Tone Profile
- Mood Curve
- Constraints refs

### OPTIONAL
- Story artifacts (events/conflicts/turning points/climax)
- Character package (for authenticity)

### FORBIDDEN
- Emotion targets not tied to causes
- Constant high intensity without recovery windows
- Anchor spam without decay

---

## 11. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- No emotional thesis
- Targets missing earned_by refs
- Catharsis points missing prerequisites
- Fatigue control rules missing
- Payoff alignment shows major gaps (promised emotional payoff not delivered)

Reaction:
- Verdict INVALID (CRITICAL)
- Emit repair plan:
  - bind targets to causes
  - rebuild intensity curve
  - redesign catharsis with prerequisites
  - define anchor recurrence/decay

---

## 12. TRACE RULES

- trace_id optional unless pipeline requires traced execution
- if present, propagate into symbolism/metaphor/sensory planning

---

## 13. NON-GOALS
- Does not generate plot
- Does not write dialogue
- Does not set canon

---

## 14. FINAL STATEMENT

Emotion is causality felt.
Earn it — and the audience will carry it.

---

**STATUS:** Emotional Resonance Engine v1.0  
**REALM:** ACTIVE
