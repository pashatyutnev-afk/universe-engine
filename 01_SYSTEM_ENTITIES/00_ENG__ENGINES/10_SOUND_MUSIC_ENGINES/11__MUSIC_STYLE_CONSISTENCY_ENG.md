# 🎛️ MUSIC STYLE CONSISTENCY ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · PRODUCTION ENGINE · STYLE FINGERPRINT CONTROL · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 11__MUSIC_STYLE_CONSISTENCY_ENG.md
- ENGINE_ID: L3-PROD-MUSIC-STYLE-CONSISTENCY-ENGINE-011
- UID: UE.ENT.ENG.PROD.MUSIC_STYLE_CONSISTENCY
- NAME: Music Style Consistency Engine
- CLASS: Sound & Music Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (style drift)
- EDITABLE: true

### ABSOLUTE RULE
> If style fingerprint drifts, the world loses identity.

---

## 1. PURPOSE

Music Style Consistency Engine defines and enforces a **STYLE_FINGERPRINT**:
- harmonic color norms
- groove feel norms
- hook DNA boundaries
- instrumentation palette locks
- texture and sound design allowed ranges
- motif usage rules
- season/series coherence constraints (if multi-episode)

It outputs:
- `STYLE_FINGERPRINT`
- `STYLE_COMPLIANCE_REPORT`
- `STYLE_DRIFT_ALERTS` (when used in validation pass)

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define style fingerprint templates
- Lock palette and signature traits
- Define allowable variation budgets per dimension
- Validate new cue outputs against fingerprint
- Detect drift (harmonic, rhythmic, timbral, structural)
- Define approval gates and repair recommendations

### OUT-OF-SCOPE (FORBIDDEN)
- composing new music directly
- mixing/mastering choices
- narrative decisions (domain engines)

---

## 3. INPUT / OUTPUT

### 3.1 INPUT — STYLE_CONSISTENCY_REQUEST
Required fields:
- `msc_req_id`
- `timestamp`
- `style_scope` = PROJECT | SERIES | SEASON | CHARACTER_THEME | LOCATION_THEME (required)
- `tone_profile_ref`
- `reference_cues_refs` (optional but recommended)
- `constraints_refs`
- `variation_intent` (why variation is allowed)
- `trace_id` (optional)

Optional inputs (for validation):
- `candidate_blueprints_refs` (arrangement/harmony/hook/groove)
- `candidate_audio_ref` (optional; outside system)

Missing required scope/tone → REJECT.

### 3.2 OUTPUT — STYLE_FINGERPRINT_PACKAGE
Required fields:
- `style_id`
- `engine_id`
- `version`
- `status` = DRAFT | PARTIAL | FINAL
- `style_scope`
- `style_fingerprint`
- `style_locks`
- `allowed_variation_budgets`
- `compliance_gates`
- `drift_detectors`
- `repair_plan`

---

## 4. STYLE FINGERPRINT (CORE)

### 4.1 STYLE_FINGERPRINT (required fields)
- `harmonic_color_norms` (modes, cadence types, dissonance budget)
- `groove_norms` (feel, swing range, pocket placement)
- `tempo_norms` (tempo bands)
- `structure_norms` (hook deadline norms, section patterns)
- `hook_norms` (hook DNA boundaries)
- `instrumentation_norms` (palette, signature timbres)
- `texture_sfx_norms` (allowed SFX density if hybrid)
- `motif_rules` (if motifs exist)
- `notes`

Hard rule:
- each norm must include a tolerance range or discrete allowed values.

---

## 5. STYLE LOCKS

### 5.1 STYLE_LOCKS (required fields)
- `palette_lock` (true/false)
- `hook_identity_lock` (true/false)
- `cadence_lock` (optional)
- `groove_feel_lock` (optional)
- `signature_elements` (list: “the things that must stay”)
- `forbidden_changes` (list)
- `override_policy` (how to override locks)
- `notes`

Hard rule:
- override_policy must define who/what can approve overrides (governance layer reference).

---

## 6. ALLOWED VARIATION BUDGETS

