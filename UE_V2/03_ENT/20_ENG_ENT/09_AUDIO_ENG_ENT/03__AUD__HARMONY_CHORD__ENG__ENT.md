# HARMONY / CHORD ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/03__HARMONY_CHORD_ENG.md
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
UID: UE.ENG.SOUND.HARMONY.CHORD.001
OWNER: SYSTEM
ROLE: Defines deterministic harmonic language: chord vocabulary, progression rules, modulation constraints, tension-resolution mapping, and validation gates. Produces harmony specs consumable by melody/arrangement engines without owning mix/master or production placement.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Harmony/Chord Engine created: chord lexicon schema, progression rules, modulation policy, and gates."
- REASON: "Song structure needs a harmonic system to be executed consistently across cues."
- IMPACT: "Harmonic identity becomes reusable, auditable, and bounded."
- CHANGE_ID: UE.CHG.2026-01-08.SOUND.HARMONY.CHORD.001

---

## 0) PURPOSE (LAW)
This engine owns **HARMONIC LANGUAGE constraints**:
- chord vocabulary (allowed chord types, extensions, voicing constraints as tags)
- progression rules (allowed moves, forbidden moves, cadence policies)
- modulation constraints aligned to tonal direction policy
- tension-resolution mapping (how harmony contributes to tension curves)
- gates to prevent incoherent or contradictory harmonic choices

Hard rule:
- This engine defines harmonic rules, not melodies, arrangements, or mix/master.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- define macro structure (song structure engine)
- define hook melodies (melody/hook engine)
- define groove/rhythm patterns (rhythm/groove engine)
- define lyrics (lyrics engine)
- define instrumentation arrangement (arrangement engine)
- do production placement/sync (production audio engine)
- do mix/master implementation (mix/master engine)

FORBIDDEN:
- “harmony” described as “sad chords” without chord vocabulary and progression rules.

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- TONAL_DIRECTION_POLICY (recommended)
- THEME_MOTIF_BIBLE (optional)
- CUE_STRUCTURE_PLAN (optional)
- HARMONY_REQUEST (optional)

PRODUCES:
- CHORD_LEXICON
- PROGRESSION_RULESET
- MODULATION_POLICY
- HARMONIC_TENSION_MAP
- HARMONY_GATES_REPORT

