# 🎚️ TONE & MOOD ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · STYLE ENGINE · AFFECT CONTROL · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 01__TONE_MOOD_ENG.md
- ENGINE_ID: L3-STYLE-TONE-MOOD-ENGINE-001
- UID: UE.ENT.ENG.STYLE.TONE_MOOD
- NAME: Tone & Mood Engine
- CLASS: Style Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (tonal integrity)
- EDITABLE: true

### ABSOLUTE RULE
> If tone is undefined, the system will drift. Drift breaks trust.

---

## 1. PURPOSE

Tone & Mood Engine defines and enforces:
- **Tone**: authorial stance + framing attitude (how the story speaks)
- **Mood**: emotional weather over time (how it feels moment-to-moment)

It produces:
- **TONE_PROFILE** (static/constraints)
- **MOOD_CURVE** (dynamic over arc/sequence)
- tonal constraints and forbidden shifts
- repair guidance when drift is detected

This engine makes the “feel” machine-grade and controllable.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define tone/mood schemas and controlled vocabulary
- Choose target tone(s) per project/arc/sequence (bounded set)
- Define mood curve states across time windows
- Define allowed transitions and forbidden jumps
- Map tone/mood to language cues (lexicon, rhythm, harshness, humor allowance)
- Emit validation rules for downstream writing engines

### OUT-OF-SCOPE (FORBIDDEN)
- Plot decisions (narrative engines)
- Canon authority decisions
- Scheduling events (event scheduling engine)
- Full prose generation (production layer) — only constraints and profiles

---

## 3. DEFINITIONS (HARD)

### 3.1 Tone (STATIC FRAME)
Tone is the **narrator/author stance**:
- serious vs playful
- clinical vs poetic
- intimate vs distant
- cynical vs hopeful
- brutal vs gentle

Tone changes rarely and only with explicit justification.

### 3.2 Mood (DYNAMIC WEATHER)
Mood is the **emotional state field** over time:
- dread, wonder, grief, suspense, relief, awe, tenderness, rage, calm
Mood can shift often but must follow allowed transitions.

---

## 4. OUTPUT ARTIFACTS

### 4.1 OUTPUT — TONE_PROFILE (required fields)
- `tp_id`
- `primary_tone` (one)
- `secondary_tones` (0–2 max)
- `voice_distance` = INTIMATE | MEDIUM | DISTANT
- `humor_allowance` = NONE | LOW | MEDIUM | HIGH
- `violence_texture` = IMPLIED | MODERATE | GRAPHIC (if applicable)
- `language_texture` = SIMPLE | NEUTRAL | LYRICAL | TECHNICAL
- `taboo_constraints` (optional list)
- `forbidden_tonal_modes` (list)
- `allowed_tonal_shifts` (list with conditions)
- `style_cues` (lexicon + pacing + sentence shape cues)
- `validation_rules` (hard rules + soft rules)
- `trace_id` (optional)

Missing any required field → REJECT.

### 4.2 OUTPUT — MOOD_CURVE (required fields)
- `mc_id`
- `mode` = ARC | SEQUENCE | SCENE
- `time_windows` (ordered list)
- `dominant_mood_by_window` (map)
- `transition_rules` (allowed next states)
- `intensity_scale` (0–10 per window)
- `spike_points` (optional list)
- `recovery_windows` (optional list)
- `integrity_report` (issues + fixes)
- `trace_id` (optional)

Missing any required field → REJECT.

### 4.3 OUTPUT — TONE_MOOD_VERDICT
- `tm_req_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 5. INPUT ARTIFACTS

### 5.1 INPUT — TONE_MOOD_REQUEST
**REQUIRED FIELDS**
- `tm_req_id`
- `timestamp`
- `target_genre` (required)
- `audience_target` (required)
- `constraints_refs` (required)
- `narrative_intent_ref` (recommended)
- `world_package_ref` (optional)
- `character_package_ref` (optional)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 6. CONTROLLED VOCABULARY (STANDARD SET)

### 6.1 Standard Tone Tags
- SERIOUS
- GROUNDED
- EPIC
- MYTHIC
- NOIR
- SATIRICAL
- HOPEFUL
- NIHILISTIC
- INTIMATE
- CLINICAL
- POETIC
- BRUTAL
- TENDER
- PLAYFUL

### 6.2 Standard Mood Tags
- DREAD
- SUSPENSE
- WONDER
- AWE
- GRIEF
- ANGER
- TENSION
- RELIEF
- CALM
- JOY
- UNEASE
- TRIUMPH
- MELANCHOLY

---

## 7. HARD RULES (TONAL INTEGRITY)

- Primary tone is singular.
- Secondary tones max 2.
- Tone shift requires:
  - explicit condition
  - transition window
  - narrative justification hook
- Mood curve must include:
  - at least 1 recovery window after intensity spikes ≥ 8 (unless horror mode explicitly forbids relief)
- Humor allowance must be compatible with stakes:
  - HIGH humor with CRITICAL stakes requires “dark humor” framing rule.

---

## 8. DRIFT DETECTION (VALIDATION RULES)

### 8.1 Drift Signals
- sudden language_texture change without declared shift
- humor intrusion when humor_allowance = NONE
- violence_texture mismatch (graphic description when implied-only)
- narrator distance flip without transition

### 8.2 Drift Handling
- classify drift: SOFT or HARD violation
- propose repair:
  - rewrite cue adjustment
  - insert transition beat
  - downgrade/upgrade texture
  - constrain vocabulary

---

## 9. CORE OPERATIONS

- OP_01: INGEST_CONSTRAINTS_AND_INTENT
- OP_02: SELECT_PRIMARY_AND_SECONDARY_TONES (bounded)
- OP_03: DEFINE_LANGUAGE_AND_VOICE_PARAMETERS
- OP_04: CONSTRUCT_MOOD_CURVE_WINDOWS
- OP_05: DEFINE_TRANSITION_AND_RECOVERY_RULES
- OP_06: BUILD_VALIDATION_RULESET (drift detection)
- OP_07: EMIT_TONE_PROFILE_AND_MOOD_CURVE

---

## 10. DEPENDENCIES

### REQUIRED
- Constraints refs (genre, platform, rating)
- Audience target

### OPTIONAL
- Narrative intent
- World/character packages

### FORBIDDEN
- Unlimited tone tags (“everything at once”)
- Unjustified tone flips
- Mood curve with constant peak intensity (fatigue) unless explicitly intended

---

## 11. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- No primary tone defined
- Secondary tone overflow (>2)
- Mood curve missing transition rules
- Forbidden tonal mode appears as allowed
- Drift cannot be repaired without redefining constraints

Reaction:
- Verdict INVALID (CRITICAL)
- Emit repair plan:
  - reduce tones
  - define transitions
  - set humor/violence textures
  - rebuild mood windows

---

## 12. TRACE RULES

- trace_id optional unless pipeline requires traced execution
- if present, propagate into atmosphere/resonance/symbolism engines

---

## 13. NON-GOALS
- Does not write prose
- Does not decide plot events
- Does not override canon

---

## 14. FINAL STATEMENT

Tone is the contract.
Mood is the weather.
Control both — and the audience stays inside the story.

---

**STATUS:** Tone & Mood Engine v1.0  
**REALM:** ACTIVE
