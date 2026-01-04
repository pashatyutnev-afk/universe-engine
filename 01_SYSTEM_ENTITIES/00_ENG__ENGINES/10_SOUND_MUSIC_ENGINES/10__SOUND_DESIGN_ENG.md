# 🔊 SOUND DESIGN ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · PRODUCTION ENGINE · SOUND LAYER ARCHITECTURE · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 10__SOUND_DESIGN_ENG.md
- ENGINE_ID: L3-PROD-SOUND-DESIGN-ENGINE-010
- UID: UE.ENT.ENG.PROD.SOUND_DESIGN
- NAME: Sound Design Engine
- CLASS: Sound & Music Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (coherence + masking)
- EDITABLE: true

### ABSOLUTE RULE
> Sound design must reinforce meaning and motion — without masking music, dialogue, or hook.

---

## 1. PURPOSE

Sound Design Engine produces a **SOUND_DESIGN_LAYER_MAP**:
- SFX layer architecture (impacts, risers, whooshes, textures, foley, ambiences)
- timing locks and sync hooks (hits, cuts, reveals)
- world consistency rules (diegetic vs non-diegetic)
- masking avoidance plan (space, register, density)
- deliverability as stems (SFX stems, transitions stems)
- edit-friendly entry/exit points + tail policies

This engine is used for:
- music + SFX hybrid cues
- cinematic transitions
- scene punctuation
- trailer/short-form edits

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define sound layer taxonomy and roles
- Define timing of impacts/risers/transitions
- Define diegetic/non-diegetic constraints
- Define masking avoidance constraints
- Define SFX stem plan + routing
- Define loop/cut-safe behavior
- Define QA gates + repair plan

### OUT-OF-SCOPE (FORBIDDEN)
- composing harmony/melody/groove
- mixing/mastering final loudness (13 engine)
- detailed Foley recording process (outside system; only blueprint)

---

## 3. INPUT / OUTPUT

### 3.1 INPUT — SOUND_DESIGN_REQUEST
Required fields:
- `sd_req_id`
- `timestamp`
- `target_format_ref`
- `tone_profile_ref`
- `scene_ref` (recommended)
- `sync_plan_ref` (recommended)
- `arrangement_plan_ref` (recommended if music exists)
- `music_cue_blueprint_ref` (optional)
- `constraints_refs`
- `world_constraints_refs` (optional; required for diegetic fidelity)
- `dialogue_presence` = NONE | LOW | HIGH (optional; default LOW)
- `trace_id` (optional)

Missing required input → REJECT.

### 3.2 OUTPUT — SOUND_DESIGN_LAYER_MAP
Required fields:
- `sd_id`
- `engine_id`
- `version`
- `status` = DRAFT | PARTIAL | FINAL
- `layer_taxonomy`
- `layer_plan` (per section/time window)
- `diegetic_rules`
- `masking_avoid_plan`
- `sync_hooks`
- `transition_rules`
- `stem_routing_plan`
- `editability_support`
- `qa_gates`
- `repair_plan`

---

## 4. LAYER TAXONOMY

### 4.1 LAYER_TAXONOMY (required fields)
Allowed layer roles:
- AMBIENCE
- TEXTURE
- FOLEY
- WHOOSH
- RISER
- IMPACT
- HITPOINT_PUNCTUATION
- GLITCH/TECH
- SUB_BOOM
- SWELL
- SPARKLES/DETAILS
- DIEGETIC_MUSIC (if applicable)

Fields:
- `allowed_layers` (list)
- `forbidden_layers` (list)
- `signature_sonic_material` (optional)
- `notes`

Hard rule:
- forbidden layers cannot appear unless explicit override.

---

## 5. LAYER PLAN (TIME/SECTION MAPPING)

### 5.1 LAYER_PLAN (required)
For each window (sec_id or timestamp range):
- `window_id`
- `time_range_ref`
- `active_layers` (list)
- `layer_density` (low/med/high)
- `focus_target` = DIALOGUE | MUSIC_HOOK | MUSIC_BED | SFX_ONLY | HYBRID
- `notes`

Hard rule:
- if focus_target = MUSIC_HOOK, masking_avoid_plan must ensure SFX density low or carved.

---

## 6. DIEGETIC RULES (WORLD COHERENCE)

### 6.1 DIEGETIC_RULES (required fields)
- `mode` = DIEGETIC_ONLY | NON_DIEGETIC_ONLY | MIXED_CONTROLLED
- `diegetic_sources` (list; if diegetic)
- `transition_policy` (how to move between diegetic/non)
- `world_consistency_lock` (true/false)
- `notes`

