# 🎚️ MIX & MASTER ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · PRODUCTION ENGINE · DELIVERY QC · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 13__MIX_MASTER_ENG.md
- ENGINE_ID: L3-PROD-MIX-MASTER-ENGINE-013
- UID: UE.ENT.ENG.PROD.MIX_MASTER
- NAME: Mix & Master Engine
- CLASS: Sound & Music Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (delivery quality)
- EDITABLE: true

### ABSOLUTE RULE
> If delivery targets and QC gates are not met, the audio is not released.

---

## 1. PURPOSE

Mix & Master Engine produces **DELIVERY_SPEC** and **QC_REPORT**:
- mix intent (priority signal: hook/dialogue/music bed)
- loudness targets per platform/format
- peak/true-peak constraints and headroom
- stem deliverables and naming
- export specs (sample rate, bit depth, file types)
- QC gates (clipping, distortion, masking, mono compatibility)
- revision plan (what to fix first)

This engine is a **quality gate** for any audio output.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define loudness and peak targets
- Define mix priority and masking rules
- Define stem export package requirements
- Define basic processing intent (conceptual)
- Define QC checks + pass/fail conditions
- Define export formats and file naming conventions
- Define repair plan

### OUT-OF-SCOPE (FORBIDDEN)
- composing music
- writing lyrics
- changing arrangement roles (only feedback to 08 engine)
- changing prosody (feedback to 06/07)
- editorial decisions outside target formats

---

## 3. INPUT / OUTPUT

### 3.1 INPUT — MIX_MASTER_REQUEST
Required fields:
- `mm_req_id`
- `timestamp`
- `target_format_ref` (platform + duration type)
- `priority_signal` = DIALOGUE | MUSIC_HOOK | MUSIC_BED | SFX_ONLY (required)
- `arrangement_plan_ref` (recommended)
- `stem_mapping_ref` (required if stems delivered)
- `dialogue_presence` = NONE | LOW | HIGH (required)
- `constraints_refs`
- `delivery_scope` = FINAL_ONLY | FINAL_PLUS_STEMS (required)
- `trace_id` (optional)

Optional:
- `style_fingerprint_ref` (11)
- `scene_sync_blueprint_ref` (12)
- `sound_design_layer_map_ref` (10)
- `reference_mix_refs` (optional)

Missing required input → REJECT.

### 3.2 OUTPUT — DELIVERY_PACKAGE_SPEC
Required fields:
- `delivery_id`
- `engine_id`
- `version`
- `status` = DRAFT | PARTIAL | FINAL
- `mix_intent`
- `loudness_targets`
- `peak_targets`
- `masking_rules`
- `stem_deliverables` (if needed)
- `export_spec`
- `file_naming_spec`
- `qc_gates`
- `qc_report_template`
- `repair_plan`

---

## 4. MIX INTENT

### 4.1 MIX_INTENT (required fields)
- `priority_signal` (from request)
- `secondary_priority` (optional)
- `hook_protection_policy` (if hook exists)
- `dialogue_protection_policy` (if dialogue_presence != NONE)
- `low_end_policy` (tight/large/controlled)
- `width_policy` (mono-safe/wide/controlled)
- `notes`

Hard rule:
- if dialogue_presence HIGH, dialogue_protection_policy must override music width/brightness where needed.

---

## 5. LOUDNESS TARGETS

### 5.1 LOUDNESS_TARGETS (required fields)
Define per target_format_ref:
- `integrated_lufs_target` (range allowed)
- `short_term_lufs_limit` (optional)
- `momentary_lufs_limit` (optional)
- `dynamic_range_target` (0–10)
- `notes`

Hard rule:
- must define allowed range (not a single unbounded number).

---

## 6. PEAK TARGETS

### 6.1 PEAK_TARGETS (required fields)
- `true_peak_max_dbTP`
- `sample_peak_max_dbFS`
- `headroom_db`
- `clip_zero_tolerance` (true/false)
- `notes`

Hard rule:
- clip_zero_tolerance true → any clip event is FAIL.

---

## 7. MASKING RULES

### 7.1 MASKING_RULES (required fields)
- `critical_band_protection` (dialogue or hook frequency region; conceptual)
- `sibilance_control_intent` (if vocals)
- `hook_keyword_clarity_rule` (if vocals)
- `fx_transient_ceiling` (if SFX present)
- `notes`

Hard rule:
- if priority_signal MUSIC_HOOK, hook_keyword_clarity_rule must exist for vocal hooks.

---

