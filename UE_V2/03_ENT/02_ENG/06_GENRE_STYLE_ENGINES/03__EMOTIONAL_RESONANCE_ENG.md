# EMOTIONAL RESONANCE ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/06_GENRE_STYLE_ENGINES/03__EMOTIONAL_RESONANCE_ENG.md
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
UID: UE.ENG.STYLE.EMOTIONAL.RESONANCE.001
OWNER: SYSTEM
ROLE: Defines deterministic emotional resonance constraints: intended aftertaste, echo patterns, emotional arc-of-feel (not plot), persistence windows, and validation gates against tone/mood/atmosphere drift.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Emotional Resonance Engine created: resonance profile schema, echo rules, persistence windows, and drift gates."
- REASON: "Tone/mood/atmosphere define local feel; resonance defines what lingers after scenes/arcs."
- IMPACT: "Outputs can target a consistent emotional aftertaste without rewriting story content."
- CHANGE_ID: UE.CHG.2026-01-08.STYLE.EMOTIONAL.RESONANCE.001

---

## 0) PURPOSE (LAW)
This engine owns **EMOTIONAL RESONANCE constraints**:
- emotional aftertaste targets (“what remains in the viewer/reader”)
- echo patterns (recurring emotional motifs)
- persistence windows (how long a feeling should linger across segments)
- resonance rules that constrain how scenes should land (without writing scenes)

Hard rule:
- Resonance here is NOT narrative theme/meaning and NOT pacing mechanics. It is a constraint target for “what lingers”.

Guarantees:
- a RESONANCE_PROFILE exists (targets + windows)
- an ECHO_RULESET exists (how resonance repeats/returns)
- gates detect mismatch vs tone/mood/atmosphere

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- define story structure, beats, or meaning (NARRATIVE owns)
- define character psychology/motivation (CHARACTER owns)
- define world rules or constraints (WORLD owns)
- define event mechanics (EXPRESSION owns)
- define pacing/rhythm as story-time cadence (pacing engine)
- define production implementation (music cues, editing timing, camera language) — production engines may consume this as constraint

Also forbidden:
- replacing Theme & Meaning (narrative) with “resonance meaning statements”
- defining montage rhythm (production) as resonance

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- TONE_PROFILE (recommended)
- MOOD_PROFILE (recommended)
- ATMOSPHERE_LAYER_SPEC (recommended)
- EVENT_PACK (optional)
- SCENE_PACK (optional)

PRODUCES:
- RESONANCE_PROFILE
- ECHO_RULESET
- RESONANCE_GATES_REPORT

