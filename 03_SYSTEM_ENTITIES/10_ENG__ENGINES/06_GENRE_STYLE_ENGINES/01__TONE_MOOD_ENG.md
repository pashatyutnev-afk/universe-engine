# TONE & MOOD ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/06_GENRE_STYLE_ENGINES/01__TONE_MOOD_ENG.md
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
UID: UE.ENG.STYLE.TONE.MOOD.001
OWNER: SYSTEM
ROLE: Defines deterministic tone and mood constraints: target emotional direction (tone), felt ambience (mood), allowed tag sets, intensity bounds, and validation gates for consistency across outputs.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Tone & Mood Engine created: tone/mood profile schema, allowed tag sets, intensity bounds, and drift gates."
- REASON: "Style layer needs a base constraint primitive before atmosphere/symbolism/metaphor/sensory."
- IMPACT: "All downstream style/production/narrative outputs can remain consistent in feel without redefining content."
- CHANGE_ID: UE.CHG.2026-01-08.STYLE.TONE.MOOD.001

---

## 0) PURPOSE (LAW)
This engine owns **TONE + MOOD constraints** (style primitives):
- TONE = emotional direction / authorial attitude constraints (what the work “aims to feel like”)
- MOOD = local felt ambience constraints (what it “feels like inside the scene/world window”)

Hard rule:
- This engine outputs constraints/profiles only. It does NOT write plot, characters, or scenes.

Guarantees:
- a reusable TONE_PROFILE exists
- a reusable MOOD_PROFILE exists
- validation gates detect drift and “same-voice” style collapse

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- define story structure, beats, pacing, meaning (NARRATIVE owns)
- define character psychology or motivation (CHARACTER owns)
- define world laws or reality constraints (WORLD owns)
- define event mechanics primitives (EXPRESSION owns)
- define camera/editing/sound implementation specifics (PRODUCTION owns)
- define governance authority/pipeline/audit (GOVERNANCE owns)
- define system identity/state/lifecycle (CORE owns)

Also forbidden:
- “tone = genre label only” without constraints (must be operational)
- “mood = vibes” without tag/intensity bounds

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- STYLE_BRIEF (optional)
- WORLD_LAWSET (optional)
- CHARACTER_CONSTRAINTS (optional)
- EVENT_PACK (optional)
- PROJECT_INTENT (optional)

PRODUCES:
- TONE_PROFILE
- MOOD_PROFILE
- TONE_MOOD_GATES_REPORT

