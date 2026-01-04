# 🧷 SPEECH NATURALIZATION ENGINE
## Canonical Engine Specification  
**LEVEL: L2 · DOMAIN ENGINE · VOICE SYSTEM · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 08__SPEECH_NATURALIZATION_ENG.md
- ENGINE_ID: L2-DOM-SPEECH-NATURALIZATION-ENGINE-008
- UID: UE.ENT.ENG.DOM.CHARACTER.SPEECH_NATURALIZATION
- NAME: Speech Naturalization Engine
- CLASS: Domain Engine
- DOMAIN: Character
- CATEGORY: Voice Profile, Idiolect, Diction & Natural Speech Constraints
- LEVEL: L2
- STATUS: FINAL
- FAILURE_MODE: fail-closed (for voice consistency)
- EDITABLE: true
- BYPASS_ALLOWED: false (within character pipeline)

### ABSOLUTE RULE
> If every character sounds the same, the cast collapses into one voice.

---

## 1. PURPOSE

Speech Naturalization Engine produces:
- **VOICE_PROFILE** per character (how they speak)
- **NATURALIZATION_BLUEPRINT** for turning dialogue intent into natural lines

It guarantees:
- consistent idiolect (personal speech fingerprint)
- vocabulary/education alignment to world constraints
- rhythm, brevity, fillers, interruptions, politeness level
- “stress speech” shifts (speech changes under pressure)
- avoidance of exposition dumps through voice constraints

This engine does not invent scene intent; it renders it as believable speech patterns.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define voice profile per character (tone, diction, cadence)
- Define rules for sentence length, complexity, slang usage
- Define signature phrases, verbal tics (controlled, not spam)
- Define taboo words/topics (speech constraints)
- Define deception speech style (if character lies)
- Define stress speech modes (fight/flight/freeze/fawn voice)
- Produce blueprint mapping dialogue beats → naturalized utterance constraints
- Detect “same-voice syndrome” across characters and suggest separation

### OUT-OF-SCOPE (FORBIDDEN)
- Creating dialogue intent (Dialogue Engine)
- Changing plot info or reveal schedule
- Writing long final dialogue scenes as output artifact (only blueprint/spec)
- Canon authority decisions (Governance)

---

## 3. VOICE MODEL

### 3.1 Voice Dimensions (fixed)
- FORMALITY: 0..10
- DIRECTNESS: 0..10
- EMOTIONALITY: 0..10
- HUMOR: 0..10
- AGGRESSION: 0..10
- EMPATHY: 0..10
- VERBOSITY: 0..10 (talkativeness)
- EDUCATION_LEVEL: 0..10 (linguistic complexity)

### 3.2 Idiolect Components
- default_sentence_length: SHORT | MEDIUM | LONG
- cadence: STACCATO | EVEN | FLOWING
- favorite_constructions (e.g., rhetorical questions, imperatives)
- filler_usage: LOW | MEDIUM | HIGH
- interruption_style: RARE | NORMAL | FREQUENT
- signature_phrases (max 3–5)
- taboo_topics (optional)

### 3.3 Stress Speech Modes
- STRESS_FIGHT: sharper, threats, imperatives
- STRESS_FLIGHT: short evasions, topic shifts
- STRESS_FREEZE: pauses, minimal answers
- STRESS_FAWN: politeness spikes, agreement, apologies

---

## 4. INPUT ARTIFACTS

### 4.1 INPUT — VOICE_REQUEST
**REQUIRED FIELDS**
- `voice_id`
- `timestamp`
- `char_core_profile_ref`
- `motivation_map_ref` (recommended)
- `value_profile_ref` (recommended)
- `psyche_model_ref` (recommended)
- `world_constraints_refs`
- `relationship_edge_ref` (optional; affects politeness/power)
- `trace_id` (optional)

Missing required fields → REJECT.

### 4.2 INPUT — NATURALIZATION_REQUEST
**REQUIRED FIELDS**
- `nat_id`
- `timestamp`
- `dialogue_intent_spec_ref`
- `voice_profiles_refs` (required)
- `reveal_schedule_ref` (optional)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 5. OUTPUT ARTIFACTS

### 5.1 OUTPUT — VOICE_PROFILE
**REQUIRED FIELDS**
- `voice_id`
- `char_id`
- `voice_dimensions` (values in 0..10)
- `idiolect` (components from 3.2)
- `preferred_tactics_as_speech` (how tactics sound for this voice)
- `deception_speech_style` (if applicable)
- `stress_voice_modes` (mapping from 3.3)
- `do_not_do` (speech anti-patterns for this character)
- `distinctiveness_notes` (what makes it unique)
- `trace_id` (if provided)

### 5.2 OUTPUT — NATURALIZATION_BLUEPRINT
**REQUIRED FIELDS**
- `nat_id`
- `scene_id`
- `turn_blueprints` (ordered list per dialogue beat)
Each blueprint includes:
- `beat_id`
- `speaker`
- `allowed_length` (short/medium/long)
- `tone_target` (calm/tense/sarcastic/etc.)
- `diction_constraints` (simple/complex, slang allowed, taboo words)
- `subtext_delivery_style` (hint, deny, joke, silence, etc.)
- `avoid_exposition_rules` (what must not be explained directly)
- `stress_mode_if_triggered` (optional)
- `micro_variants` (2–3 micro-options: NOT full lines, only approach labels)

- `voice_consistency_checks`
- `trace_id` (if provided)

### 5.3 OUTPUT — SPEECH_VERDICT
- `id` = voice_id or nat_id
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 6. CORE OPERATIONS

- OP_01: BUILD_VOICE_DIMENSIONS
- OP_02: BUILD_IDIOLECT_COMPONENTS
- OP_03: DEFINE_STRESS_VOICE_MODES
- OP_04: CHECK_DISTINCTIVENESS (anti-same-voice)
- OP_05: MAP_DIALOGUE_BEATS_TO_TURN_BLUEPRINTS
- OP_06: EMIT_VOICE_PROFILE_AND_BLUEPRINT

---

## 7. ACCESS MODEL

### WRITE
- Domain pipeline outputs only

### READ
- Dialogue Engine (feedback: tactics feasibility)
- Relationship Engine (politeness/power tuning)
- Scene Construction Engine (dialogue integration)
- Continuity Engine (ensure vocabulary matches knowledge state)

### DELETE
- Allowed for drafts; finalization per project governance

---

## 8. DEPENDENCIES

### REQUIRED
- Character Core Profile
- World constraints (language/culture plausibility)
- Dialogue Intent Spec (for naturalization blueprint)

### FORBIDDEN
- Making new reveals via phrasing
- Producing “one voice fits all”
- Overusing signature phrases (spam)

---

## 9. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- Voice profile missing idiolect (no unique fingerprint)
- Dimensions contradict world constraints (e.g., illiterate but highly academic diction) without bridge
- Naturalization blueprint encourages exposition dumps
- Two major characters share near-identical voice dimensions + idiolect with no separation notes
- Stress modes undefined for high-stress characters

Reaction:
- Verdict INVALID (CRITICAL)
- Provide repairs: define idiolect, separate voices, add stress speech rules.

---

## 10. TRACE RULES

- trace_id optional unless orchestrator requires traced pipeline
- if present, propagate constraints into downstream outputs

---

## 11. NON-GOALS
- Does not create dialogue intent
- Does not change plot information
- Does not grant canon authority
- Does not output long final scripts as canonical artifacts

---

## 12. FINAL STATEMENT

Voice is identity in motion.
Natural speech makes intent believable.

---

**STATUS:** Speech Naturalization Engine v1.0  
**DOMAIN:** ACTIVE
