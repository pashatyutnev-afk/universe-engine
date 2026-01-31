# MELODY / HOOK ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/04__MELODY_HOOK_ENG.md
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
UID: UE.ENG.SOUND.MELODY.HOOK.001
OWNER: SYSTEM
ROLE: Defines deterministic melody/hook outputs: motif-to-melody realization rules, hook candidates, contour constraints, range policies, repetition/variation laws, and validation gates. Produces melody specs consumable by arrangement/vocal engines without owning lyrics or mix/master.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Melody/Hook Engine created: hook candidate schema, contour/range rules, repetition/variation policy, and gates."
- REASON: "Themes/motifs require melodic realization to become memorable and reusable."
- IMPACT: "Hooks can be generated consistently and validated against motif identity and harmony constraints."
- CHANGE_ID: UE.CHG.2026-01-08.SOUND.MELODY.HOOK.001

---

## 0) PURPOSE (LAW)
This engine owns **MELODY / HOOK primitives**:
- translates motifs/themes into melody candidates
- defines contour constraints and range policies
- defines repetition vs variation rules (memorability vs freshness)
- emits gates against aimless melodies and motif identity loss

Hard rule:
- This engine outputs melody specs/candidates, not lyrics, not arrangement, not mix/master.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- define harmonic language (harmony engine)
- define song structure (song structure engine)
- define groove/rhythm patterning (rhythm/groove engine)
- write lyrics (lyrics engine)
- orchestrate instruments (arrangement engine)
- perform vocals (vocal performance engine)
- mix/master (mix/master engine)
- do production placement/sync (production layer)

FORBIDDEN:
- “hook = vibes” without contour/range/repetition policies.

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- THEME_MOTIF_BIBLE (recommended)
- CHORD_LEXICON / PROGRESSION_RULESET (optional but recommended)
- CUE_STRUCTURE_PLAN (optional)
- MELODY_REQUEST (optional)

PRODUCES:
- MELODY_HOOK_CANDIDATE_SET
- MELODY_CONTOUR_POLICY
- RANGE_REGISTER_POLICY
- MELODY_GATES_REPORT

