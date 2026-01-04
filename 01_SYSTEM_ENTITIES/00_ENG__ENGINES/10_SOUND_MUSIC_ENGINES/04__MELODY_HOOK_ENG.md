# 🎣 MELODY HOOK ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · PRODUCTION ENGINE · HOOK DESIGN · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 04__MELODY_HOOK_ENG.md
- ENGINE_ID: L3-PROD-MELODY-HOOK-ENGINE-004
- UID: UE.ENT.ENG.PROD.MELODY_HOOK
- NAME: Melody Hook Engine
- CLASS: Sound & Music Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (hook identity)
- EDITABLE: true

### ABSOLUTE RULE
> If the hook identity drifts, the audience loses the song.

---

## 1. PURPOSE

Melody Hook Engine designs **HOOK_BLUEPRINTS**:
- hook DNA (contour, rhythm silhouette, signature intervals)
- placement and timing rules (arrival, reentry)
- singability constraints (if vocal)
- motif coupling (if motifs exist)
- variation budgets (what can change vs locked)
- compatibility checks with harmony/rhythm/lyrics constraints

It produces a blueprint that can be rendered by composers or generative tools.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define hook identity locks
- Define melodic contour and anchor tones (conceptual)
- Define hook rhythm silhouette and pickup rules
- Define register range and tessitura constraints
- Define repetition and micro-variation rules
- Define hook versions: primary / alt / minimal / stinger
- Define call-response subhooks (optional)
- Define QA gates + repair plan

### OUT-OF-SCOPE (FORBIDDEN)
- full harmony selection (03 engine)
- groove micro-design (05 engine)
- detailed lyric writing (07 engine)
- orchestration detail (08 engine)
- mixing/mastering

---

## 3. INPUT / OUTPUT

### 3.1 INPUT — HOOK_REQUEST
Required fields:
- `mh_req_id`
- `timestamp`
- `song_blueprint_ref` (sections + hook map)
- `harmony_blueprint_ref` (recommended)
- `tone_profile_ref`
- `genre_profile_ref` (optional)
- `cue_type` (if cue-based)
- `motif_plan_ref` (optional)
- `constraints_refs`
- `vocal_mode` = INSTRUMENTAL | VOCAL | HYBRID (required)
- `trace_id` (optional)

Missing required input → REJECT.

### 3.2 OUTPUT — HOOK_BLUEPRINT
Required fields:
- `hook_id`
- `engine_id`
- `version`
- `status` = DRAFT | PARTIAL | FINAL
- `hook_dna`
- `hook_variants`
- `placement_rules`
- `singability_profile` (if vocal)
- `motif_coupling` (if motifs used)
- `compatibility_locks`
- `qa_gates`
- `repair_plan`

---

## 4. HOOK DNA (IDENTITY CORE)

### 4.1 HOOK_DNA (required fields)
- `contour_profile` (UP/DOWN/ARCH/WAVE/STEPWISE + description)
- `anchor_tones` (conceptual: tonic/third/fifth or “home/bright/tension”)
- `signature_intervals` (list; e.g., “leap of 5th”, “minor 2nd bite”)
- `rhythm_silhouette` (syncopated/straight/anticipation/late)
- `hook_length_ref` (bars or seconds)
- `pickup_rule` (none / pickup / delayed-entry)
- `memorability_driver` (one-liner: what makes it stick)
- `identity_lock` (true/false)

Hard rule:
- identity_lock true requires explicit variation budgets.

---

## 5. HOOK VARIANTS

### 5.1 HOOK_VARIANTS (required fields)
Must include at least:
- `PRIMARY`
- `ALT_MINIMAL`
Optional:
- `STINGER`
- `CALL_RESPONSE`
- `INSTRUMENTAL_ONLY`
- `VOCAL_ONLY`

Each variant:
- `variant_id`
- `role`
- `allowed_changes` (list)
- `locked_elements` (list)
- `intensity_target` (0–10)
- `notes`

Hard rule:
- PRIMARY locked elements must include at least contour_profile OR rhythm_silhouette.

---

## 6. PLACEMENT RULES (TIMING)

### 6.1 PLACEMENT_RULES (required fields)
- `first_hook_deadline_ref` (time)
- `reentry_frequency_rule` (e.g., every N sections)
- `avoid_early_overuse_rule`
- `hitpoint_alignment_rule` (optional)
- `cut_safe_entry_points`
- `cut_safe_exit_points`

