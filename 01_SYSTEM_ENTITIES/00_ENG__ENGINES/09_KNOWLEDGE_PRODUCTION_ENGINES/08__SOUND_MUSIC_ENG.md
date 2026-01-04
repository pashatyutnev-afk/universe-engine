# 🔊 SOUND & MUSIC ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · PRODUCTION ENGINE · AUDIO PACKAGE · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 08__SOUND_MUSIC_ENG.md
- ENGINE_ID: L3-PROD-SOUND-MUSIC-ENGINE-008
- UID: UE.ENT.ENG.PROD.SOUND_MUSIC
- NAME: Sound & Music Engine
- CLASS: Knowledge Production Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (auditory continuity)
- EDITABLE: true

### ABSOLUTE RULE
> Audio is subconscious control. If audio contradicts the scene, the brain rejects the world.

---

## 1. PURPOSE

Sound & Music Engine defines an **audio package** for production:
- sound design layers (ambience, Foley, SFX, UI)
- music cue map (themes, tension beds, stingers)
- sync hooks (beats, transitions, reveals)
- loudness/dynamics policy
- dialogue intelligibility policy (if dialogue exists)
- continuity anchors (signature tones, motifs)
- forbidden audio drift patterns
- deliverable audio stems plan

It produces:
- **SOUND_MUSIC_PACKAGE**
- cue sheet + layer map compatible with editing/montage plan

This engine prevents “random music swaps” and messy loudness.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define ambience + Foley + SFX layer structure
- Define music cue strategy and placement rules
- Define sync hooks for edits and transitions
- Define dynamics/loudness policy
- Define dialogue clarity constraints (if used)
- Define continuity anchors (motifs, signature sound)
- Define deliverable stems and export plan
- Define QA gates for audio continuity and clipping

### OUT-OF-SCOPE (FORBIDDEN)
- Composing full music (handled by Sound Music Engines realm 12 in detail)
- Rewriting narrative
- Changing canon facts
- Overriding edit logic (must align with Editing Engine)

---

## 3. SOUND/MUSIC PACKAGE MODEL

### 3.1 Output — SOUND_MUSIC_PACKAGE (required fields)
- `smp_id`
- `target_format_ref` (required)
- `audio_layers` (required)
- `music_cue_map` (required)
- `sync_hooks` (required)
- `dynamics_loudness_policy` (required)
- `dialogue_intelligibility_policy` (required)
- `continuity_anchors` (required)
- `negative_constraints` (required)
- `deliverable_stems` (required)
- `qa_gates` (required)
- `repair_plan` (required)
- `integrity_report` (issues + fixes)
- `trace_id` (optional)

Missing any required field → REJECT.

---

## 4. AUDIO LAYERS

### 4.1 AUDIO_LAYERS (required fields)
- `ambience_layer` (required)
- `foley_layer` (optional but recommended)
- `sfx_layer` (required)
- `ui_layer` (optional)
- `music_layer` (required)
- `dialogue_layer` (optional)
- `layer_priority_rules` (required)
- `notes`

Hard rule:
- layer_priority_rules must protect intelligibility (dialogue/primary info always wins).

---

## 5. AMBIENCE LAYER

### 5.1 AMBIENCE_LAYER (required fields)
- `world_room_tone_policy` (consistent baseline)
- `location_signature_sounds` (list)
- `density_policy` (low/med/high + bounds)
- `movement_policy` (static/moving ambience)
- `forbidden_ambience` (generic unrelated beds)
- `notes`

Hard rule:
- ambience must match location/time mood coupling.

---

## 6. SFX + FOLEY LAYERS

### 6.1 FOLEY_LAYER (optional fields)
- `presence` (bool)
- `detail_density` (low/med/high)
- `priority_objects` (hands/tools/steps/etc.)
- `notes`

