# VOCAL PERFORMANCE ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/09__VOCAL_PERFORMANCE_ENG.md
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
UID: UE.ENG.SOUND.VOCAL.PERFORMANCE.001
OWNER: SYSTEM
ROLE: Defines deterministic vocal performance specs: delivery style profiles, phrasing/stress alignment, articulation dynamics, range comfort rules, take/comp policy (abstract), and validation gates. Consumes lyrics/melody/rhythm/arrangement constraints; does not own mix/master.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Vocal Performance Engine created: vocal style profile schema, phrasing rules, take plan, and gates."
- REASON: "Vocal execution needs deterministic constraints aligned to lyric meter and melodic range."
- IMPACT: "Vocals become consistent, interpretable, and compatible with arrangement and lyric structure."
- CHANGE_ID: UE.CHG.2026-01-08.SOUND.VOCAL.PERFORMANCE.001

---

## 0) PURPOSE (LAW)
This engine owns **VOCAL PERFORMANCE constraints/specs**:
- delivery style profiles (tone, grit, breathiness as controlled tags)
- phrasing and stress alignment to meter/groove/melody constraints
- articulation and dynamics policies (soft/hard, legato/staccato)
- range comfort rules and leap tolerance
- take planning and comp policy (abstract; not DAW-specific)
- gates to detect range violations, stress mismatch, and over-articulation drift

Hard rule:
- This engine defines performance specs; it does NOT mix/master vocals.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- write lyrics (lyrics engine)
- compose melody/harmony (melody/harmony engines)
- define groove (rhythm engine)
- arrange instrumentation (arrangement engine)
- do mix/master and vocal processing chains (mix/master engine)
- do production placement/sync (production audio engine)

FORBIDDEN:
- “sing it better” without measurable constraints (range, stress fit, dynamics rules)

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- LYRIC_DRAFT_VARIANTS (recommended)
- METER_PATTERN_SPEC / STRESS_PHRASE_POLICY (recommended)
- MELODY_HOOK_CANDIDATE_SET (recommended)
- TEMPO_METER_POLICY / GROOVE_PALETTE (optional)
- REGISTER_VOICING_POLICY (optional; arrangement)
- VOCAL_REQUEST (optional)

PRODUCES:
- VOCAL_STYLE_PROFILE
- PHRASE_STRESS_ALIGNMENT_RULES
- TAKE_PLAN_SPEC
- VOCAL_GATES_REPORT