Hard rule:
- if Song Structure says hook_priority HIGH, first_hook_deadline_ref must match its requirement.

---

## 7. SINGABILITY PROFILE (VOCAL)

Required if `vocal_mode` includes VOCAL.

### 7.1 SINGABILITY_PROFILE (required fields)
- `range_limit` (low..high; conceptual ok)
- `tessitura_focus` (where most notes sit)
- `max_leap_size` (e.g., 7th max) (conceptual)
- `breath_points_rule`
- `consonant_attack_rule` (if lyrics used; optional)
- `difficulty_rating` (1–10)
- `notes`

Hard rule:
- difficulty > 7 must include rationale and intended performer type.

---

## 8. MOTIF COUPLING (OPTIONAL)

If motifs exist:
### 8.1 MOTIF_COUPLING (required fields)
- `motif_ids_linked`
- `coupling_type` = DIRECT_QUOTE | RHYTHMIC_ECHO | INTERVAL_ECHO | CONTOUR_ECHO | HARMONIC_ECHO
- `quote_budget` (0–10)
- `forbidden_motif_distortions`
- `notes`

Hard rule:
- DIRECT_QUOTE requires motif_identity_lock true upstream.

---

## 9. COMPATIBILITY LOCKS

### 9.1 COMPATIBILITY_LOCKS (required fields)
- `harmony_compat_rule` (avoid clashes with cadence plan)
- `rhythm_compat_rule` (hook rhythm must sit in groove pocket)
- `lyrics_compat_rule` (if lyrics planned; syllable fit)
- `instrumentation_compat_rule` (hook must be audible)
- `variation_budget_global` (0–10)
- `forbidden_changes` (list)

Hard rule:
- variation_budget_global cannot exceed Song Structure hook_variation_budget (if provided).

---

## 10. QA GATES

### 10.1 QA_GATES (required fields)
- `identity_gate` (hook recognizable across variants)
- `placement_gate` (arrives on time)
- `singability_gate` (if vocal)
- `compatibility_gate` (harmony/rhythm/arrangement)
- `fatigue_gate` (not overused or too dense)
- `edit_gate` (entry/exit points exist)

Fail rules:
- identity_gate fail → INVALID (HIGH/CRITICAL)
- placement_gate fail in short formats → INVALID (HIGH)

---

## 11. REPAIR PLAN (MANDATORY)

### 11.1 REPAIR PLAN (required)
Common repairs:
- hook not catchy → simplify contour + stronger signature interval
- hook too hard to sing → reduce leaps + lower tessitura
- hook clashes with harmony → shift anchors to stable tones near cadences
- hook rhythm fights groove → simplify silhouette or move accents
- hook fatigue → add ALT_MINIMAL and reduce reentry frequency
- hook not audible → adjust instrumentation constraints (08 engine)

Include:
- `recheck_gates`
- `max_revision_cycles`

---

## 12. CORE OPERATIONS

- OP_01: INGEST_REQUEST
- OP_02: PARSE_STRUCTURE_AND_HOOK_MAP
- OP_03: DEFINE_HOOK_DNA
- OP_04: DEFINE_PRIMARY_VARIANT
- OP_05: DEFINE_ALT_MINIMAL_VARIANT
- OP_06: DEFINE_OPTIONAL_VARIANTS (as needed)
- OP_07: SET_PLACEMENT_RULES
- OP_08: BUILD_SINGABILITY_PROFILE (if vocal)
- OP_09: BUILD_MOTIF_COUPLING (if motifs)
- OP_10: APPLY_COMPATIBILITY_LOCKS
- OP_11: BUILD_QA_GATES
- OP_12: BUILD_REPAIR_PLAN
- OP_13: EMIT_HOOK_BLUEPRINT

---

## 13. FAILURE CONDITIONS (ENGINE)

CRITICAL:
- song_blueprint_ref missing
- vocal_mode missing
- hook map missing when hook_priority is HIGH

Reaction:
- reject (fail-closed)
- request missing refs

---

## 14. NON-GOALS
- does not write full melody for entire song
- does not orchestrate instrumentation details
- does not mix/master

---

## 15. FINAL STATEMENT

The hook is the memory chip.
Protect its DNA — or you lose the listener.

---

**STATUS:** Melody Hook Engine v1.0  
**REALM:** ACTIVE