### 6.1 VARIATION DIMENSIONS
- HARMONY
- RHYTHM
- HOOK_DNA
- INSTRUMENTATION
- TEXTURE_SFX
- STRUCTURE
- TEMPO

### 6.2 ALLOWED_VARIATION_BUDGETS (required fields)
- `budget_by_dimension` (map dimension → 0–10)
- `max_simultaneous_dimensions` (how many can vary at once)
- `safe_variation_pairs` (optional)
- `forbidden_variation_pairs` (optional)
- `notes`

Hard rule:
- HOOK_DNA budget must be low if hook_identity_lock = true.

---

## 7. COMPLIANCE GATES

### 7.1 COMPLIANCE_GATES (required fields)
- `harmonic_gate`
- `groove_gate`
- `hook_gate`
- `palette_gate`
- `structure_gate`
- `texture_gate` (if hybrid)
- `motif_gate` (if motifs)
- `overall_pass_rule`

Fail rules:
- hook_gate fail when hook_identity_lock = true → INVALID (HIGH/CRITICAL)
- palette_gate fail when palette_lock = true → INVALID (HIGH)

---

## 8. DRIFT DETECTORS

### 8.1 DRIFT_DETECTORS (required fields)
- `harmonic_drift_detector` (what triggers drift)
- `rhythm_drift_detector`
- `timbre_drift_detector`
- `structure_drift_detector`
- `hook_drift_detector`
- `motif_drift_detector` (if motifs)

Each detector includes:
- `signal`
- `threshold`
- `action` (warn/reject/request-override)

Hard rule:
- thresholds must be consistent with variation budgets.

---

## 9. VALIDATION MODE (OPTIONAL)

If candidate blueprints are provided, emit a compliance report:

### 9.1 STYLE_COMPLIANCE_REPORT (required fields)
- `candidate_id`
- `dimension_scores` (0–10 per dimension)
- `violations` (list)
- `override_needed` (bool)
- `recommendations`
- `status` = PASS | WARN | FAIL

Hard rule:
- FAIL if any locked dimension violation occurs without override.

---

## 10. QA GATES (ENGINE INTERNAL)

### 10.1 QA_GATES (required fields)
- `fingerprint_gate` (all norms defined with tolerance)
- `lock_gate` (locks consistent and enforceable)
- `budget_gate` (budgets defined and realistic)
- `detector_gate` (detectors match budgets)
- `governance_gate` (override policy references authority)

Fail rules:
- governance_gate fail → PARTIAL (cannot enforce overrides)
- fingerprint_gate fail → INVALID

---

## 11. REPAIR PLAN (MANDATORY)

### 11.1 REPAIR PLAN (required)
Common repairs:
- style too vague → add signature_elements + tighten tolerances
- style too strict → increase budgets but keep signature locked
- frequent drift → lower simultaneous variation; lock more
- palette problems → enforce palette_lock or clarify allowed instruments
- hook drift → lower HOOK_DNA budget; add hook identity constraints

Include:
- `recheck_gates`
- `max_revision_cycles`

---

## 12. CORE OPERATIONS

- OP_01: INGEST_REQUEST
- OP_02: BUILD_STYLE_FINGERPRINT
- OP_03: SET_STYLE_LOCKS
- OP_04: SET_VARIATION_BUDGETS
- OP_05: DEFINE_COMPLIANCE_GATES
- OP_06: DEFINE_DRIFT_DETECTORS
- OP_07: RUN_VALIDATION_MODE (optional)
- OP_08: BUILD_ENGINE_QA_GATES
- OP_09: BUILD_REPAIR_PLAN
- OP_10: EMIT_STYLE_FINGERPRINT_PACKAGE

---

## 13. FAILURE CONDITIONS (ENGINE)

CRITICAL:
- style_scope missing
- tone_profile_ref missing
- tolerances not defined (fingerprint not enforceable)

Reaction:
- reject (fail-closed)
- request missing enforceable norms

---

## 14. NON-GOALS
- does not compose music
- does not mix/master
- does not replace narrative canon

---

## 15. FINAL STATEMENT

Style consistency is world continuity.
Break it — and the universe cracks.

---

**STATUS:** Music Style Consistency Engine v1.0  
**REALM:** ACTIVE
