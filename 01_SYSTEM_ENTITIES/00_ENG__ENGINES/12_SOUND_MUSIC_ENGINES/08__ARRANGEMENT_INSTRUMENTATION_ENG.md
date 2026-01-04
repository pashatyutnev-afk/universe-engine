# 🎻 ARRANGEMENT & INSTRUMENTATION ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · PRODUCTION ENGINE · ORCHESTRATION PLAN · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 08__ARRANGEMENT_INSTRUMENTATION_ENG.md
- ENGINE_ID: L3-PROD-ARRANGEMENT-INSTRUMENTATION-ENGINE-008
- UID: UE.ENT.ENG.PROD.ARRANGEMENT_INSTRUMENTATION
- NAME: Arrangement & Instrumentation Engine
- CLASS: Sound & Music Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (clarity + hook spotlight)
- EDITABLE: true

### ABSOLUTE RULE
> If arrangement does not protect the hook and clarity, the cue becomes mud.

---

## 1. PURPOSE

Arrangement & Instrumentation Engine converts:
- Composition blueprint (01)
- Song blueprint (02)
- Harmony blueprint (03)
- Hook blueprint (04)
- Groove blueprint (05)
(+ lyrics if vocal)

into an **ARRANGEMENT_PLAN**:
- instrument palette and locks
- role allocation per section
- density and dynamics curve
- hook spotlight strategy
- stem mapping plan (for edit + mix)
- transition orchestration rules
- register management (avoid masking)
- deliverability + QA gates

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define instrument palette and palette locks
- Allocate musical roles (bass/harmony/melody/pads/fx) to instruments
- Define section-by-section layering and density
- Define hook spotlight (space, register, timbre)
- Define automation intent (builds, drops, risers; conceptually)
- Define stem plan mapping (consistent with composition engine)
- Define arrangement QA + repair plan

### OUT-OF-SCOPE (FORBIDDEN)
- actual audio rendering and sound choice details (10 engine may define sound design layer map)
- vocal performance micro-direction (09 engine)
- mixing/mastering (13 engine)

---

## 3. INPUT / OUTPUT

### 3.1 INPUT — ARRANGEMENT_REQUEST
Required fields:
- `ai_req_id`
- `timestamp`
- `music_cue_blueprint_ref` (01) OR `song_blueprint_ref` (02)
- `harmony_blueprint_ref` (03)
- `hook_blueprint_ref` (04) (required if hook exists)
- `groove_blueprint_ref` (05)
- `tone_profile_ref`
- `constraints_refs`
- `stem_plan_ref` (from 01) (required)
- `vocal_mode` (optional)
- `lyrics_artifact_ref` (optional; required if vocal final)
- `trace_id` (optional)

Missing required input → REJECT.

### 3.2 OUTPUT — ARRANGEMENT_PLAN
Required fields:
- `arrangement_id`
- `engine_id`
- `version`
- `status` = DRAFT | PARTIAL | FINAL
- `instrument_palette`
- `role_allocation_map`
- `section_layer_map`
- `density_curve`
- `register_management_plan`
- `hook_spotlight_plan`
- `transition_orchestration_rules`
- `stem_mapping`
- `editability_support`
- `qa_gates`
- `repair_plan`

---

## 4. INSTRUMENT PALETTE

### 4.1 INSTRUMENT_PALETTE (required fields)
- `palette_lock` (true/false)
- `allowed_groups` (list; e.g., drums, bass, pads, strings, synth lead)
- `preferred_instruments` (optional list)
- `forbidden_instruments` (list)
- `signature_timbre` (optional; what makes identity)
- `notes`

Hard rule:
- palette_lock true requires justification for any new instrument introduced later.

---

## 5. ROLE ALLOCATION MAP

### 5.1 ROLE ENUM
- DRUMS
- BASS
- HARMONY
- MELODY
- HOOK_LEAD
- PADS
- ARP_MOTION
- FX_TRANSITIONS
- VOCALS_MAIN
- VOCALS_BACKING
- TEXTURE_NOISE
- IMPACTS

### 5.2 ROLE_ALLOCATION_MAP (required fields)
- `role_to_instrument_group` (map)
- `redundancy_policy` (what roles may have doubles)
- `mute_safe_policy` (what can be muted without collapse)
- `notes`

Hard rule:
- HOOK_LEAD must have exclusive space policy (register/timbre) if hook exists.

---

## 6. SECTION LAYER MAP

### 6.1 SECTION_LAYER (required per section)
- `sec_id`
- `sec_type`
- `active_layers` (list of roles)
- `layer_density` (low/med/high)
- `dynamic_target` (0–10)
- `hook_visibility_target` (0–10)
- `texture_notes`
- `automation_intent` (optional)

Hard rule:
- hook sections must have hook_visibility_target >= 7 by default unless intentionally hidden and tagged.

---

## 7. DENSITY CURVE

