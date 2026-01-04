# 🌫️ ATMOSPHERE ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · STYLE ENGINE · ENVIRONMENTAL FRAME · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 02__ATMOSPHERE_ENG.md
- ENGINE_ID: L3-STYLE-ATMOSPHERE-ENGINE-002
- UID: UE.ENT.ENG.STYLE.ATMOSPHERE
- NAME: Atmosphere Engine
- CLASS: Style Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (atmospheric coherence)
- EDITABLE: true

### ABSOLUTE RULE
> Atmosphere is not decoration — it is pressure that shapes perception and choice.

---

## 1. PURPOSE

Atmosphere Engine defines the **ambient frame** in which events occur:
- environmental conditions
- social climate
- threat presence
- sensory background
- spatial texture

It produces:
- **ATMOSPHERE_LAYER_MAP**
- atmosphere-to-scene constraints
- environmental pressure rules (how atmosphere affects actions)
- consistency checks (no “different world” vibe without reason)

This engine prevents “generic backgrounds” and inconsistent vibe swaps.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Define atmosphere schema and controlled layer system
- Build layered atmosphere profile per arc/sequence/scene type
- Specify how atmosphere modifies perception and decision-making
- Define consistency constraints across locations and time windows
- Map atmosphere to sensory palettes and social cues
- Provide repair guidance for atmospheric drift

### OUT-OF-SCOPE (FORBIDDEN)
- Plot decisions and causality
- Canon authority decisions
- Full prose generation (only constraints + maps)

---

## 3. ATMOSPHERE MODEL

### 3.1 Atmosphere Map — ATMOSPHERE_LAYER_MAP (required fields)
- `am_id`
- `scope` = WORLD | REGION | ARC | SEQUENCE | SCENE_TYPE
- `base_atmosphere` (layer bundle)
- `variants` (optional list of layer bundles keyed by location/time)
- `pressure_rules` (how layers affect behavior)
- `consistency_rules` (hard/soft)
- `drift_detection_rules`
- `integrity_report` (issues + fixes)
- `trace_id` (optional)

Missing any required field → REJECT.

### 3.2 Layer Bundle (required layers)
A layer bundle must contain:
- `environment_layer` (weather/temperature/light/air/space)
- `spatial_layer` (scale, density, geometry, motion)
- `social_layer` (norms, surveillance, crowd mood, class tension)
- `threat_layer` (visible/invisible danger, proximity, intensity)
- `sensory_palette` (sound/texture/smell/light motifs)
- `symbolic_weather` (optional: metaphoric atmospheric echo; must align with tone)

Missing any required layer → REJECT.

### 3.3 Pressure Rules (required)
- `perception_bias` (what people notice first)
- `movement_friction` (what slows/complicates actions)
- `communication_noise` (misunderstanding risk)
- `risk_multiplier` (how dangerous choices become)

---

## 4. CONTROLLED VOCABULARY (STANDARD)

### 4.1 Environmental Tags
- CLEAN
- TOXIC
- HUMID
- DRY
- COLD
- HOT
- DIM
- HARSH_LIGHT
- FOGGY
- DUSTY
- STATIC_CHARGED
- SILENT
- LOUD

### 4.2 Social Climate Tags
- PARANOID
- OPPRESSIVE
- FESTIVE
- DECAYING
- RITUALIZED
- LAWLESS
- SURVEILLED
- CLASS_TENSE
- COMMUNAL
- ISOLATED

### 4.3 Threat Tags
- NONE
- DISTANT
- PRESENT
- IMMINENT
- OVERWHELMING

---

## 5. HARD RULES (ATMOSPHERIC COHERENCE)

- Atmosphere must support tone:
  - tone profile incompatible layer bundles must be rejected or justified.
- Threat layer must match stakes windows:
  - “calm spa vibe” during high-stakes chase requires explicit contrast intent.
- Location changes must cause atmosphere transition:
  - transitions require “bridge” cues (travel, doorway, cut, time jump).
- Sensory palette must be bounded:
  - no random motif spam; motifs repeat with purpose.

---

## 6. INPUT ARTIFACTS

### 6.1 INPUT — ATMOSPHERE_REQUEST
**REQUIRED FIELDS**
- `at_req_id`
- `timestamp`
- `tone_profile_ref` (required)
- `mood_curve_ref` (recommended)
- `world_package_ref` (recommended)
- `constraints_refs` (required)
- `location_set_ref` (optional: list of key locations)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 7. OUTPUT ARTIFACTS

### 7.1 OUTPUT — ATMOSPHERE_LAYER_MAP
(see model above)

### 7.2 OUTPUT — ATMOSPHERE_VERDICT
- `at_req_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 8. CORE OPERATIONS

- OP_01: INGEST_TONE_MOOD_WORLD_CONSTRAINTS
- OP_02: DEFINE_BASE_LAYER_BUNDLE (default frame)
- OP_03: DEFINE_VARIANTS_BY_LOCATION_TIME (optional)
- OP_04: DEFINE_PRESSURE_RULES (perception/friction/noise/risk)
- OP_05: DEFINE_CONSISTENCY_AND_TRANSITION_RULES
- OP_06: DEFINE_DRIFT_DETECTION_RULES
- OP_07: EMIT_ATMOSPHERE_LAYER_MAP

---

## 9. DRIFT DETECTION RULES

Hard drift (INVALID):
- threat layer contradicts declared stakes without intent
- social climate flips with no transition window
- sensory palette motifs change completely without bridge

Soft drift (PARTIAL):
- minor texture mismatch (light, noise) that can be corrected

Repair suggestions must include:
- add transition cues
- constrain motifs
- align threat layer to stakes
- adjust social climate framing

---

## 10. DEPENDENCIES

### REQUIRED
- Tone Profile
- Constraints refs

### OPTIONAL
- Mood curve
- World package (ecology, tech level, geography)

### FORBIDDEN
- Atmosphere with missing layers
- Unjustified atmosphere resets (“new genre suddenly”)
- Motif overload with no repetition logic

---

## 11. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- Layer bundles missing required layers
- Atmosphere contradicts tone profile with no justification
- Transition rules absent for multi-location narratives
- Threat layer mismatched to stakes windows repeatedly

Reaction:
- Verdict INVALID (CRITICAL)
- Emit repair plan:
  - rebuild layer bundles
  - add transitions
  - align layers to tone/mood
  - reduce motif noise

---

## 12. TRACE RULES

- trace_id optional unless pipeline requires traced execution
- if present, propagate into resonance/symbolism/metaphor/sensory engines

---

## 13. NON-GOALS
- Does not write prose descriptions
- Does not decide plot
- Does not set canon facts

---

## 14. FINAL STATEMENT

Atmosphere is systemic pressure.
Define it — and every scene breathes the same world.

---

**STATUS:** Atmosphere Engine v1.0  
**REALM:** ACTIVE