### 6.2 SFX_LAYER (required fields)
- `sfx_categories` (impacts, whooshes, tech, explosions, UI clicks etc.)
- `style_mode` = REALISTIC | STYLIZED | HYBRID_CONTROLLED
- `usage_rules` (when to use, when to avoid)
- `forbidden_sfx` (overused risers, meme hits unless allowed)
- `notes`

Hard rule:
- SFX must not mask primary information.

---

## 7. MUSIC CUE MAP

### 7.1 MUSIC_CUE_MAP (required fields)
- `themes_motifs` (required)
- `cue_types_allowed` (bed, stinger, transition cue, tension pulse)
- `cue_placement_rules` (required)
- `cue_exclusion_rules` (where music must be silent)
- `max_music_density` (bounded)
- `notes`

### 7.2 THEME_MOTIF (required fields)
- `motif_id`
- `role` (hero, villain, mystery, awe, tragedy etc.)
- `instrumentation_bias` (conceptual)
- `tempo_band` (conceptual)
- `harmonic_color` (conceptual)
- `recurrence_rules` (where it reappears)
- `notes`

Hard rule:
- motifs must be stable; swapping motif identity mid-episode is forbidden.

---

## 8. SYNC HOOKS (EDIT COUPLING)

### 8.1 SYNC_HOOKS (required fields)
- `hook_points` (list of HOOK_POINT)
- `allowed_hook_types` (beat hit, sting, silence drop, swell)
- `forbidden_hook_types` (random stings)
- `notes`

### 8.2 HOOK_POINT (required fields)
- `hook_id`
- `time_ref` (or segment/shot ref)
- `trigger` (cut, reveal, transition, impact)
- `audio_action` (sting, drop, swell, whoosh, hard stop)
- `intensity` (0–10)
- `notes`

Hard rule:
- hooks must support editing intent, not compete with it.

---

## 9. DYNAMICS & LOUDNESS POLICY

### 9.1 DYNAMICS_LOUDNESS_POLICY (required fields)
- `loudness_target_mode` = PLATFORM_SAFE | CINEMATIC_SAFE | BROADCAST_SAFE
- `max_peak_policy` (no clipping)
- `dialogue_loudness_priority` (if dialogue exists)
- `music_ducking_policy` (when dialogue enters)
- `dynamic_range_policy` (bounded)
- `silence_policy` (allowed silence windows)
- `notes`

Hard rule:
- clipping is forbidden. any clipping → INVALID.

---

## 10. DIALOGUE INTELLIGIBILITY POLICY

### 10.1 DIALOGUE_INTELLIGIBILITY_POLICY (required fields)
- `dialogue_present` (bool)
- `clarity_gate` (must be intelligible)
- `noise_floor_policy` (keep under control)
- `sibilance_policy` (avoid harshness)
- `forbidden_masking_sources` (music beds, harsh SFX)
- `notes`

If dialogue_present=false, policy must still define how narration/voiceover would be treated (if later added).

---

## 11. CONTINUITY ANCHORS (AUDIO IDENTITY)

### 11.1 CONTINUITY_ANCHORS (required fields)
- `signature_sound_set` (UI ticks, engine hum, world pulse etc.)
- `motif_lock_rules` (theme identity stable)
- `reverb_space_lock` (room/space continuity)
- `tonal_palette_lock` (warm/cool audio color conceptual)
- `variation_budget` (0–10)
- `notes`

Hard rule:
- signature sounds must be consistent across same world/location.

---

## 12. NEGATIVE CONSTRAINTS

### 12.1 NEGATIVE_CONSTRAINTS (required fields)
- `forbid_clipping` (true)
- `forbid_harsh_high_end` (true)
- `forbid_muddy_low_end` (true)
- `forbid_constant_music` (true unless explicitly chosen)
- `forbid_meme_sfx` (true unless genre allows)
- `forbid_unmotivated_stingers` (true)
- `notes`

---

## 13. DELIVERABLE STEMS

