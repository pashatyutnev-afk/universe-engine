# ATMOSPHERE ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/06_GENRE_STYLE_ENGINES/02__ATMOSPHERE_ENG.md
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 06_GENRE_STYLE_ENGINES
CLASS: STYLE (L3)
LEVEL: L3
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.STYLE.ATMOSPHERE.001
OWNER: SYSTEM
ROLE: Defines deterministic atmosphere constraints: environmental feel rules, tension air-pressure, texture layers, scene-window modifiers, and validation gates (without owning world laws or production implementation).

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Atmosphere Engine created: atmosphere layer spec, environmental feel rules, modifiers by context, and drift gates."
- REASON: "Tone/mood is not enough; atmosphere needs its own constraint layer before symbolism/sensory detail."
- IMPACT: "Outputs can maintain consistent 'air' and scene feel across narrative and production."
- CHANGE_ID: UE.CHG.2026-01-08.STYLE.ATMOSPHERE.001

---

## 0) PURPOSE (LAW)
This engine owns **ATMOSPHERE constraints**:
- atmosphere is the *felt environment* (air, pressure, texture, threat/comfort field)
- it bridges tone/mood to implementable constraints, without dictating camera/editing
- defines layers and modifiers per scene-window context

Hard rule:
- Atmosphere is a constraint layer, not world physics and not production directives.

Guarantees:
- an ATMOSPHERE_LAYER_SPEC exists (layered, reusable)
- an ATMOSPHERE_RULESET exists (what must/forbidden)
- gates detect atmosphere drift and contradiction with tone/mood

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- define plot, beats, pacing, meaning (NARRATIVE owns)
- define character psyche/motivation (CHARACTER owns)
- define world hard rules/ecology as primary (WORLD owns)
- define event mechanics (EXPRESSION owns)
- define camera/editing/sound specifics (PRODUCTION owns)
- define governance authority/audit (GOVERNANCE owns)
- define system identity/state (CORE owns)

Also forbidden:
- “atmosphere = weather system” (weather/ecology belongs to world engines)
- “atmosphere = lighting/camera recipe” (production owns)

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- TONE_PROFILE (recommended)
- MOOD_PROFILE (recommended)
- WORLD_STRUCTURE_MODEL (optional)
- WORLD_LAWSET (optional)
- SCENE_PACK (optional)
- EVENT_PACK (optional)

PRODUCES:
- ATMOSPHERE_LAYER_SPEC
- ATMOSPHERE_RULESET
- ATMOSPHERE_GATES_REPORT

