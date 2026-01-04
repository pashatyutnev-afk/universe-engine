# 🎬 MUSIC TO SCENE ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · PRODUCTION ENGINE · SCENE SYNC CONTROL · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 12__MUSIC_TO_SCENE_ENG.md
- ENGINE_ID: L3-PROD-MUSIC-TO-SCENE-ENGINE-012
- UID: UE.ENT.ENG.PROD.MUSIC_TO_SCENE
- NAME: Music to Scene Engine
- CLASS: Sound & Music Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (sync integrity)
- EDITABLE: true

### ABSOLUTE RULE
> If hitpoints and emotional beats are not mapped, music cannot lock to picture.

---

## 1. PURPOSE

Music to Scene Engine produces a **SCENE_SYNC_BLUEPRINT**:
- hitpoints map (cuts, reveals, actions, camera beats)
- emotional beat map (tension curve across time)
- dialogue-safe windows (if dialogue present)
- cue start/end and tail strategy
- cutdown mapping rules (15s/30s/60s)
- handoff spec to music engines (structure/harmony/hook/groove)
- compliance gates for sync and editability

This engine is the synchronization brain between video edit and music design.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Map hitpoints and classify them
- Define emotional beat curve and priorities
- Define dialogue-safe windows and masking constraints
- Define cue boundaries (start, end, tail)
- Define cutdown targets and mapping strategy
- Define sync constraints for groove/harmony/hook placement
- Define QA gates + repair plan

### OUT-OF-SCOPE (FORBIDDEN)
- composing melody/harmony directly
- sound design layer creation (10 engine)
- mixing/mastering (13 engine)
- narrative writing (domain engines)

---

## 3. INPUT / OUTPUT

### 3.1 INPUT — SCENE_SYNC_REQUEST
Required fields:
- `ms_req_id`
- `timestamp`
- `scene_duration`
- `scene_ref` (optional but recommended)
- `edit_timeline_ref` (optional)
- `dialogue_presence` = NONE | LOW | HIGH (required)
- `tone_profile_ref`
- `target_format_ref` (short/longform/etc.)
- `constraints_refs`
- `trace_id` (optional)

Optional:
- `hitpoints_provided` (list)
- `cutdown_targets` (list: 15/30/60 etc.)

Missing required input → REJECT.

### 3.2 OUTPUT — SCENE_SYNC_BLUEPRINT
Required fields:
- `sync_id`
- `engine_id`
- `version`
- `status` = DRAFT | PARTIAL | FINAL
- `hitpoints_map`
- `emotional_beat_map`
- `dialogue_safe_windows`
- `cue_boundary_plan`
- `cutdown_map`
- `handoff_constraints`
- `qa_gates`
- `repair_plan`

---

## 4. HITPOINTS MAP

### 4.1 HITPOINT (required fields)
- `hp_id`
- `time_ref` (timestamp or frame)
- `type` = CUT | ACTION | REVEAL | LOOK | IMPACT | CAMERA_MOVE | TITLE | TRANSITION
- `priority` = LOW | MED | HIGH | CRITICAL
- `strength` (0–10)
- `notes`

### 4.2 HITPOINTS_MAP (required)
- `hitpoints` (list)
- `cluster_rules` (how close hitpoints are grouped)
- `max_hitpoints_per_10s` (limit)
- `notes`

Hard rule:
- CRITICAL hitpoints must be explicitly handled in handoff_constraints.

---

## 5. EMOTIONAL BEAT MAP

### 5.1 EMOTIONAL_BEAT (required fields)
- `eb_id`
- `time_range_ref`
- `emotion_label` (e.g., awe, tension, triumph)
- `intensity_target` (0–10)
- `direction` (build/hold/release)
- `notes`

### 5.2 EMOTIONAL_BEAT_MAP (required)
- `beats` (ordered list)
- `peak_points` (timestamps)
- `release_points` (timestamps)
- `notes`

Hard rule:
- must include at least one peak and one release unless scene is static and tagged.

---

## 6. DIALOGUE SAFE WINDOWS

Required when dialogue_presence != NONE.