## 8. STEM DELIVERABLES (OPTIONAL)

Required if delivery_scope = FINAL_PLUS_STEMS.

### 8.1 STEM_DELIVERABLES (required fields)
At minimum:
- `MIX_FULL`
- `DRUMS`
- `BASS`
- `MUSIC_NO_LEAD` (optional but recommended)
- `LEAD` (hook lead or vocals)
- `FX_TRANSITIONS` (if present)
- `SFX_MAIN` (if present)

Fields:
- `stem_list` (with descriptions)
- `phase_alignment_rule`
- `stem_loudness_policy` (consistent references)
- `mute_safe_tests` (list)
- `notes`

Hard rule:
- stems must sum to MIX_FULL within tolerance (declared).

---

## 9. EXPORT SPEC

### 9.1 EXPORT_SPEC (required fields)
- `sample_rate` (e.g., 48k)
- `bit_depth` (e.g., 24-bit)
- `file_format` (WAV/AIFF/etc.)
- `dither_policy` (if needed)
- `mono_compatibility_requirement` (pass/fail)
- `deliverable_variants` (e.g., full, instrumental, a cappella if needed)
- `notes`

Hard rule:
- target_format_ref must define defaults; if not, engine must set them explicitly.

---

## 10. FILE NAMING SPEC

### 10.1 FILE_NAMING_SPEC (required fields)
- `base_pattern`
- `required_tokens` (project_id, cue_id, version, duration, stem_name)
- `forbidden_characters`
- `example_names` (list)

Hard rule:
- must be consistent across stems and masters.

---

## 11. QC GATES

### 11.1 QC_GATES (required fields)
- `loudness_gate` (within target range)
- `true_peak_gate` (<= true_peak_max_dbTP)
- `clip_gate` (no clips if zero tolerance)
- `distortion_gate` (no audible distortion in critical regions)
- `masking_gate` (dialogue/hook intelligible)
- `mono_gate` (mono compatibility pass)
- `stem_sum_gate` (if stems)
- `noise_floor_gate` (optional)
- `export_gate` (format correct)

Fail rules:
- true_peak_gate fail → FAIL (HIGH)
- clip_gate fail with zero tolerance → FAIL (CRITICAL)
- masking_gate fail with dialogue_presence HIGH → FAIL (CRITICAL)

---

## 12. QC REPORT TEMPLATE

### 12.1 QC_REPORT_TEMPLATE (required fields)
- `checks_run` (list)
- `measurements` (placeholders: LUFS, dBTP, etc.)
- `issues_found` (list)
- `severity` (LOW/MED/HIGH/CRITICAL)
- `recommended_actions`
- `recheck_required` (bool)

---

## 13. REPAIR PLAN (MANDATORY)

### 13.1 REPAIR PLAN (required)
Common repairs:
- loudness off → adjust master gain / gentle compression intent
- peaks too high → limit/clip control within policy
- hook masked → reduce competing midrange, tighten SFX transients
- dialogue masked → carve music bed, reduce width/brightness in dialogue windows
- mono issues → reduce wide phasey elements, enforce mono-safe policy
- stems mismatch → align phase and rebalance stem exports

Include:
- `recheck_gates`
- `max_revision_cycles`

---

## 14. CORE OPERATIONS

- OP_01: INGEST_REQUEST
- OP_02: SET_MIX_INTENT
- OP_03: SET_LOUDNESS_TARGETS
- OP_04: SET_PEAK_TARGETS
- OP_05: SET_MASKING_RULES
- OP_06: DEFINE_STEM_DELIVERABLES (if needed)
- OP_07: DEFINE_EXPORT_SPEC
- OP_08: DEFINE_FILE_NAMING_SPEC
- OP_09: DEFINE_QC_GATES
- OP_10: BUILD_QC_REPORT_TEMPLATE
- OP_11: BUILD_REPAIR_PLAN
- OP_12: EMIT_DELIVERY_PACKAGE_SPEC

---

## 15. FAILURE CONDITIONS (ENGINE)

CRITICAL:
- target_format_ref missing
- priority_signal missing
- dialogue_presence missing
- delivery_scope missing

Reaction:
- reject (fail-closed)
- request missing inputs

---

## 16. NON-GOALS
- does not create the mix audio itself (outside system execution)
- does not override creative intent without governance

---

## 17. FINAL STATEMENT

Mastering is permission to publish.
No QC pass — no release.

---

**STATUS:** Mix & Master Engine v1.0  
**REALM:** ACTIVE
