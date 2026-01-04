# 🎤 VOCAL PERFORMANCE ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · PRODUCTION ENGINE · PERFORMANCE DIRECTION · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 09__VOCAL_PERFORMANCE_ENG.md
- ENGINE_ID: L3-PROD-VOCAL-PERFORMANCE-ENGINE-009
- UID: UE.ENT.ENG.PROD.VOCAL_PERFORMANCE
- NAME: Vocal Performance Engine
- CLASS: Sound & Music Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (intelligibility + emotion)
- EDITABLE: true

### ABSOLUTE RULE
> If performance does not transmit emotion clearly and keep intelligibility, lyrics fail.

---

## 1. PURPOSE

Vocal Performance Engine produces **VOCAL_PERFORMANCE_PLAN**:
- delivery style and emotion target
- phrasing and breath plan
- articulation and consonant policy
- dynamics and intensity curve
- doubles/harmonies/adlibs plan
- take map and comping rules
- performance QA gates + repair plan

It is the bridge between Lyrics/Prosody and recorded performance.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define vocal style profile (spoken/sung/rap/chant)
- Define emotion targets per section
- Define phrasing + breath points
- Define articulation rules (clarity vs softness)
- Define dynamics control (close/intimate vs wide/power)
- Define doubles/harmonies strategy
- Define take map + comping plan
- Define QA gates + repair plan

### OUT-OF-SCOPE (FORBIDDEN)
- lyric writing (07)
- melody/harmony design (04/03)
- arrangement beyond vocal placement (08)
- mixing/mastering processing decisions (13)

---

## 3. INPUT / OUTPUT

### 3.1 INPUT — VOCAL_PERFORMANCE_REQUEST
Required fields:
- `vp_req_id`
- `timestamp`
- `lyrics_artifact_ref` (required)
- `prosody_blueprint_ref` (required)
- `hook_blueprint_ref` (recommended)
- `song_blueprint_ref` (required)
- `groove_blueprint_ref` (recommended)
- `tone_profile_ref`
- `language_mode`
- `constraints_refs`
- `trace_id` (optional)

Missing required input → REJECT.

### 3.2 OUTPUT — VOCAL_PERFORMANCE_PLAN
Required fields:
- `vp_id`
- `engine_id`
- `version`
- `status` = DRAFT | PARTIAL | FINAL
- `style_profile`
- `section_emotion_map`
- `phrasing_plan`
- `breath_plan`
- `articulation_policy`
- `dynamics_profile`
- `doubles_harmonies_plan`
- `adlibs_plan`
- `take_map`
- `comping_rules`
- `delivery_notes`
- `qa_gates`
- `repair_plan`

---

## 4. STYLE PROFILE

### 4.1 STYLE_PROFILE (required fields)
- `delivery_mode` = SING | RAP | SPOKEN | CHANT | HYBRID
- `tone_color` (airy/dry/gritty/clean/whisper/power; conceptual)
- `attitude` (confident/broken/angry/playful/etc.)
- `intelligibility_target` (0–10)
- `emotion_target_global` (short)
- `notes`

Hard rule:
- intelligibility_target < 6 must be explicitly justified (e.g., “dreamy wash”).

---

## 5. SECTION EMOTION MAP

### 5.1 SECTION_EMOTION (required per section)
- `sec_id`
- `emotion_label` (e.g., longing, defiance)
- `intensity_target` (0–10)
- `energy_behavior` (build/hold/release)
- `timbre_instruction` (conceptual)
- `notes`

Hard rule:
- hook sections must have explicit emotion_label + intensity_target.

---

## 6. PHRASING PLAN

### 6.1 PHRASING_PLAN (required fields)
- `phrase_grouping_rules` (how lines group into phrases)
- `pickup_rules` (early/late entries; align with groove)
- `rubato_allowance` (0–10; usually low in tight groove)
- `phrase_end_rules` (cut/release/vibrato/tail)
- `notes`

---

## 7. BREATH PLAN

### 7.1 BREATH_PLAN (required fields)
- `breath_points` (map sec_id → list of breath markers)
- `max_no_breath_run` (syllables or seconds)
- `breath_noise_policy` (keep/clean)
- `emergency_breath_rule` (if phrasing too dense)
- `notes`

Hard rule:
- must respect prosody breathability lock.

---

## 8. ARTICULATION POLICY

### 8.1 ARTICULATION_POLICY (required fields)
- `consonant_attack` (soft/medium/hard)
- `sibilance_control_note` (conceptual)
- `vowel_shape_note` (open/closed/neutral)
- `language_specific_rules` (RU/EN differences if mixed)
- `hook_word_clarity_lock` (words that must be clear)
- `notes`