### 6.1 DIALOGUE_SAFE_WINDOW (required fields)
- `window_id`
- `time_range_ref`
- `strictness` (0–10)
- `priority_signal` = DIALOGUE
- `music_allowed_level` (0–10)
- `sfx_allowed_level` (0–10)
- `notes`

Hard rule:
- dialogue_presence HIGH requires at least one strict window.

---

## 7. CUE BOUNDARY PLAN

### 7.1 CUE_BOUNDARY_PLAN (required fields)
- `cue_start_rule` (cold/open/fade-in)
- `cue_end_rule` (hardstop/tail/fade)
- `tail_policy` (seconds or conceptual)
- `stinger_policy` (optional)
- `loop_policy` (optional)
- `notes`

Hard rule:
- end rule must respect last CRITICAL hitpoint timing.

---

## 8. CUTDOWN MAP

### 8.1 CUTDOWN_MAP (required if cutdowns requested)
For each cutdown target:
- `target_duration`
- `keep_segments` (time ranges)
- `drop_segments` (time ranges)
- `hook_presence_rule` (must appear / optional)
- `hitpoints_preservation_rule`
- `notes`

Hard rule:
- if hook_priority HIGH, cutdowns must preserve at least one hook instance.

---

## 9. HANDOFF CONSTRAINTS (TO MUSIC ENGINES)

### 9.1 HANDOFF_CONSTRAINTS (required fields)
- `hook_deadline_ref` (time)
- `hitpoint_alignment_targets` (list of hp_id)
- `energy_curve_targets` (map time → intensity)
- `dialogue_masking_constraints` (link to safe windows)
- `structure_constraints` (allowed section types and durations)
- `groove_constraints` (pocket strictness, transitions)
- `harmony_constraints` (cadence at key hitpoints)
- `notes`

Hard rule:
- any CRITICAL hitpoint must map to an alignment target or explicit exception.

---

## 10. QA GATES

### 10.1 QA_GATES (required fields)
- `hitpoints_gate` (hitpoints defined, prioritized)
- `emotion_gate` (beat map coherent)
- `dialogue_gate` (safe windows defined if needed)
- `boundary_gate` (start/end rules defined)
- `cutdown_gate` (if required)
- `handoff_gate` (constraints actionable)

Fail rules:
- handoff_gate fail → INVALID (cannot build music)
- hitpoints_gate fail when edit_timeline exists → INVALID

---

## 11. REPAIR PLAN (MANDATORY)

### 11.1 REPAIR PLAN (required)
Common repairs:
- too many hitpoints → cluster and reduce, preserve only CRITICAL/HIGH
- emotional curve flat → add peak/release beats
- dialogue fighting music → enlarge safe windows and tighten masking constraints
- cue end misses moment → adjust boundary plan + tail policy
- cutdowns break hook → re-map keep segments and enforce hook presence

Include:
- `recheck_gates`
- `max_revision_cycles`

---

## 12. CORE OPERATIONS

- OP_01: INGEST_REQUEST
- OP_02: BUILD_HITPOINTS_MAP (or validate provided)
- OP_03: BUILD_EMOTIONAL_BEAT_MAP
- OP_04: BUILD_DIALOGUE_SAFE_WINDOWS (if needed)
- OP_05: BUILD_CUE_BOUNDARY_PLAN
- OP_06: BUILD_CUTDOWN_MAP (if required)
- OP_07: BUILD_HANDOFF_CONSTRAINTS
- OP_08: BUILD_QA_GATES
- OP_09: BUILD_REPAIR_PLAN
- OP_10: EMIT_SCENE_SYNC_BLUEPRINT

---

## 13. FAILURE CONDITIONS (ENGINE)

CRITICAL:
- dialogue_presence missing
- scene_duration missing
- tone_profile_ref missing

Reaction:
- reject (fail-closed)
- request missing inputs

---

## 14. NON-GOALS
- does not compose music
- does not create sound design assets
- does not master audio

---

## 15. FINAL STATEMENT

Picture is the ruler.
If music doesn’t measure to it — it fails.

---

**STATUS:** Music to Scene Engine v1.0  
**REALM:** ACTIVE
