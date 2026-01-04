# 🧩 METAPHOR ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · STYLE ENGINE · SOURCE→TARGET MAPPING · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 05__METAPHOR_ENG.md
- ENGINE_ID: L3-STYLE-METAPHOR-ENGINE-005
- UID: UE.ENT.ENG.STYLE.METAPHOR
- NAME: Metaphor Engine
- CLASS: Style Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (metaphor coherence)
- EDITABLE: true

### ABSOLUTE RULE
> A metaphor must clarify meaning, not replace logic. If it breaks world sense, it is rejected.

---

## 1. PURPOSE

Metaphor Engine defines a **coherent metaphor system**:
- source domain → target domain mappings
- recurrence and pacing rules
- tone compatibility constraints
- forbidden metaphors list (genre/platform/taboo)
- drift detection (metaphor noise and mixed frames)

It produces:
- **METAPHOR_SYSTEM**
- metaphor pacing plan
- coherence and alignment checks

This engine prevents “random poetic lines” that contradict the world.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define metaphor schema and mapping language
- Register metaphor families (frames) and rules of use
- Map metaphors to symbols/emotional anchors (optional)
- Control metaphor density (pacing + fatigue)
- Enforce tone/world alignment constraints
- Detect mixed metaphors and frame collisions
- Emit metaphor constraints for writing/scene engines

### OUT-OF-SCOPE (FORBIDDEN)
- Plot decisions
- Canon authority decisions
- Theme ownership (theme engine owns meaning; metaphor expresses it)
- Full prose generation

---

## 3. METAPHOR SYSTEM MODEL

### 3.1 Output — METAPHOR_SYSTEM (required fields)
- `ms_id`
- `scope` = PROJECT | ARC | SEQUENCE
- `frame_registry` (list of METAPHOR_FRAME)
- `mapping_rules` (global rules)
- `pacing_plan` (density by windows)
- `forbidden_metaphors` (list)
- `coherence_gates` (hard rules)
- `integrity_report` (issues + fixes)
- `trace_id` (optional)

Missing any required field → REJECT.

### 3.2 Metaphor Frame — METAPHOR_FRAME (required fields)
- `frame_id`
- `name`
- `source_domain` (concrete domain: ocean, machine, disease, fire, prison, garden…)
- `target_domain` (abstract: love, power, guilt, time, identity…)
- `core_mapping` (one sentence: source explains target)
- `allowed_expressions` (list: images/verbs/objects)
- `forbidden_expressions` (list)
- `recurrence_rule` (frequency + constraints)
- `decay_or_mutation_rule` (fade/mutate/invert)
- `tone_alignment` = OK | RISK | VIOLATION
- `world_alignment` = OK | RISK | VIOLATION
- `notes`

Missing any required field → REJECT.

### 3.3 Pacing Window (required fields)
- `window_id`
- `time_ref`
- `density` = NONE | SPARSE | MEDIUM | HIGH
- `allowed_frames` (list of frame_id)
- `forbidden_frames` (list)
- `purpose` (clarify / intensify / soften / contrast)
- `notes`

Missing any required field → REJECT.

---

## 4. COHERENCE GATES (HARD)

- Frame limit:
  - max 3 active metaphor frames per ARC unless explicitly declared “mythic overload” genre mode.
- No mixed metaphors in the same beat:
  - conflicting source domains in one unit without intentional contrast rule.
- World alignment:
  - metaphors must not imply impossible mechanics that confuse canon (unless clearly marked as figurative and tone permits).
- Tone alignment:
  - clinical tone forbids lyrical overflow; lyrical tone may allow it.
- Recurrence + decay mandatory:
  - every frame must have recurrence and decay/mutation rule.

---

## 5. CONTROLLED VOCABULARY (STANDARD)

Standard metaphor purposes:
- CLARIFY
- INTENSIFY
- SOFTEN
- IRONIZE
- FORESHADOW
- MIRROR_SYMBOL
- CONTRAST_REALITY

Standard density rules:
- HIGH density only near turning points/climax windows unless style explicitly aims for poetic saturation.

---

## 6. INPUT ARTIFACTS

### 6.1 INPUT — METAPHOR_REQUEST
**REQUIRED FIELDS**
- `met_req_id`
- `timestamp`
- `tone_profile_ref` (required)
- `mood_curve_ref` (recommended)
- `symbol_system_ref` (recommended)
- `emotional_resonance_map_ref` (recommended)
- `constraints_refs` (required)
- `world_package_ref` (recommended)
- `theme_hooks_ref` (optional)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 7. OUTPUT ARTIFACTS

### 7.1 OUTPUT — METAPHOR_SYSTEM
(see model above)

### 7.2 OUTPUT — METAPHOR_VERDICT
- `met_req_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 8. CORE OPERATIONS

- OP_01: INGEST_TONE_SYMBOL_RESONANCE_CONSTRAINTS
- OP_02: SELECT_METAPHOR_FRAMES (bounded set)
- OP_03: DEFINE_SOURCE_TARGET_MAPPINGS
- OP_04: DEFINE_ALLOWED_FORBIDDEN_EXPRESSIONS
- OP_05: DEFINE_PACING_PLAN (density by windows)
- OP_06: DEFINE_FORBIDDEN_METAPHORS (platform/taboo)
- OP_07: RUN_COHERENCE_AND_ALIGNMENT_CHECKS
- OP_08: EMIT_METAPHOR_SYSTEM

---

## 9. MISUSE DETECTION

Hard violations (INVALID):
- >3 active frames per arc without declaration
- mixed metaphor collisions without contrast intent
- world-alignment violations that confuse mechanics
- frames without recurrence/decay rules

Soft violations (PARTIAL):
- density too high outside key windows (fatigue)
- metaphor repeated without variation (stale)

Repair suggestions:
- merge frames
- restrict windows
- add decay/mutation
- rewrite expressions to align tone/world
- move high density nearer pivots

---

## 10. DEPENDENCIES

### REQUIRED
- Tone Profile
- Constraints refs

### OPTIONAL
- Symbol system
- Emotional resonance map
- World package
- Theme hooks

### FORBIDDEN
- unlimited frames
- metaphor-as-plot-replacement
- metaphors that contradict established canon logic

---

## 11. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- No mapping rules
- Coherence gates missing
- Frame registry violates limits
- Forbidden metaphors appear as allowed
- Integrity report indicates systemic drift

Reaction:
- Verdict INVALID (CRITICAL)
- Emit repair plan:
  - reduce frames
  - define pacing
  - enforce alignment rules
  - rebuild forbidden list

---

## 12. TRACE RULES

- trace_id optional unless pipeline requires traced execution
- if present, propagate into sensory detail and scene construction constraints

---

## 13. NON-GOALS
- Does not write prose
- Does not decide plot or canon
- Does not create themes

---

## 14. FINAL STATEMENT

Metaphor is a mapping, not magic.
Control the frames — and meaning becomes precise.

---

**STATUS:** Metaphor Engine v1.0  
**REALM:** ACTIVE