Hard rule:
- hook keywords (from lyrics brief) must be included in hook_word_clarity_lock.

---

## 9. DYNAMICS PROFILE

### 9.1 DYNAMICS_PROFILE (required fields)
- `distance_profile` (close/intimate vs stage/wide)
- `dynamic_range` (0–10)
- `section_dynamic_targets` (sec_id → 0–10)
- `peak_control_rule` (avoid clipping by performance control)
- `notes`

---

## 10. DOUBLES / HARMONIES PLAN

### 10.1 DOUBLES_HARMONIES_PLAN (required fields)
- `doubles_policy` (none/chorus-only/selected-words)
- `harmony_policy` (none/thirds/fifths/pads)
- `hook_stack_rule` (how hook is stacked)
- `call_response_policy` (optional)
- `notes`

Hard rule:
- hook stacking must not reduce intelligibility (gate below).

---

## 11. ADLIBS PLAN (OPTIONAL)

### 11.1 ADLIBS_PLAN (required if used)
- `allowed_sections`
- `density` (0–10)
- `content_policy` (no taboo, no derail)
- `timing_rule` (after main words / gaps)
- `notes`

---

## 12. TAKE MAP

### 12.1 TAKE_MAP (required fields)
- `takes_per_section_target`
- `priority_sections` (hook/chorus)
- `alternate_delivery_take` (optional)
- `punch_in_policy` (when punch-ins are allowed)
- `notes`

Hard rule:
- hook section must have at least 2 takes target by default.

---

## 13. COMPING RULES

### 13.1 COMPING_RULES (required fields)
- `selection_priority` (emotion > timing > pitch, or declared)
- `timing_tolerance` (tight/medium/loose)
- `pitch_correction_policy` (none/light/medium; conceptual)
- `consistency_lock` (avoid “patchwork voice”)
- `notes`

---

## 14. QA GATES

### 14.1 QA_GATES (required fields)
- `intelligibility_gate` (words understandable where required)
- `emotion_gate` (emotion transmitted per section targets)
- `prosody_gate` (phrasing respects meter/stress)
- `timing_gate` (sits in groove pocket)
- `hook_gate` (hook clarity + memorability)
- `fatigue_gate` (no constant shouting unless intended)
- `stack_gate` (doubles/harmonies do not blur hook)

Fail rules:
- hook_gate fail → INVALID (HIGH/CRITICAL)
- intelligibility_gate fail on hook keywords → INVALID (HIGH)

---

## 15. REPAIR PLAN (MANDATORY)

### 15.1 REPAIR PLAN (required)
Common repairs:
- words unclear → increase consonant attack + re-record hook keywords
- emotion flat → new takes with clearer intention; adjust intensity targets
- timing off → re-take with pocket placement rule; reduce rubato
- breath issues → move breath points; simplify dense lines (feeds back to Lyrics)
- hook too stacked → reduce doubles; keep one clean lead
- fatigue → lower dynamic targets; add contrast sections

Include:
- `recheck_gates`
- `max_revision_cycles`

---

## 16. CORE OPERATIONS

- OP_01: INGEST_REQUEST
- OP_02: BUILD_STYLE_PROFILE
- OP_03: BUILD_SECTION_EMOTION_MAP
- OP_04: BUILD_PHRASING_PLAN
- OP_05: BUILD_BREATH_PLAN
- OP_06: BUILD_ARTICULATION_POLICY
- OP_07: BUILD_DYNAMICS_PROFILE
- OP_08: BUILD_DOUBLES_HARMONIES_PLAN
- OP_09: BUILD_ADLIBS_PLAN (optional)
- OP_10: BUILD_TAKE_MAP
- OP_11: BUILD_COMPING_RULES
- OP_12: BUILD_QA_GATES
- OP_13: BUILD_REPAIR_PLAN
- OP_14: EMIT_VOCAL_PERFORMANCE_PLAN

---

## 17. FAILURE CONDITIONS (ENGINE)

CRITICAL:
- lyrics_artifact_ref missing
- prosody_blueprint_ref missing
- structure missing

Reaction:
- reject (fail-closed)
- request missing refs

---

## 18. NON-GOALS
- does not mix vocals
- does not design vocal FX chain
- does not rewrite lyrics directly (only feedback)

---

## 19. FINAL STATEMENT

Performance is the delivery mechanism.
If it misses — the text is dead.

---

**STATUS:** Vocal Performance Engine v1.0  
**REALM:** ACTIVE