DEPENDS_ON:
- [06_GENRE_STYLE_ENGINES/01__TONE_MOOD_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/STYLE/ATMOSPHERE/
OPTIONAL:
- KB/STYLE/ATMOSPHERE (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Atmosphere Layer: a named constraint layer (e.g., THREAT_FIELD, COMFORT_FIELD, UNCERTAINTY_FOG).
- Modifier: context-based adjustment of a layer (by location type, time window, relationship context).
- Texture: the qualitative “surface” constraints (rough/smooth, sterile/organic) expressed as controlled tags.
- Pressure: perceived tension/weight; expressed as 0..100 scalar.
- Scene Window: bounded slice of story-time context used for applying modifiers.

Enums (baseline):
- pressure_scale: 0..100
- layer_scope: GLOBAL|ARC|SCENE_WINDOW
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- defining atmosphere layers and their constraints
- defining modifiers per scope/context
- defining atmosphere anti-style rules
- validating consistency vs tone/mood profiles

OUT OF SCOPE (HARD):
- defining world physical climate/ecology (world engines)
- defining production implementation (lighting, camera, sound design specifics)
- defining story meaning or arc logic

COLLISION RULE:
- If request is “what the world climate does” → `04_DOMAIN_WORLD_ENGINES/10__ENVIRONMENT_ECOLOGY_ENG`
- If request is “how to light/edit to get this atmosphere” → production engines (this engine provides constraints only)
- If request is “emotional aftertaste over time” → `03__EMOTIONAL_RESONANCE_ENG`
- If request is “symbolic meaning of atmosphere choices” → symbolism/metaphor engines (04/05)

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: ATMOSPHERE_LAYER_SPEC defines layers with tags + pressure targets + bounds.
R2 (HARD) MUST: each layer declares scope (GLOBAL/ARC/SCENE_WINDOW) and allowed modifiers.
R3 (HARD) MUST: ATMOSPHERE_RULESET includes MUST/FORBIDDEN rules that are implementable as constraints.
R4 (HARD) MUST: atmosphere must be compatible with TONE_PROFILE + MOOD_PROFILE; conflicts require explicit resolution rule.
R5 (HARD) FORBIDDEN: atmosphere outputs that redefine world laws or production recipes.
R6 (SOFT) SHOULD: include “signals” (what indicates the atmosphere is achieved) as constraint checks.
R7 (HARD) MUST: gates report FAIL on S0 contradictions (empty layers, bounds invalid, hard conflict with tone).

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: ATMOSPHERE_LAYER_SPEC
- MUST:
  - spec_id
  - version
  - base_refs (tone_profile_id, mood_profile_id)
  - layers[] (non-empty)
  - modifiers[] (optional)
  - anti_style_rules[] (non-empty)
  - conflict_rules[] (non-empty)
  - validation_checks[] (non-empty)
- LAYER (minimum):
  - layer_id
  - name
  - scope (GLOBAL|ARC|SCENE_WINDOW)
  - texture_tags[] (non-empty; controlled)
  - pressure_target (0..100)
  - pressure_bounds (min,max)
  - intensity_target (0..100)
  - intensity_bounds (min,max)
  - signals[] (optional; observable indicators)
  - forbidden_tags[] (optional)
  - notes
- MODIFIER (minimum):
  - modifier_id
  - applies_to_layer_id
  - context (location/time/relationship/event)
  - delta:
    - pressure_delta (optional)
    - intensity_delta (optional)
    - add_tags[] (optional)
    - forbid_tags[] (optional)
  - bounds (optional)
  - notes
- VALIDATION:
  - layers non-empty
  - bounds within 0..100 and include targets
  - each modifier references existing layer_id
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/STYLE/ATMOSPHERE/ATMOSPHERE_LAYER_SPEC.md

---

ARTIFACT: ATMOSPHERE_RULESET
- MUST:
  - ruleset_id
  - version
  - rules[] (non-empty)
  - invariants[] (optional)
  - checks[] (non-empty)
- RULE (minimum):
  - rule_id
  - type (MUST|FORBIDDEN|ALLOWED)
  - statement (testable constraint)
  - scope (GLOBAL|ARC|SCENE_WINDOW)
  - enforcement_hint (optional; which downstream should apply)
  - severity_if_broken (S0|S1|S2|S3)
- CHECK (minimum):
  - check_id
  - description
  - severity
- VALIDATION:
  - rules non-empty
  - at least one FORBIDDEN rule (anti-style)
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/STYLE/ATMOSPHERE/ATMOSPHERE_RULESET.md

---

ARTIFACT: ATMOSPHERE_GATES_REPORT
- MUST:
  - report_id
  - version
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
- GATE (minimum):
  - gate_id
  - name
  - pass_condition
  - fail_condition
  - severity_if_fail (S0|S1|S2|S3)
- Minimum required gates:
  - G1_LAYER_EMPTY (S0)
  - G2_BOUNDS_INVALID (S0)
  - G3_CONTRADICTS_TONE_MOOD (S1)
  - G4_OVER_MODIFIED_NO_BASE (S1)
  - G5_NON_IMPLEMENTABLE_RULES (S2)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/STYLE/ATMOSPHERE/ATMOSPHERE_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load tone + mood profiles and validate their gates.
2) Define base atmosphere layers:
   - texture tags, pressure/intensity targets and bounds
3) Define modifiers:
   - by location/time/relationship/event context
4) Define anti-style rules and conflict resolution.
5) Run gates:
   - bounds, empties, contradictions vs tone/mood
6) Emit: layer spec + ruleset + gates report.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: layers[] is empty.
- S0-2: any bounds invalid or outside 0..100.
- S0-3: produced artifacts missing required schema fields.
- S0-4: atmosphere defines world laws or production implementation recipes.
- S0-5: hidden dependency on tone/mood (not declared) or conflicts without resolution rule.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- tone/mood engine provides base direction
- world engines may provide context (optional)
- scene/event packs may provide where modifiers apply (optional)

Downstream:
- production engines implement atmosphere constraints (lighting/sound/camera choices)
- narrative scene engines ensure scenes obey atmosphere layer targets
- emotional resonance engine can use atmosphere as input signal layer
- symbolism/metaphor engines may reference atmosphere tags as carriers (but cannot override them silently)

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family README:
  06_GENRE_STYLE_ENGINES/00__README__GENRE_STYLE_ENGINES.md
- Family template:
  06_GENRE_STYLE_ENGINES/00__TEMPLATE__ENGINE__GENRE_STYLE_ENGINES.md

--- END.

LOCK: OPEN