Hard rule:
- MIXED_CONTROLLED must define explicit switch points and reason.

---

## 7. MASKING AVOID PLAN

### 7.1 MASKING_AVOID_PLAN (required fields)
- `priority_signal` = DIALOGUE | MUSIC_HOOK | MUSIC_LEAD | NONE
- `avoid_registers` (low/mid/high)
- `density_ceiling_by_focus` (map focus → ceiling)
- `transient_policy` (avoid spikes near hook words/hits)
- `sidechain_intent` (conceptual; optional)
- `notes`

Hard rule:
- if dialogue_presence = HIGH, priority_signal cannot be NONE.

---

## 8. SYNC HOOKS

### 8.1 SYNC_HOOK (required fields)
- `hook_id`
- `time_ref`
- `type` = HIT | CUT | REVEAL | TRANSITION | DROP | RISE_END
- `layer_roles_triggered` (list)
- `intensity` (0–10)
- `notes`

Hard rule:
- must not exceed intensity ceiling when focus is dialogue or hook.

---

## 9. TRANSITION RULES

### 9.1 TRANSITION_RULES (required fields)
- `riser_policy` (when used)
- `impact_policy` (when used)
- `silence_window_policy` (optional)
- `tail_policy` (reverb tail / hard stop)
- `notes`

Hard rule:
- transitions must align with sync plan if provided.

---

## 10. STEM ROUTING PLAN

### 10.1 STEM_ROUTING_PLAN (required fields)
At minimum:
- `SFX_MAIN`
- `SFX_TRANSITIONS`
Optional:
- `FOLEY`
- `AMBIENCE`
- `IMPACTS`
- `SUB`

Fields:
- `stem_to_layers` (map)
- `mute_safe_policy`
- `delivery_notes`

Hard rule:
- mute_safe_policy must allow removing SFX without breaking timing of music.

---

## 11. EDITABILITY SUPPORT

### 11.1 EDITABILITY_SUPPORT (required fields)
- `entry_points`
- `exit_points`
- `hard_cut_safe_points`
- `loop_points` (optional)
- `tail_policy`
- `notes`

---

## 12. QA GATES

### 12.1 QA_GATES (required fields)
- `coherence_gate` (matches tone/world)
- `masking_gate` (does not mask hook/dialogue)
- `sync_gate` (hooks aligned)
- `density_gate` (no constant high density)
- `stem_gate` (routing complete)
- `edit_gate` (cut-safe points exist)
- `diegetic_gate` (rules respected)

Fail rules:
- masking_gate fail when priority_signal is MUSIC_HOOK → INVALID (HIGH/CRITICAL)
- sync_gate fail → INVALID (HIGH)

---

## 13. REPAIR PLAN (MANDATORY)

### 13.1 REPAIR PLAN (required)
Common repairs:
- masking detected → reduce density, move register, soften transients
- sync off → move hit/impact to exact hook time_ref
- world inconsistency → enforce diegetic mode or remove violating layers
- too noisy → remove textures, keep only impacts/risers
- stems not usable → separate transitions from ambience/foley
- not cut-friendly → add hard_cut_safe_points + tail policy

Include:
- `recheck_gates`
- `max_revision_cycles`

---

## 14. CORE OPERATIONS

- OP_01: INGEST_REQUEST
- OP_02: SET_LAYER_TAXONOMY
- OP_03: BUILD_LAYER_PLAN
- OP_04: SET_DIEGETIC_RULES
- OP_05: BUILD_MASKING_AVOID_PLAN
- OP_06: BUILD_SYNC_HOOKS
- OP_07: BUILD_TRANSITION_RULES
- OP_08: BUILD_STEM_ROUTING_PLAN
- OP_09: BUILD_EDITABILITY_SUPPORT
- OP_10: BUILD_QA_GATES
- OP_11: BUILD_REPAIR_PLAN
- OP_12: EMIT_SOUND_DESIGN_LAYER_MAP

---

## 15. FAILURE CONDITIONS (ENGINE)

CRITICAL:
- tone_profile_ref missing
- target_format_ref missing
- layer_taxonomy empty

Reaction:
- reject (fail-closed)
- request missing inputs

---

## 16. NON-GOALS
- does not compose music
- does not master loudness
- does not create final sound assets; only blueprint

---

## 17. FINAL STATEMENT

Sound design is motion and meaning.
But if it steals focus — it is sabotage.

---

**STATUS:** Sound Design Engine v1.0  
**REALM:** ACTIVE
