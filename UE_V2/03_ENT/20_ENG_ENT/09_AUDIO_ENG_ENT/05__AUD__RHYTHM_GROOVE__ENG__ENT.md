# RHYTHM / GROOVE ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/05__RHYTHM_GROOVE_ENG.md
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 09_SOUND_MUSIC_ENGINES
CLASS: SOUND (L3)
LEVEL: L3
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.SOUND.RHYTHM.GROOVE.001
OWNER: SYSTEM
ROLE: Defines deterministic rhythmic language: groove palettes, meter/tempo policies, rhythmic density rules, syncopation constraints, and validation gates. Produces rhythm specs consumable by arrangement and performance engines without owning editing montage rhythm.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Rhythm/Groove Engine created: groove palette schema, tempo/meter policy, density rules, and gates."
- REASON: "Music needs controlled rhythmic identity separate from video editing rhythm."
- IMPACT: "Groove becomes reusable and auditable across cues and songs."
- CHANGE_ID: UE.CHG.2026-01-08.SOUND.RHYTHM.GROOVE.001

---

## 0) PURPOSE (LAW)
This engine owns **RHYTHM / GROOVE primitives**:
- defines groove palette (feel categories and patterns as constraints)
- defines meter and tempo policies (ranges, allowed meters)
- defines rhythmic density rules (sparse vs busy)
- defines syncopation constraints (allowed/forbidden)
- emits gates against incoherent groove and drift

Hard rule:
- This engine defines music rhythm, not editing montage rhythm and not performance execution details.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- define cut rhythm for video editing (editing/montage engine)
- define song macro structure (song structure engine)
- define chord harmony (harmony engine)
- define melody hooks (melody engine)
- define lyrics (lyrics engine)
- define instrument arrangement specifics (arrangement engine)
- define vocal performance (vocal engine)
- do mix/master (mix/master engine)

FORBIDDEN:
- “groove” described only as “fast” without meter/tempo/density rules.

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- CUE_STRUCTURE_PLAN (optional)
- THEME_MOTIF_BIBLE (optional)
- RHYTHM_REQUEST (optional)

PRODUCES:
- GROOVE_PALETTE
- TEMPO_METER_POLICY
- RHYTHMIC_DENSITY_PROFILE
- RHYTHM_GATES_REPORT