DEPENDS_ON:
- [09_SOUND_MUSIC_ENGINES/01__MUSIC_COMPOSITION_ENG]
(soft) [09_SOUND_MUSIC_ENGINES/03__HARMONY_CHORD_ENG, 09_SOUND_MUSIC_ENGINES/02__SONG_STRUCTURE_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/MUSIC/MELODY/
OPTIONAL:
- KB/MUSIC/MELODY (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Hook: a memorable melodic fragment designed to recur.
- Contour: shape of pitch movement (rise/fall/arch/zigzag) expressed as constraints.
- Register: low/mid/high ranges relative to instrument/voice.
- Motif Identity: constraints inherited from motif descriptors.
- Repetition Law: what repeats exactly vs what must vary.

Enums (baseline):
- contour_type: ASCENT|DESCENT|ARCH|INVERTED_ARCH|ZIGZAG|STEPWISE|LEAPY
- register: LOW|MID|HIGH|MIXED
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- melody/hook candidate generation rules and specs
- contour and range/register policies
- repetition/variation constraints
- gates for identity and coherence

OUT OF SCOPE (HARD):
- lyrics content (lyrics engine)
- harmony rules (harmony engine)
- instrumentation arrangement (arrangement engine)
- performance technique (vocal performance engine)
- mix/master

COLLISION RULE:
- If request is “write lyrics for the hook” → `07__LYRICS_ENG`
- If request is “choose chord progression for hook” → harmony engine
- If request is “arrange hook for instruments” → arrangement engine
- If request is “singing technique” → vocal performance engine

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: candidate set includes >=1 hook candidate per requested motif/theme (or explicit NONE with reason).
R2 (HARD) MUST: MELODY_CONTOUR_POLICY defines allowed contour types and forbidden contours by context.
R3 (HARD) MUST: RANGE_REGISTER_POLICY defines allowable register and range bounds.
R4 (HARD) MUST: repetition/variation rules exist for hooks.
R5 (HARD) FORBIDDEN: melodies that ignore motif identity descriptors (identity loss).
R6 (SOFT) SHOULD: include “singability” proxy rules if vocals are intended (range, leaps).
R7 (HARD) MUST: gates detect empty candidates, out-of-range specs, and identity drift.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: MELODY_HOOK_CANDIDATE_SET
- MUST:
  - candidate_set_id
  - version
  - candidates[] (non-empty)
  - binds_to[] (motif/theme refs)
  - checks[] (non-empty)
- CANDIDATE (minimum):
  - hook_id
  - bind_ref (motif_id or theme_id)
  - contour_type (enum)
  - register (LOW|MID|HIGH|MIXED)
  - range_bounds_semitones (min,max)
  - rhythmic_density_proxy (0..100 optional)
  - repetition_plan (required)
  - variation_plan (required)
  - compatibility_notes (optional: harmony/structure refs)
  - validation_tags[] (optional)
- REPETITION PLAN (minimum):
  - repeats_exact (bool)
  - repeat_frequency (testable)
- VARIATION PLAN (minimum):
  - allowed_variations[] (non-empty)
  - forbidden_variations[] (optional)
- VALIDATION:
  - candidates non-empty
  - each candidate has bind_ref and repetition/variation plans
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/MELODY/MELODY_HOOK_CANDIDATE_SET.md

---

ARTIFACT: MELODY_CONTOUR_POLICY
- MUST:
  - policy_id
  - version
  - allowed_contours[] (non-empty)
  - forbidden_contours[] (optional)
  - usage_rules[] (non-empty)
  - checks[] (non-empty)
- USAGE RULE (minimum):
  - rule_id
  - condition (testable)
  - allowed_contours[] (optional)
  - forbidden_contours[] (optional)
  - severity_if_broken (S0|S1|S2|S3)
- VALIDATION:
  - allowed_contours non-empty
  - usage_rules non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/MELODY/MELODY_CONTOUR_POLICY.md

---

ARTIFACT: RANGE_REGISTER_POLICY
- MUST:
  - policy_id
  - version
  - default_register (LOW|MID|HIGH|MIXED)
  - max_range_semitones (integer)
  - leap_policy (required)
  - checks[] (non-empty)
- LEAP POLICY (minimum):
  - max_leap_semitones (integer)
  - allow_exception_conditions (optional)
  - forbidden_leaps_contexts[] (optional)
- VALIDATION:
  - max_range_semitones > 0
  - max_leap_semitones > 0
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/MELODY/RANGE_REGISTER_POLICY.md

---

ARTIFACT: MELODY_GATES_REPORT
- MUST:
  - report_id
  - version
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
- Minimum required gates:
  - G1_CANDIDATES_EMPTY (S0)
  - G2_BIND_REF_MISSING (S0)
  - G3_RANGE_INVALID (S0)
  - G4_IDENTITY_DRIFT (S1)
  - G5_CONTOUR_POLICY_MISSING (S0)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/MELODY/MELODY_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load motif/theme bible (+ harmony/structure if provided).
2) Define contour policy and range/register policy.
3) For each motif/theme request:
   - generate 1..N hook candidates with contour + repetition/variation plans
4) Validate candidates against range and identity rules.
5) Run gates and emit artifacts.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: candidate set empty.
- S0-2: contour policy missing or empty.
- S0-3: range policy invalid.
- S0-4: produced artifacts missing schemas/storage targets.
- S0-5: hooks lack bind_ref or repetition/variation plans.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- motifs/themes define identity constraints
- harmony can constrain pitch choices (optional)
- structure plan can constrain where hooks appear (optional)

Downstream:
- arrangement engine orchestrates hooks into instruments
- vocal performance engine interprets hook for voice
- lyrics engine can align text to hook rhythm (separate owner)
- mix/master later finalizes audio

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family template:
  09_SOUND_MUSIC_ENGINES/00__TEMPLATE__ENGINE__SOUND_MUSIC_ENGINES.md
- Family README:
  09_SOUND_MUSIC_ENGINES/00__README__SOUND_MUSIC_ENGINES.md

--- END.

LOCK: OPEN