DEPENDS_ON:
- [09_SOUND_MUSIC_ENGINES/07__LYRICS_ENG, 09_SOUND_MUSIC_ENGINES/06__RHYME_METER_ENG, 09_SOUND_MUSIC_ENGINES/04__MELODY_HOOK_ENG]
(soft) [09_SOUND_MUSIC_ENGINES/05__RHYTHM_GROOVE_ENG, 09_SOUND_MUSIC_ENGINES/08__ARRANGEMENT_INSTRUMENTATION_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/MUSIC/VOCALS/
OPTIONAL:
- KB/MUSIC/VOCALS (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Vocal Style Profile: controlled tags for delivery (clean/gritty/breathy/whisper/chant) with bounds.
- Stress Alignment: mapping stressed syllables to strong beats/positions.
- Phrasing: breath and line break rules aligned to groove.
- Dynamics: loudness intensity proxy (0..100) by section.
- Take Plan: number of takes, comp strategy, and QC checks (abstract).

Enums (baseline):
- delivery_style: CLEAN|GRITTY|BREATHY|WHISPER|CHANT|RAP_TIGHT|RAP_LAIDBACK
- articulation: LEGATO|MIXED|STACCATO
- intensity: 0..100
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- performance delivery constraints and profiles
- phrase/stress alignment rules
- take planning specs and QC gates

OUT OF SCOPE (HARD):
- lyrical content writing
- melody/harmony composition changes
- arrangement orchestration
- mix/master processing and loudness targets beyond performance proxies

COLLISION RULE:
- If request is “change lyric lines” → lyrics engine
- If request is “change melody to fit singer” → melody engine
- If request is “compress/EQ/reverb settings” → mix/master engine
- If request is “arrange backing vocals/harmonies notes” → arrangement engine (this engine only defines performance constraints)

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: VOCAL_STYLE_PROFILE defines delivery style tags and forbidden styles.
R2 (HARD) MUST: PHRASE_STRESS_ALIGNMENT_RULES define how stresses align to beats/positions (testable).
R3 (HARD) MUST: TAKE_PLAN_SPEC defines take counts and comp policy with QC checks.
R4 (HARD) MUST: range comfort and leap tolerance rules exist (from melody range policy or declared here).
R5 (HARD) FORBIDDEN: performance specs that require mix/master processing to “fix” core issues (must fix at performance level).
R6 (SOFT) SHOULD: include section-level dynamics envelopes aligned with song structure if provided.
R7 (HARD) MUST: gates detect stress mismatch, range violations, and delivery-style contradictions with lyric intent.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: VOCAL_STYLE_PROFILE
- MUST:
  - profile_id
  - version
  - delivery_style (enum)
  - articulation (LEGATO|MIXED|STACCATO)
  - intensity_target (0..100)
  - intensity_bounds (min,max)
  - forbidden_styles[] (optional)
  - breath_policy (required)
  - checks[] (non-empty)
- BREATH POLICY (minimum):
  - max_phrase_length_proxy (optional)
  - allowed_breath_points[] (optional)
  - forbidden_breath_points[] (optional)
- VALIDATION:
  - intensity bounds valid and include target
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/VOCALS/VOCAL_STYLE_PROFILE.md

---

ARTIFACT: PHRASE_STRESS_ALIGNMENT_RULES
- MUST:
  - rules_id
  - version
  - stress_alignment_rules[] (non-empty)
  - phrasing_rules[] (non-empty)
  - checks[] (non-empty)
- STRESS ALIGNMENT RULE (minimum):
  - rule_id
  - condition (testable; meter/groove context)
  - statement (testable)
  - severity_if_broken (S0|S1|S2|S3)
- PHRASING RULE (minimum):
  - rule_id
  - statement (testable)
  - severity_if_broken (S0|S1|S2|S3)
- VALIDATION:
  - both rule lists non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/VOCALS/PHRASE_STRESS_ALIGNMENT_RULES.md

---

ARTIFACT: TAKE_PLAN_SPEC
- MUST:
  - take_plan_id
  - version
  - sections[] (optional)
  - take_count_target (integer)
  - comp_policy (required)
  - qc_checks[] (non-empty)
- COMP POLICY (minimum):
  - method (BEST_TAKE|COMPOSITE|LAYERED_DOUBLES)
  - selection_criteria[] (non-empty; testable)
  - when_to_redo (testable)
- QC CHECK (minimum):
  - check_id
  - description
  - severity (S0|S1|S2|S3)
- VALIDATION:
  - take_count_target > 0
  - selection_criteria non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/VOCALS/TAKE_PLAN_SPEC.md

---

ARTIFACT: VOCAL_GATES_REPORT
- MUST:
  - report_id
  - version
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
- Minimum required gates:
  - G1_STYLE_PROFILE_MISSING (S0)
  - G2_STRESS_RULES_EMPTY (S0)
  - G3_TAKE_PLAN_INVALID (S0)
  - G4_RANGE_VIOLATION (S0)
  - G5_STRESS_MISMATCH (S1)
  - G6_DELIVERY_CONTRADICTION (S1)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/VOCALS/VOCAL_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load lyric draft + meter/stress + melody range constraints (+ groove optional).
2) Define vocal style profile (delivery, articulation, intensity bounds, breath policy).
3) Define phrase & stress alignment rules (beat alignment and phrasing breaks).
4) Define take plan and comp policy with QC checks.
5) Run gates (range, stress mismatch, missing rules).
6) Emit artifacts.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: vocal style profile missing.
- S0-2: stress/phrasing rules missing.
- S0-3: take plan invalid.
- S0-4: range violation detected (out of bounds).
- S0-5: produced artifacts missing schemas/storage targets.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- lyrics provide text
- meter/rhyme provide stress expectations
- melody provides pitch/range constraints
- groove provides timing feel (optional)
- arrangement provides space and register policy (optional)

Downstream:
- mix/master engine can process vocals after performance spec is satisfied
- production audio engine can place vocals in timeline (sync/clarity) separate from deep music
- QA can validate takes against gates

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Production audio boundary:
  08_KNOWLEDGE_PRODUCTION_ENGINES/08__SOUND_MUSIC_ENG.md
- Family template:
  09_SOUND_MUSIC_ENGINES/00__TEMPLATE__ENGINE__SOUND_MUSIC_ENGINES.md
- Family README:
  09_SOUND_MUSIC_ENGINES/00__README__SOUND_MUSIC_ENGINES.md

--- END.

LOCK: OPEN