DEPENDS_ON:
- [09_SOUND_MUSIC_ENGINES/01__MUSIC_COMPOSITION_ENG]
(soft) [09_SOUND_MUSIC_ENGINES/02__SONG_STRUCTURE_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/MUSIC/HARMONY/
OPTIONAL:
- KB/MUSIC/HARMONY (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Chord Lexicon: allowed chord types and extensions + constraints.
- Progression: chord-to-chord movement with allowed/forbidden transitions.
- Cadence Policy: closure patterns allowed (authentic/plagal/deceptive/etc.).
- Modulation: tonal center change policy aligned to tonal direction policy.
- Harmonic Tension: proxy mapping of harmonic density/instability to 0..100 tension.
- Voicing Tag: abstract voicing constraint (OPEN|CLOSE|CLUSTER|SPREAD) without full notation.

Enums (baseline):
- chord_quality: MAJ|MIN|DIM|AUG|SUS|DOM
- cadence_type: AUTHENTIC|PLAGAL|DECEPTIVE|HALF|NONE
- voicing_tag: OPEN|CLOSE|CLUSTER|SPREAD
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- harmonic vocabulary and rulesets
- modulation policy and allowed moves
- tension mapping support for structure plans
- gates for consistency and contradiction prevention

OUT OF SCOPE (HARD):
- melody generation and hook design
- arrangement/instrument voicing details (beyond tags)
- mix/master
- production placement/sync

COLLISION RULE:
- If request is “write melody on top of chords” → `04__MELODY_HOOK_ENG`
- If request is “arrange voicings for instruments” → `08__ARRANGEMENT_INSTRUMENTATION_ENG`
- If request is “mix/master levels” → `13__MIX_MASTER_ENG`
- If request is “place cue to scene timeline” → `12__MUSIC_TO_SCENE_ENG` / production layer

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: CHORD_LEXICON defines allowed chord qualities/extensions and forbidden chords.
R2 (HARD) MUST: PROGRESSION_RULESET defines allowed transitions and forbidden transitions (non-empty).
R3 (HARD) MUST: MODULATION_POLICY aligns with TONAL_DIRECTION_POLICY when provided.
R4 (HARD) MUST: HARMONIC_TENSION_MAP supports section tension targets (if structure plan exists).
R5 (HARD) FORBIDDEN: rulesets that are only adjectives or “use jazz chords”.
R6 (SOFT) SHOULD: include cadence policies per cue type (tension build vs release).
R7 (HARD) MUST: gates detect missing lexicon, empty transitions, and modulation contradictions.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: CHORD_LEXICON
- MUST:
  - lexicon_id
  - version
  - allowed_chords[] (non-empty)
  - forbidden_chords[] (optional)
  - voicing_tags_allowed[] (non-empty)
  - extension_policy (required)
  - checks[] (non-empty)
- ALLOWED CHORD (minimum):
  - chord_id
  - quality (MAJ|MIN|DIM|AUG|SUS|DOM)
  - allowed_extensions[] (optional: 7,9,11,13)
  - functional_role (TONIC|DOMINANT|SUBDOMINANT|COLOR|AMBIGUOUS)
  - when_to_use (testable)
  - when_forbidden (optional)
- EXTENSION POLICY (minimum):
  - max_extension (e.g., 13)
  - disallow_stack_conditions (optional)
- VALIDATION:
  - allowed_chords non-empty
  - voicing_tags_allowed non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/HARMONY/CHORD_LEXICON.md

---

ARTIFACT: PROGRESSION_RULESET
- MUST:
  - ruleset_id
  - version
  - allowed_transitions[] (non-empty)
  - forbidden_transitions[] (non-empty)
  - cadence_policies[] (non-empty)
  - checks[] (non-empty)
- TRANSITION (minimum):
  - transition_id
  - from_role (TONIC|DOMINANT|SUBDOMINANT|COLOR|AMBIGUOUS)
  - to_role (TONIC|DOMINANT|SUBDOMINANT|COLOR|AMBIGUOUS)
  - allowed (bool)
  - conditions (optional)
  - severity_if_broken (S0|S1|S2|S3)
- CADENCE POLICY (minimum):
  - policy_id
  - cadence_type (AUTHENTIC|PLAGAL|DECEPTIVE|HALF|NONE)
  - when_to_use (testable)
  - when_forbidden (optional)
- VALIDATION:
  - allowed_transitions non-empty
  - forbidden_transitions non-empty
  - cadence_policies non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/HARMONY/PROGRESSION_RULESET.md

---

ARTIFACT: MODULATION_POLICY
- MUST:
  - policy_id
  - version
  - allowed_modulations[] (non-empty)
  - forbidden_modulations[] (optional)
  - triggers[] (optional)
  - checks[] (non-empty)
- ALLOWED MODULATION (minimum):
  - modulation_id
  - from_center (tag)
  - to_center (tag)
  - method (PIVOT|DIRECT|CHROMATIC|TEXTURE_SHIFT)
  - when_allowed (testable)
  - severity_if_broken (S0|S1|S2|S3)
- VALIDATION:
  - allowed_modulations non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/HARMONY/MODULATION_POLICY.md

---

ARTIFACT: HARMONIC_TENSION_MAP
- MUST:
  - tension_map_id
  - version
  - mapping_rules[] (non-empty)
  - section_overrides[] (optional)
  - checks[] (non-empty)
- MAPPING RULE (minimum):
  - rule_id
  - tension_band (e.g., 0-20, 20-50, 50-80, 80-100)
  - harmonic_tools_allowed[] (non-empty; e.g., "modal mixture", "secondary dominants")
  - harmonic_tools_forbidden[] (optional)
  - cadence_policy_ref (optional)
- SECTION OVERRIDE (optional):
  - section_id
  - target_tension (0..100)
  - allowed_tools[] (optional)
- VALIDATION:
  - mapping_rules non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/HARMONY/HARMONIC_TENSION_MAP.md

---

ARTIFACT: HARMONY_GATES_REPORT
- MUST:
  - report_id
  - version
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
- Minimum required gates:
  - G1_LEXICON_EMPTY (S0)
  - G2_TRANSITIONS_EMPTY (S0)
  - G3_CADENCE_POLICY_EMPTY (S0)
  - G4_MODULATION_CONTRADICTION (S1)
  - G5_VAGUE_RULES (S1)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/HARMONY/HARMONY_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load tonal direction policy and optional structure plan.
2) Define chord lexicon (qualities, extensions, voicing tags).
3) Define progression ruleset (allowed/forbidden transitions + cadence policies).
4) Define modulation policy aligned to tonal direction.
5) Define harmonic tension map to support section tension curves.
6) Run gates and emit artifacts.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: chord lexicon empty.
- S0-2: progression transitions empty.
- S0-3: cadence policies missing.
- S0-4: produced artifacts missing schemas/storage targets.
- S0-5: rules are vague adjectives without structure.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- composition defines tonal direction and motif identity
- structure plan provides section tension targets (optional)

Downstream:
- melody/hook engine writes melodies consistent with harmonic rules
- rhythm/groove engine integrates harmonic rhythm timing constraints (optional)
- arrangement engine realizes voicings and instrumentation
- mix/master engine finalizes audio (later stage)

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family template:
  09_SOUND_MUSIC_ENGINES/00__TEMPLATE__ENGINE__SOUND_MUSIC_ENGINES.md
- Family README:
  09_SOUND_MUSIC_ENGINES/00__README__SOUND_MUSIC_ENGINES.md

--- END.

LOCK: OPEN
