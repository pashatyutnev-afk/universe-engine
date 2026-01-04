# ✍️ RHYME & METER ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · PRODUCTION ENGINE · PROSODY CONTROL · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 06__RHYME_METER_ENG.md
- ENGINE_ID: L3-PROD-RHYME-METER-ENGINE-006
- UID: UE.ENT.ENG.PROD.RHYME_METER
- NAME: Rhyme & Meter Engine
- CLASS: Sound & Music Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (prosody mismatch)
- EDITABLE: true

### ABSOLUTE RULE
> If stress and syllables do not match the groove and melody, lyrics cannot land.

---

## 1. PURPOSE

Rhyme & Meter Engine designs **PROSODY_BLUEPRINTS**:
- meter scheme (syllable counts per line)
- stress map (strong/weak pattern)
- rhyme scheme (end/internal, families, density)
- syllable budgets per section (verse/chorus/etc.)
- hook-line constraints for memorability
- multilingual handling rules (if mixed language)

It outputs a blueprint for Lyrics Engine (07) and Vocal Performance Engine (09).

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define syllable budgets per section and per line
- Define stress map aligned to beat grid
- Define rhyme scheme and rhyme families
- Define internal rhyme / assonance / consonance budgets
- Define hook line constraints (short, punchy, repeatable)
- Define forbidden word-shapes (hard clusters, awkward stresses)
- Define QA gates + repair plan

### OUT-OF-SCOPE (FORBIDDEN)
- writing full lyric text (07)
- melody composition (04)
- harmony (03)
- mixing/mastering

---

## 3. INPUT / OUTPUT

### 3.1 INPUT — PROSODY_REQUEST
Required fields:
- `rm_req_id`
- `timestamp`
- `song_blueprint_ref` (sections)
- `groove_blueprint_ref` (recommended)
- `hook_blueprint_ref` (recommended)
- `language_mode` = RU | EN | MIXED_CONTROLLED | OTHER_DECLARED (required)
- `genre_profile_ref` (optional)
- `tone_profile_ref`
- `constraints_refs`
- `vocal_mode` (VOCAL/HYBRID required; if instrumental, skip engine)
- `trace_id` (optional)

Missing required input → REJECT.

### 3.2 OUTPUT — PROSODY_BLUEPRINT
Required fields:
- `prosody_id`
- `engine_id`
- `version`
- `status` = DRAFT | PARTIAL | FINAL
- `language_mode`
- `section_prosody_map`
- `meter_scheme`
- `stress_map`
- `rhyme_scheme`
- `rhyme_family_rules`
- `sound_devices_budget`
- `hook_line_constraints`
- `forbidden_shapes`
- `compatibility_locks`
- `qa_gates`
- `repair_plan`

---

## 4. METER SCHEME

### 4.1 METER_SCHEME (required fields)
- `per_section_line_count` (sec_type → line_count)
- `syllables_per_line` (sec_type → range or exact)
- `syllable_tolerance` (±)
- `pickup_syllables_allowed` (bool)
- `notes`

Hard rule:
- chorus/hook sections must have tighter tolerance than verses (default).

---

## 5. STRESS MAP (PROSODY GRID)

### 5.1 STRESS_MAP (required fields)
- `grid_alignment` (align stresses to beat positions)
- `stress_pattern_per_section` (sec_id → pattern)
- `primary_stress_targets` (beat positions)
- `avoid_stress_positions` (beat positions)
- `breath_gap_rule` (where pauses can occur)
- `notes`

Hard rule:
- primary hook line must place its primary stresses on stable groove accents.

---

## 6. RHYME SCHEME

### 6.1 RHYME_SCHEME (required fields)
- `end_rhyme_pattern` (e.g., AABB, ABAB, AAAA, etc.)
- `internal_rhyme_density` (0–10)
- `multisyllable_rhyme_allowed` (bool)
- `near_rhyme_allowed` (bool)
- `repetition_rule` (when lines repeat)
- `notes`

Hard rule:
- if near_rhyme_allowed = true, must define acceptability rule.

---

## 7. RHYME FAMILY RULES

