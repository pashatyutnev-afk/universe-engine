# ✂️ EDITING & MONTAGE ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · PRODUCTION ENGINE · CUT LOGIC · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 07__EDITING_MONTAGE_ENG.md
- ENGINE_ID: L3-PROD-EDITING-MONTAGE-ENGINE-007
- UID: UE.ENT.ENG.PROD.EDITING_MONTAGE
- NAME: Editing & Montage Engine
- CLASS: Knowledge Production Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (rhythm + continuity)
- EDITABLE: true

### ABSOLUTE RULE
> Editing is time control. If time control fails, attention dies.

---

## 1. PURPOSE

Editing & Montage Engine defines **how footage becomes a finished sequence**:
- cut logic (what motivates cuts)
- rhythm and pacing rules (beat alignment)
- montage structure types
- continuity repair rules (axis, match, time compression)
- transition policies
- B-roll/insert policies
- retention gates (no dead zones, no drift)
- deliverable assembly specification

It produces:
- **EDITING_MONTAGE_SPEC**
- cut map / montage map and repair actions

This engine prevents “random cuts” and “slow dead sections”.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define edit pacing (cut density and variation)
- Define cut motivations (action, gaze, sound, info)
- Define montage pattern rules (training, travel, buildup)
- Define continuity repair rules (match cuts, bridges, re-establish)
- Define B-roll/insert usage policy
- Define transition types and constraints
- Define retention gates and dead-zone elimination
- Emit deliverable assembly plan (timeline spec)

### OUT-OF-SCOPE (FORBIDDEN)
- Sound design/music composition (Sound & Music Engine)
- Camera/lighting/style decisions (upstream)
- Changing canon facts
- Infinite re-cutting without redesign (must escalate)

---

## 3. EDITING SPEC MODEL

### 3.1 Output — EDITING_MONTAGE_SPEC (required fields)
- `ems_id`
- `target_format_ref` (short/series/youtube/game; required)
- `source_timeline_ref` (required)
- `pacing_rhythm_policy` (required)
- `cut_logic_rules` (required)
- `montage_models` (required)
- `transition_policy` (required)
- `continuity_repair_rules` (required)
- `broll_insert_policy` (required)
- `retention_gates` (required)
- `deliverable_assembly` (required)
- `qa_gates` (required)
- `repair_plan` (required)
- `integrity_report` (issues + fixes)
- `trace_id` (optional)

Missing any required field → REJECT.

---

## 4. PACING & RHYTHM POLICY

### 4.1 PACING_RHYTHM_POLICY (required fields)
- `pace_mode` = FAST | MEDIUM | SLOW_CONTROLLED | VARIABLE_CONTROLLED
- `cut_density_target` (cuts per minute conceptual)
- `max_dead_zone_seconds` (format dependent)
- `beat_alignment_policy` (align cuts to beats/meaning)
- `tempo_curve` (optional: build-up/relief)
- `allowed_slowdowns` (bounded list)
- `notes`

Hard rule:
- dead zones beyond max without payoff → INVALID.

---

## 5. CUT LOGIC RULES (MOTIVATION)

### 5.1 CUT_LOGIC_RULES (required fields)
- `primary_cut_motivators` (list)
  - ACTION_MATCH
  - GAZE_MATCH
  - INFORMATION_REVEAL
  - SOUND_CUE
  - EMOTION_SHIFT
  - VISUAL_CONTRAST
- `forbidden_cut_patterns` (list)
  - random jump cut without reason
  - cut on nothing
  - “talking head” too long without inserts (if retention requires)
- `hold_rules` (when to hold a shot)
- `cut_on_motion_policy` (optional)
- `notes`

Hard rule:
- every cut must have an explicit motivator.

---

## 6. MONTAGE MODELS

### 6.1 MONTAGE_MODEL (required fields)
- `montage_id`
- `type` = TRAINING | TRAVEL | BUILDUP | DISCOVERY | WAR | WORKFLOW | MEMORY
- `purpose`
- `shot_unit_rules` (what kinds of shots are allowed)
- `duration_budget_seconds` (min/max)
- `rhythm_pattern` (e.g., accelerating)
- `transition_pattern` (cut/match/flash etc. bounded)
- `notes`

Hard rule:
- montage must deliver meaning (progress/contrast) not filler.

---

## 7. TRANSITION POLICY

### 7.1 TRANSITION_POLICY (required fields)
- `allowed_transitions` (CUT, MATCH_CUT, DISSOLVE_LIMITED, WHIP_IF_ALLOWED)
- `forbidden_transitions` (random wipes, heavy effects unless style allows)
- `transition_usage_budget` (how many non-cuts allowed)
- `re_hook_rule_after_transition` (must add info)
- `notes`

Hard rule:
- non-cut transitions must be justified by mood/meaning.

---

## 8. CONTINUITY REPAIR RULES

### 8.1 CONTINUITY_REPAIR_RULES (required fields)
- `axis_repair` (re-establishing shot, neutral bridge)
- `time_compression_rules` (ellipsis allowed, must preserve causality)
- `match_rules` (action match, eyeline, graphic match)
- `geography_clarity_rule` (must show space before complex cutting)
- `continuity_anchors_ref` (from camera/lighting/style)
- `notes`