DEPENDS_ON:
- []  (base style primitive; may consume constraints from other families but does not require them)

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/STYLE/TONE_MOOD/
OPTIONAL:
- KB/STYLE/TONE_MOOD (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Tone Tag: controlled vocabulary label for tone direction (e.g., GRIM, HOPEFUL, SATIRIC).
- Mood Tag: controlled vocabulary label for felt ambience (e.g., OMINOUS, TENDER, UNEASY).
- Intensity: 0..100 scalar for strength of tone/mood.
- Drift: deviation from allowed tags/bounds across outputs.
- Clamp: hard constraint limiting tag/intensity to allowed range.

Allowed enums (baseline):
- severity: S0|S1|S2|S3
- scope: GLOBAL|ARC|SCENE_WINDOW

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- defining tone/mood tag sets and constraints
- intensity bounds and consistency rules
- validation gates and drift detection

OUT OF SCOPE (HARD):
- generating scenes or dialogue
- choosing plot outcomes or character decisions
- implementing tone via camera/editing/sound directives (only constraints)

COLLISION RULE:
- If request is “write a scene in this mood” → route to narrative/scene engines (this engine provides profiles only)
- If request is “how to film/edit to achieve this” → route to production engines (this engine outputs constraints)
- If request is “theme/meaning” → route to narrative theme engine
- If request is “emotional resonance aftertaste over time” → route to `03__EMOTIONAL_RESONANCE_ENG`

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: TONE_PROFILE defines allowed tone tags, forbidden tags, and intensity bounds.
R2 (HARD) MUST: MOOD_PROFILE defines mood tags by scope (GLOBAL/ARC/SCENE_WINDOW) with bounds.
R3 (HARD) MUST: every profile includes “anti-style” constraints (what must NOT appear).
R4 (HARD) MUST: gates detect (a) drift (b) same-voice collapse (c) contradiction (tag clash).
R5 (HARD) FORBIDDEN: profiles that are only adjectives without controlled tags and bounds.
R6 (SOFT) SHOULD: provide example anchors (1–3) as references (not content, just descriptors).
R7 (HARD) MUST: if tag conflict exists, profile must include a resolution rule.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: TONE_PROFILE
- MUST:
  - tone_profile_id
  - version
  - scope (GLOBAL|ARC)
  - allowed_tone_tags[] (non-empty)
  - forbidden_tone_tags[] (optional)
  - intensity_target (0..100)
  - intensity_bounds (min,max within 0..100)
  - anti_style_rules[] (non-empty)
  - conflict_rules[] (non-empty)
  - validation_checks[] (non-empty)
- OPTIONAL:
  - anchor_descriptors[] (short phrases)
  - rationale (short)
- VALIDATION:
  - allowed_tone_tags non-empty
  - intensity_bounds within 0..100 and includes intensity_target
  - anti_style_rules non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/STYLE/TONE_MOOD/TONE_PROFILE.md

ARTIFACT: MOOD_PROFILE
- MUST:
  - mood_profile_id
  - version
  - scopes[] (GLOBAL/ARC/SCENE_WINDOW; non-empty)
  - mood_layers[] (non-empty)
  - anti_style_rules[] (non-empty)
  - conflict_rules[] (non-empty)
  - validation_checks[] (non-empty)
- MOOD LAYER (minimum):
  - layer_id
  - scope (GLOBAL|ARC|SCENE_WINDOW)
  - allowed_mood_tags[] (non-empty)
  - forbidden_mood_tags[] (optional)
  - intensity_target (0..100)
  - intensity_bounds (min,max)
  - triggers[] (optional: when to apply)
- VALIDATION:
  - at least one layer for each declared scope
  - each layer has allowed tags + bounds
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/STYLE/TONE_MOOD/MOOD_PROFILE.md

ARTIFACT: TONE_MOOD_GATES_REPORT
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
  - G1_TAG_SET_EMPTY (S0)
  - G2_INTENSITY_OUT_OF_BOUNDS (S0)
  - G3_TAG_CONTRADICTION (S1)
  - G4_DRIFT_OVER_THRESHOLD (S1)
  - G5_SAME_VOICE_STYLE (S2)
- VALIDATION:
  - FAIL if any S0 gate fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/STYLE/TONE_MOOD/TONE_MOOD_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load STYLE_BRIEF and any constraints (world/character/event).
2) Select controlled tag sets:
   - allowed + forbidden
3) Set intensity targets and bounds per scope.
4) Define anti-style rules and conflict resolution rules.
5) Run gates against current project outputs (if any) to detect drift.
6) Emit: tone profile + mood profile + gates report.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: allowed_tone_tags or allowed_mood_tags empty.
- S0-2: intensity bounds invalid or outside 0..100.
- S0-3: profiles contain only prose without controlled tags/bounds.
- S0-4: missing output schemas for produced artifacts.
- S0-5: hidden dependencies (requires other engines but not declared).

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream (typical inputs):
- narrative premise/structure constraints (optional)
- character constraints (optional)
- world laws/epoch context (optional)
- event packs (optional)

Downstream (typical consumers):
- `02__ATMOSPHERE_ENG` (uses tone/mood as base layer)
- `03__EMOTIONAL_RESONANCE_ENG` (targets aftertaste consistent with tone)
- production engines (implement constraints into visuals/audio)
- narrative scene engines (choose scene execution consistent with profiles)

Compatibility notes:
- This engine sets constraints; other engines implement or extend, never overwrite silently.

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family README:
  06_GENRE_STYLE_ENGINES/00__README__GENRE_STYLE_ENGINES.md
- Family template:
  06_GENRE_STYLE_ENGINES/00__TEMPLATE__ENGINE__GENRE_STYLE_ENGINES.md

--- END.

LOCK: OPEN