DEPENDS_ON:
- [06_GENRE_STYLE_ENGINES/01__TONE_MOOD_ENG, 06_GENRE_STYLE_ENGINES/02__ATMOSPHERE_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/STYLE/RESONANCE/
OPTIONAL:
- KB/STYLE/RESONANCE (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Resonance Target: named emotional aftertaste goal (e.g., “uneasy hope”, “cold awe”).
- Persistence Window: span across which resonance must remain noticeable (SCENE_WINDOW/ARC/EPISODE).
- Echo: recurrence of a resonance target with controlled variation.
- Resonance Spike: allowed peak moments where intensity rises sharply.
- Drift: deviation from declared resonance targets.

Enums (baseline):
- window_scope: SCENE_WINDOW|ARC|EPISODE|SEASON
- intensity: 0..100
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- aftertaste targets and intensity bounds
- persistence windows
- echo rules and controlled recurrence
- gates and drift detection

OUT OF SCOPE (HARD):
- plot logic or story structure
- pacing timing decisions (how long a scene lasts, beat duration)
- soundtrack composition or sound design implementation (production)
- symbolism/metaphor content (handled by symbolism/metaphor engines)

COLLISION RULE:
- If request is “what does it mean” → narrative Theme & Meaning engine
- If request is “how to pace to achieve it” → narrative Pacing & Rhythm engine
- If request is “what music to write” → sound/music engines (this engine gives constraints only)
- If request is “symbol carriers” → symbolism/metaphor engines (04/05)

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: RESONANCE_PROFILE defines targets with intensity targets and bounds and persistence windows.
R2 (HARD) MUST: ECHO_RULESET defines how and when targets recur (frequency and variation bounds).
R3 (HARD) MUST: include anti-style rules: forbidden resonance targets and forbidden spikes.
R4 (HARD) MUST: gates validate compatibility with tone/mood/atmosphere (no direct contradictions).
R5 (HARD) FORBIDDEN: resonance defined as “theme statement” or plot outcome.
R6 (SOFT) SHOULD: define allowed spike moments with explicit clamp rules.
R7 (HARD) MUST: if multiple targets exist, profile includes conflict resolution ordering.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: RESONANCE_PROFILE
- MUST:
  - resonance_profile_id
  - version
  - base_refs (tone_profile_id, mood_profile_id, atmosphere_spec_id)
  - targets[] (non-empty)
  - persistence_windows[] (non-empty)
  - spike_rules[] (optional)
  - anti_style_rules[] (non-empty)
  - conflict_rules[] (non-empty)
  - validation_checks[] (non-empty)
- TARGET (minimum):
  - target_id
  - name
  - descriptors[] (optional short words)
  - intensity_target (0..100)
  - intensity_bounds (min,max)
  - allowed_carriers[] (optional: symbol/metaphor/sensory tags)
  - forbidden_carriers[] (optional)
  - notes
- PERSISTENCE WINDOW (minimum):
  - window_id
  - scope (SCENE_WINDOW|ARC|EPISODE|SEASON)
  - applies_to_target_ids[] (non-empty)
  - min_presence (0..100)
  - max_presence (0..100)
  - fade_rule (testable)
- SPIKE RULE (minimum):
  - spike_id
  - target_id
  - trigger (optional)
  - max_spike_intensity (0..100)
  - recovery_bounds (min,max)
- VALIDATION:
  - targets non-empty
  - intensity bounds valid and include targets
  - persistence windows reference existing target_ids
  - anti_style_rules non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/STYLE/RESONANCE/RESONANCE_PROFILE.md

---

ARTIFACT: ECHO_RULESET
- MUST:
  - echo_ruleset_id
  - version
  - echoes[] (non-empty)
  - rules[] (non-empty)
  - checks[] (non-empty)
- ECHO (minimum):
  - echo_id
  - target_id
  - recurrence_scope (SCENE_WINDOW|ARC|EPISODE|SEASON)
  - frequency (e.g., "1 per arc", "every 3 scenes") (testable)
  - variation_bounds (e.g., intensity ±10)
  - allowed_forms[] (optional: “quiet echo”, “sharp echo”)
  - forbidden_forms[] (optional)
- RULE (minimum):
  - rule_id
  - type (MUST|FORBIDDEN|ALLOWED)
  - statement (testable)
  - severity_if_broken (S0|S1|S2|S3)
- VALIDATION:
  - echoes reference existing target_ids
  - at least one FORBIDDEN rule
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/STYLE/RESONANCE/ECHO_RULESET.md

---

ARTIFACT: RESONANCE_GATES_REPORT
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
  - G1_TARGETS_EMPTY (S0)
  - G2_BOUNDS_INVALID (S0)
  - G3_CONTRADICTS_TONE_MOOD_ATMOS (S1)
  - G4_PERSISTENCE_UNDEFINED (S1)
  - G5_ECHO_OVERLOAD_OR_NONE (S2)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/STYLE/RESONANCE/RESONANCE_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load tone/mood/atmosphere and validate their gates.
2) Define resonance targets (aftertaste) with intensity targets/bounds.
3) Define persistence windows (where/how long each target must remain).
4) Define echo rules (recurrence + variation bounds).
5) Add anti-style and conflict rules (ordering / priority).
6) Run gates (contradictions, missing windows, invalid bounds).
7) Emit: resonance profile + echo ruleset + gates report.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: targets[] empty.
- S0-2: any intensity bounds invalid or outside 0..100.
- S0-3: persistence windows missing or referencing unknown target ids.
- S0-4: produced artifacts missing required schema fields.
- S0-5: hidden dependency on tone/mood/atmosphere not declared.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- tone/mood provides direction
- atmosphere provides felt environment constraints
- optional event/scene packs provide where to apply resonance windows

Downstream:
- narrative engines can plan scene outcomes to satisfy resonance windows (without changing plot logic)
- production engines can implement resonance via performance/music/edit choices (outside this engine)
- symbolism/metaphor engines can supply carriers aligned with allowed_carriers constraints

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family README:
  06_GENRE_STYLE_ENGINES/00__README__GENRE_STYLE_ENGINES.md
- Family template:
  06_GENRE_STYLE_ENGINES/00__TEMPLATE__ENGINE__GENRE_STYLE_ENGINES.md

--- END.

LOCK: OPEN