Hard rule:
- if continuity breaks, repair must be specified (do not ignore).

---

## 9. B-ROLL / INSERT POLICY

### 9.1 BROLL_INSERT_POLICY (required fields)
- `broll_allowed` (bool)
- `insert_types_allowed` (hands, objects, environment, UI, text cards if allowed)
- `broll_purposes` (cover cuts, add proof, add texture, re-hook attention)
- `max_broll_density` (bounded)
- `forbidden_broll` (generic unrelated filler)
- `notes`

Hard rule:
- every B-roll must have a purpose.

---

## 10. RETENTION GATES (HARD)

### 10.1 RETENTION_GATES (required fields)
- `no_dead_zones_gate` (max seconds rule)
- `value_change_interval_gate` (viewer must receive change regularly)
- `open_loop_touch_gate` (if longform format)
- `peak_protection_gate` (no CTA or filler during peaks)
- `information_pacing_gate` (avoid overload)
- `format_specific_gates` (short vs youtube vs series)

Verdict rules:
- if no_dead_zones_gate fails → INVALID.
- if peak_protection_gate fails → PARTIAL/INVALID depending on severity.

---

## 11. DELIVERABLE ASSEMBLY

### 11.1 DELIVERABLE_ASSEMBLY (required fields)
- `final_duration_seconds` (required)
- `fps` (required)
- `aspect_ratio` (required)
- `resolution_target` (required)
- `caption_placeholder_policy` (space reserved or baked)
- `export_policy` (codec conceptual)
- `chapter_markers_policy` (if youtube)
- `notes`

Hard rule:
- deliverable must match platform constraints.

---

## 12. QA GATES

### 12.1 QA_GATES (required fields)
- `continuity_gate` (axis, anchors, geography)
- `rhythm_gate` (pace meets spec)
- `audio_sync_gate` (if audio exists)
- `visual_artifact_gate` (cuts hide artifacts, not amplify)
- `retention_gate` (dead zones removed)
- `spec_completeness_gate` (all required fields)

---

## 13. REPAIR PLAN (MANDATORY)

### 13.1 REPAIR_PLAN (required fields)
- `repair_actions_by_failure` (map)
  - dead_zone → cut/insert value beat
  - continuity_break → add bridge shot / reorder
  - pace_too_fast → extend holds on meaningful shots
  - pace_too_slow → cut redundancies, add inserts
  - confusing geography → add establishing
- `max_revision_cycles` (int)
- `escalation_rule` (if still failing, redesign upstream timeline/spec)

Hard rule:
- after max cycles, escalate to redesign. No infinite polishing.

---

## 14. INPUT ARTIFACTS

### 14.1 INPUT — EDITING_MONTAGE_REQUEST
**REQUIRED FIELDS**
- `em_req_id`
- `timestamp`
- `target_format_ref` (required)
- `video_generation_spec_ref` (required) OR `shot_timeline_ref` (required)
- `tone_profile_ref` (required)
- `platform_constraints_ref` (required)
- `constraints_refs` (required)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 15. OUTPUT ARTIFACTS

### 15.1 OUTPUT — EDITING_MONTAGE_SPEC
(see model above)

### 15.2 OUTPUT — EDITING_MONTAGE_VERDICT
- `em_req_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 16. CORE OPERATIONS

- OP_01: INGEST_TARGET_FORMAT_AND_TIMELINE
- OP_02: SET_PACING_RHYTHM_POLICY
- OP_03: DEFINE_CUT_LOGIC_RULES
- OP_04: DEFINE_MONTAGE_MODELS
- OP_05: DEFINE_TRANSITION_POLICY
- OP_06: DEFINE_CONTINUITY_REPAIR_RULES
- OP_07: DEFINE_BROLL_INSERT_POLICY
- OP_08: DEFINE_RETENTION_GATES
- OP_09: DEFINE_DELIVERABLE_ASSEMBLY
- OP_10: DEFINE_QA_GATES
- OP_11: BUILD_REPAIR_PLAN
- OP_12: RUN_INTEGRITY_CHECKS
- OP_13: EMIT_EDITING_MONTAGE_SPEC

---

## 17. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- dead zones remain
- cuts have no motivator
- continuity breaks with no repair rule
- transitions exceed budget without justification
- deliverable mismatches platform constraints
- infinite revision loop (no escalation)

Reaction:
- Verdict INVALID (CRITICAL)
- Emit repair plan:
  - cut redundancy
  - add inserts/bridges
  - lock pace targets
  - simplify transitions
  - redesign timeline if overloaded

---

## 18. TRACE RULES

- trace_id optional unless pipeline requires traced execution
- if present, propagate into sound planning + audit logging

---

## 19. NON-GOALS
- Does not compose music
- Does not design SFX (only sync constraints)
- Does not change canon

---

## 20. FINAL STATEMENT

Editing is meaning per second.
If a second adds nothing — remove it.

---

**STATUS:** Editing & Montage Engine v1.0  
**REALM:** ACTIVE