### 13.1 DELIVERABLE_STEMS (required fields)
- `stems` (list: DIALOGUE, MUSIC, SFX, AMBIENCE, FOLEY, UI)
- `export_format` (wav/mp3; conceptual)
- `sync_reference` (timecode/markers)
- `naming_policy` (optional)
- `notes`

Hard rule:
- stems must be separable for editing fixes.

---

## 14. QA GATES

### 14.1 QA_GATES (required fields)
- `clipping_gate` (must pass)
- `intelligibility_gate` (dialogue/primary info)
- `balance_gate` (layers not fighting)
- `continuity_gate` (anchors stable)
- `sync_gate` (hooks align to edits)
- `fatigue_gate` (no constant maximum intensity)
- `spec_completeness_gate` (all required fields)

Verdict rules:
- clipping_gate fail → INVALID (CRITICAL).
- sync_gate fail at HIGH severity → PARTIAL/INVALID.

---

## 15. REPAIR PLAN (MANDATORY)

### 15.1 REPAIR_PLAN (required fields)
- `repair_actions_by_failure` (map)
  - clipping → reduce peaks + limiter policy (conceptual) + re-export
  - muddy_mix → carve lows + reduce ambience density
  - dialogue_masked → duck music + reduce SFX
  - music_overuse → add silence windows + reduce density
  - sync_off → align hook points + re-render
- `max_revision_cycles` (int)
- `escalation_rule` (if still failing, revisit edit pacing or cue map)

---

## 16. INPUT ARTIFACTS

### 16.1 INPUT — SOUND_MUSIC_REQUEST
**REQUIRED FIELDS**
- `sm_req_id`
- `timestamp`
- `target_format_ref` (required)
- `editing_montage_spec_ref` (required)
- `tone_profile_ref` (required)
- `platform_constraints_ref` (required)
- `constraints_refs` (required)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 17. OUTPUT ARTIFACTS

### 17.1 OUTPUT — SOUND_MUSIC_PACKAGE
(see model above)

### 17.2 OUTPUT — SOUND_MUSIC_VERDICT
- `sm_req_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 18. CORE OPERATIONS

- OP_01: INGEST_EDIT_SPEC_AND_FORMAT_CONSTRAINTS
- OP_02: BUILD_AUDIO_LAYERS
- OP_03: DEFINE_AMBIENCE_SIGNATURE
- OP_04: DEFINE_SFX_FOLEY_RULES
- OP_05: BUILD_MUSIC_CUE_MAP (themes + rules)
- OP_06: DEFINE_SYNC_HOOKS (edit coupling)
- OP_07: DEFINE_DYNAMICS_LOUDNESS_POLICY
- OP_08: DEFINE_DIALOGUE_INTELLIGIBILITY_POLICY
- OP_09: DEFINE_CONTINUITY_ANCHORS
- OP_10: DEFINE_NEGATIVE_CONSTRAINTS
- OP_11: DEFINE_DELIVERABLE_STEMS
- OP_12: DEFINE_QA_GATES
- OP_13: BUILD_REPAIR_PLAN
- OP_14: RUN_INTEGRITY_CHECKS
- OP_15: EMIT_SOUND_MUSIC_PACKAGE

---

## 19. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- clipping
- dialogue unintelligible when present
- anchors missing (audio identity drift)
- sync hooks contradict edit logic
- deliverable mismatches platform constraints
- constant music density without silence policy

Reaction:
- Verdict INVALID (CRITICAL)
- Emit repair plan:
  - reduce peaks + rebalance
  - add silence windows
  - lock motifs + reverb space
  - re-align hooks
  - simplify layer density

---

## 20. TRACE RULES

- trace_id optional unless pipeline requires traced execution
- if present, propagate into audit log

---

## 21. NON-GOALS
- Does not fully compose tracks
- Does not replace the detailed music realm (12)
- Does not change canon

---

## 22. FINAL STATEMENT

Sound is the invisible architecture of emotion.
Lock the anchors — and the world feels real.

---

**STATUS:** Sound & Music Engine v1.0  
**REALM:** ACTIVE