DEPENDS_ON:
- [] (can be used independently; integrates downstream with structure/harmony)

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/MUSIC/RHYTHM/
OPTIONAL:
- KB/MUSIC/RHYTHM (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Groove: rhythmic feel constrained by pattern templates and density rules.
- Meter: time signature constraint (e.g., 4/4, 3/4, 7/8).
- Tempo Policy: allowable BPM ranges and tempo-change rules.
- Density: proxy 0..100 for rhythmic event frequency.
- Syncopation: off-beat emphasis policy (bounded).
- Swing: timing feel (STRAIGHT|SWING_LIGHT|SWING_HEAVY).

Enums (baseline):
- meter: 4_4|3_4|6_8|7_8|5_4|CUSTOM
- swing: STRAIGHT|SWING_LIGHT|SWING_HEAVY
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- groove palette and rhythm constraints
- tempo/meter policies and change rules
- density and syncopation constraints
- validation gates for rhythm coherence

OUT OF SCOPE (HARD):
- editing montage rhythm (video)
- instrument arrangement details (which instrument plays what)
- performance microtiming beyond swing category

COLLISION RULE:
- If request is “edit cut rhythm” → `08_KNOWLEDGE_PRODUCTION_ENGINES/07__EDITING_MONTAGE_ENG`
- If request is “drum pattern arrangement for kit” → arrangement engine (this engine outputs palette constraints)
- If request is “performance timing nuance beyond swing” → vocal/performance engine (09)

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: GROOVE_PALETTE defines allowed groove templates with constraints.
R2 (HARD) MUST: TEMPO_METER_POLICY defines allowed meters and BPM bounds.
R3 (HARD) MUST: RHYTHMIC_DENSITY_PROFILE defines density targets and bounds per scope/section.
R4 (HARD) MUST: include syncopation policy (allowed/forbidden ranges).
R5 (HARD) FORBIDDEN: rhythm outputs that are only adjectives without meter/tempo/density.
R6 (SOFT) SHOULD: include “tempo modulation rules” (ramps, drops) bounded.
R7 (HARD) MUST: gates detect missing palette/policy and invalid bounds.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: GROOVE_PALETTE
- MUST:
  - palette_id
  - version
  - grooves[] (non-empty)
  - swing_default (STRAIGHT|SWING_LIGHT|SWING_HEAVY)
  - checks[] (non-empty)
- GROOVE (minimum):
  - groove_id
  - name
  - meter (enum)
  - feel_tags[] (optional)
  - density_target (0..100)
  - syncopation_target (0..100)
  - allowed_variations[] (non-empty)
  - forbidden_variations[] (optional)
  - when_to_use (testable)
- VALIDATION:
  - grooves non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/RHYTHM/GROOVE_PALETTE.md

---

ARTIFACT: TEMPO_METER_POLICY
- MUST:
  - policy_id
  - version
  - allowed_meters[] (non-empty)
  - bpm_bounds (min,max)
  - tempo_change_rules[] (optional)
  - forbidden_ranges[] (optional)
  - checks[] (non-empty)
- TEMPO CHANGE RULE (optional):
  - rule_id
  - type (RAMP|STEP|DROP|HOLD)
  - max_delta_bpm (optional)
  - when_allowed (testable)
- VALIDATION:
  - allowed_meters non-empty
  - bpm bounds valid
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/RHYTHM/TEMPO_METER_POLICY.md

---

ARTIFACT: RHYTHMIC_DENSITY_PROFILE
- MUST:
  - density_profile_id
  - version
  - density_targets[] (non-empty)
  - bounds (min,max)
  - anti_patterns[] (non-empty)
  - checks[] (non-empty)
- DENSITY TARGET (minimum):
  - scope (GLOBAL|SECTION)
  - section_ref (optional)
  - target (0..100)
  - bounds (min,max)
  - notes
- VALIDATION:
  - density_targets non-empty
  - bounds valid
  - anti_patterns non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/RHYTHM/RHYTHMIC_DENSITY_PROFILE.md

---

ARTIFACT: RHYTHM_GATES_REPORT
- MUST:
  - report_id
  - version
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
- Minimum required gates:
  - G1_GROOVE_PALETTE_EMPTY (S0)
  - G2_TEMPO_METER_POLICY_MISSING (S0)
  - G3_BPM_BOUNDS_INVALID (S0)
  - G4_DENSITY_PROFILE_EMPTY (S0)
  - G5_VAGUE_RHYTHM (S1)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/RHYTHM/RHYTHM_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load optional structure plan and rhythm request.
2) Define tempo/meter policy (allowed meters + BPM bounds).
3) Define groove palette (templates with density and syncopation targets).
4) Define density profile (targets per section/scope).
5) Run gates and emit artifacts.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: groove palette empty.
- S0-2: tempo/meter policy missing or invalid bounds.
- S0-3: density profile empty.
- S0-4: produced artifacts missing schemas/storage targets.
- S0-5: outputs are vague adjectives without concrete constraints.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- structure plan can map grooves to sections (optional)
- composition motifs can align with groove identity (optional)

Downstream:
- arrangement engine assigns groove patterns to instruments
- vocal performance engine aligns phrasing to groove constraints
- mix/master engine later finalizes audio

Boundary:
- editing montage rhythm is separate (video editing engine).

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Video editing boundary:
  08_KNOWLEDGE_PRODUCTION_ENGINES/07__EDITING_MONTAGE_ENG.md
- Family template:
  09_SOUND_MUSIC_ENGINES/00__TEMPLATE__ENGINE__SOUND_MUSIC_ENGINES.md
- Family README:
  09_SOUND_MUSIC_ENGINES/00__README__SOUND_MUSIC_ENGINES.md

--- END.

LOCK: OPEN