### 7.1 DENSITY_CURVE (required fields)
- `curve_points` (sec_id or timestamp → density low/med/high)
- `peak_density_limit` (optional)
- `fatigue_rule` (no constant high density unless tagged)
- `dropout_strategy` (where elements drop for contrast)

---

## 8. REGISTER MANAGEMENT PLAN (ANTI-MASKING)

### 8.1 REGISTER_MANAGEMENT_PLAN (required fields)
- `register_focus_per_role` (low/mid/high)
- `masking_avoid_rules` (e.g., “no pads in hook register”)
- `frequency_space_policy` (conceptual)
- `arrangement_eq_intent` (conceptual; not mix)
- `notes`

Hard rule:
- HOOK_LEAD register must not be crowded by harmony/pads.

---

## 9. HOOK SPOTLIGHT PLAN

### 9.1 HOOK_SPOTLIGHT_PLAN (required if hook exists)
- `spotlight_method` (space/timbre/dropout/doubling/call-response)
- `pre_hook_clear_rule` (reduce density before hook)
- `hook_support_layers` (what supports it)
- `hook_mask_forbidden_layers` (what must be quiet/absent)
- `hook_repeat_variation_strategy` (how repeats vary without drift)
- `notes`

---

## 10. TRANSITION ORCHESTRATION RULES

### 10.1 TRANSITION_RULES (required fields)
- `build_elements` (risers/snare builds/automation)
- `impact_elements` (downbeats, hits)
- `fill_policy` (from groove, enforced here)
- `silence_windows` (if needed)
- `notes`

Hard rule:
- transitions must not steal focus from hook entry.

---

## 11. STEM MAPPING

### 11.1 STEM_MAPPING (required fields)
Must map arrangement roles to composition stems:
- MAIN
- DRUMS
- BASS
- HARMONY
- MELODY
- PADS
- FX
- ALT_MINIMAL

Fields:
- `stem_to_roles` (map)
- `render_priority` (what must be rendered first)
- `mute_safe_test_cases` (list)
- `notes`

Hard rule:
- ALT_MINIMAL must preserve timing + hook recognizability (if hook exists).

---

## 12. EDITABILITY SUPPORT

### 12.1 EDITABILITY_SUPPORT (required fields)
- `entry_points` (from groove/composition)
- `exit_points`
- `tail_policy`
- `section_loop_points` (optional)
- `stinger_version_rule` (optional)
- `notes`

---

## 13. QA GATES

### 13.1 QA_GATES (required fields)
- `palette_gate` (palette respects locks)
- `role_gate` (roles allocated, no missing core)
- `hook_gate` (hook protected and audible)
- `masking_gate` (register plan avoids conflicts)
- `density_gate` (matches energy curve)
- `stem_gate` (stem mapping complete)
- `edit_gate` (entry/exit points supported)

Fail rules:
- hook_gate fail → INVALID (HIGH/CRITICAL)
- stem_gate fail → PARTIAL/INVALID depending on usage

---

## 14. REPAIR PLAN (MANDATORY)

### 14.1 REPAIR PLAN (required)
Common repairs:
- muddy mix (arrangement-level) → reduce overlapping roles + enforce register spacing
- hook not audible → dropout competing layers + timbre contrast
- too dense → remove layers in verses, reserve peak for chorus/drop
- boring → add motion layer (arp/pulse) within budget
- stems not useful → rebalance stem-to-role mapping + add ALT_MINIMAL rules

Include:
- `recheck_gates`
- `max_revision_cycles`

---

## 15. CORE OPERATIONS

- OP_01: INGEST_REQUEST
- OP_02: LOAD_UPSTREAM_BLUEPRINTS
- OP_03: DEFINE_INSTRUMENT_PALETTE
- OP_04: ALLOCATE_ROLES
- OP_05: BUILD_SECTION_LAYER_MAP
- OP_06: BUILD_DENSITY_CURVE
- OP_07: BUILD_REGISTER_MANAGEMENT_PLAN
- OP_08: BUILD_HOOK_SPOTLIGHT_PLAN (if hook)
- OP_09: BUILD_TRANSITION_RULES
- OP_10: BUILD_STEM_MAPPING
- OP_11: BUILD_EDITABILITY_SUPPORT
- OP_12: BUILD_QA_GATES
- OP_13: BUILD_REPAIR_PLAN
- OP_14: EMIT_ARRANGEMENT_PLAN

---

## 16. FAILURE CONDITIONS (ENGINE)

CRITICAL:
- stem_plan_ref missing
- harmony/groove refs missing
- hook exists but hook_blueprint_ref missing

Reaction:
- reject (fail-closed)
- request missing refs

---

## 17. NON-GOALS
- does not mix/master
- does not choose final samples/presets
- does not direct vocal performance micro-details

---

## 18. FINAL STATEMENT

Arrangement is the spotlight operator.
If it points the light wrong — the audience hears nothing.

---

**STATUS:** Arrangement & Instrumentation Engine v1.0  
**REALM:** ACTIVE