### 7.1 RHYME_FAMILY_RULES (required fields)
- `allowed_rhyme_families` (list or method)
- `avoid_overuse_rule` (max repeats per family)
- `hook_rhyme_lock` (true/false)
- `phonetic_consistency_rule` (conceptual)
- `notes`

Hard rule:
- if hook_rhyme_lock true, hook end words must remain in same family across repeats.

---

## 8. SOUND DEVICES BUDGET

### 8.1 SOUND_DEVICES_BUDGET (required fields)
- `assonance_budget` (0–10)
- `consonance_budget` (0–10)
- `alliteration_budget` (0–10)
- `internal_rhyme_budget` (0–10)
- `forbidden_devices` (optional)
- `notes`

---

## 9. HOOK LINE CONSTRAINTS

### 9.1 HOOK_LINE_CONSTRAINTS (required fields)
- `max_words` (recommended)
- `syllable_target` (exact or range)
- `stress_targets` (positions)
- `repeatability_rule` (must survive repeats)
- `memorability_rule` (short, concrete, chantable)
- `forbidden_complexity` (e.g., too many consonant clusters)
- `notes`

Hard rule:
- hook line must be speakable at tempo without “tongue-twist” unless intended and tagged.

---

## 10. FORBIDDEN SHAPES (LINGUISTIC)

### 10.1 FORBIDDEN_SHAPES (required fields)
- `forbidden_consonant_clusters` (optional)
- `forbidden_stress_patterns` (optional)
- `forbidden_syllable_spikes` (e.g., sudden very long words)
- `avoid_hi_density_sibilants` (optional)
- `notes`

---

## 11. COMPATIBILITY LOCKS

### 11.1 COMPATIBILITY_LOCKS (required fields)
- `groove_alignment_lock` (stress-to-accent)
- `hook_identity_lock_ref` (from Melody Hook engine)
- `language_consistency_lock` (if MIXED, rules for switches)
- `breathability_lock` (max continuous syllable run)
- `notes`

---

## 12. QA GATES

### 12.1 QA_GATES (required fields)
- `meter_gate` (syllable counts fit)
- `stress_gate` (stresses align to accents)
- `rhyme_gate` (scheme satisfied)
- `hook_line_gate` (hook constraints satisfied)
- `language_mode_gate` (no uncontrolled mixing)
- `performability_gate` (speakable/singable)

Fail rules:
- stress_gate fail in hook → INVALID (HIGH)
- meter_gate fail across chorus → INVALID (HIGH)

---

## 13. REPAIR PLAN (MANDATORY)

### 13.1 REPAIR PLAN (required)
Common repairs:
- too many syllables → compress wording / remove filler
- stress clashes with groove → move stresses / change word choice
- rhyme forced → broaden family / allow near rhyme with rule
- hook tongue-twister → simplify consonants / reduce word count
- mixed language messy → enforce switch points and reasons

Include:
- `recheck_gates`
- `max_revision_cycles`

---

## 14. CORE OPERATIONS

- OP_01: INGEST_REQUEST
- OP_02: PARSE_STRUCTURE_HOOK_GROOVE
- OP_03: BUILD_METER_SCHEME
- OP_04: BUILD_STRESS_MAP
- OP_05: BUILD_RHYME_SCHEME
- OP_06: BUILD_RHYME_FAMILY_RULES
- OP_07: SET_SOUND_DEVICES_BUDGET
- OP_08: SET_HOOK_LINE_CONSTRAINTS
- OP_09: SET_FORBIDDEN_SHAPES
- OP_10: APPLY_COMPATIBILITY_LOCKS
- OP_11: BUILD_QA_GATES
- OP_12: BUILD_REPAIR_PLAN
- OP_13: EMIT_PROSODY_BLUEPRINT

---

## 15. FAILURE CONDITIONS (ENGINE)

CRITICAL:
- language_mode missing
- structure missing
- vocal_mode not vocal/hybrid

Reaction:
- reject (fail-closed)
- request missing inputs

---

## 16. NON-GOALS
- does not write the lyrics
- does not compose melody
- does not mix/master

---

## 17. FINAL STATEMENT

Prosody is invisible math.
When it’s right — you feel it.
When it’s wrong — nothing saves it.

---

**STATUS:** Rhyme & Meter Engine v1.0  
**REALM:** ACTIVE
