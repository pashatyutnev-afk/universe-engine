# RHYME / METER ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/06__RHYME_METER_ENG.md
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
UID: UE.ENG.SOUND.RHYME.METER.001
OWNER: SYSTEM
ROLE: Defines deterministic rhyme and lyrical meter constraints: meter patterns, rhyme schemes, stress policies, density bounds, and validation gates. Produces text-structure specs consumable by lyrics and vocal engines without writing full lyrics.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Rhyme/Meter Engine created: meter pattern schema, rhyme scheme library, stress rules, and gates."
- REASON: "Lyrics need structural constraints aligned with groove and melody; must be reusable and auditable."
- IMPACT: "Lyric writing can be constrained to consistent meter/rhyme without ad-hoc drift."
- CHANGE_ID: UE.CHG.2026-01-08.SOUND.RHYME.METER.001

---

## 0) PURPOSE (LAW)
This engine owns **RHYME + METER constraints**:
- defines meter patterns (syllable counts / stress patterns) as reusable specs
- defines rhyme scheme libraries (AABB/ABAB/etc.) and allowed variants
- defines stress and phrasing policies compatible with groove/melody constraints
- emits gates for meter coherence and rhyme drift

Hard rule:
- This engine outputs constraints/specs; it does NOT write full lyrics.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- write lyrics content (lyrics engine)
- define melody/hook content (melody engine)
- define groove patterns (rhythm/groove engine)
- do vocal performance technique (vocal engine)
- do arrangement or mix/master
- do production placement/sync

FORBIDDEN:
- “meter” described only as “fast rap” without pattern specs.

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- TEMPO_METER_POLICY (optional)
- GROOVE_PALETTE (optional)
- MELODY_HOOK_CANDIDATE_SET (optional)
- RHYME_METER_REQUEST (optional)

PRODUCES:
- METER_PATTERN_SPEC
- RHYME_SCHEME_LIBRARY
- STRESS_PHRASE_POLICY
- RHYME_METER_GATES_REPORT

DEPENDS_ON:
- [] (can run standalone; integrates with melody/rhythm/lyrics)

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/MUSIC/LYRICS_STRUCTURE/
OPTIONAL:
- KB/MUSIC/LYRICS_STRUCTURE (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Meter Pattern: syllable count and/or stress map per line.
- Stress Map: sequence of stressed/unstressed positions (abstract).
- Rhyme Scheme: mapping line endings to rhyme groups (A,B,C...).
- Internal Rhyme: rhyme inside a line (optional constraints).
- Density: proxy 0..100 for syllable/event density in lyrics.
- Phrase Fit: compatibility constraint with groove (bar boundaries).

Enums (baseline):
- meter_mode: SYLLABLE_COUNT|STRESS_PATTERN|HYBRID
- rhyme_type: END|INTERNAL|MULTISYLLABIC|SLANT
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- meter pattern specification
- rhyme scheme library and allowed variants
- stress/phrase fit policies (constraints)
- validation gates

OUT OF SCOPE (HARD):
- writing lyrics text
- composing melody/harmony
- performance delivery details (beyond stress intent)

COLLISION RULE:
- If request is “write the lyrics” → `07__LYRICS_ENG`
- If request is “how to sing/rap delivery” → `09__VOCAL_PERFORMANCE_ENG`
- If request is “melody contour for lines” → `04__MELODY_HOOK_ENG`
- If request is “groove placement per bar” → `05__RHYTHM_GROOVE_ENG`

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: METER_PATTERN_SPEC defines at least one reusable pattern (unless instrumental-only mode stated).
R2 (HARD) MUST: RHYME_SCHEME_LIBRARY defines at least 3 schemes with allowed variants.
R3 (HARD) MUST: STRESS_PHRASE_POLICY defines stress rules and phrase fit constraints.
R4 (HARD) FORBIDDEN: vague descriptions without meter mode and pattern fields.
R5 (HARD) MUST: gates detect missing patterns, invalid line lengths, and scheme emptiness.
R6 (SOFT) SHOULD: include slant-rhyme policy bounds (allowed percent).
R7 (HARD) MUST: keep outputs compatible with tempo/meter policy if provided.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: METER_PATTERN_SPEC
- MUST:
  - meter_spec_id
  - version
  - meter_mode (SYLLABLE_COUNT|STRESS_PATTERN|HYBRID)
  - patterns[] (non-empty)
  - checks[] (non-empty)
- PATTERN (minimum):
  - pattern_id
  - name
  - line_count (integer)
  - syllables_per_line[] (required if mode includes syllables)
  - stress_map[] (required if mode includes stress; abstract tokens)
  - density_target (0..100 optional)
  - allowed_variations[] (non-empty)
  - forbidden_variations[] (optional)
- VALIDATION:
  - patterns non-empty
  - line_count > 0
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/LYRICS_STRUCTURE/METER_PATTERN_SPEC.md

---

ARTIFACT: RHYME_SCHEME_LIBRARY
- MUST:
  - library_id
  - version
  - schemes[] (non-empty)
  - checks[] (non-empty)
- SCHEME (minimum):
  - scheme_id
  - name (AABB/ABAB/etc.)
  - line_map[] (non-empty; e.g., [A,A,B,B])
  - rhyme_types_allowed[] (END|INTERNAL|MULTISYLLABIC|SLANT)
  - variation_rules[] (optional)
  - when_to_use (testable)
- VALIDATION:
  - schemes non-empty
  - each scheme has line_map
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/LYRICS_STRUCTURE/RHYME_SCHEME_LIBRARY.md

---

ARTIFACT: STRESS_PHRASE_POLICY
- MUST:
  - policy_id
  - version
  - stress_rules[] (non-empty)
  - phrase_fit_rules[] (non-empty)
  - slant_rhyme_policy (optional)
  - checks[] (non-empty)
- STRESS RULE (minimum):
  - rule_id
  - statement (testable)
  - severity_if_broken (S0|S1|S2|S3)
- PHRASE FIT RULE (minimum):
  - rule_id
  - condition (testable; e.g., "4/4 bar")
  - statement (testable)
  - severity_if_broken (S0|S1|S2|S3)
- SLANT RHYME POLICY (optional):
  - max_slant_ratio (0..100)
  - when_allowed (testable)
- VALIDATION:
  - stress_rules and phrase_fit_rules non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/LYRICS_STRUCTURE/STRESS_PHRASE_POLICY.md

---

ARTIFACT: RHYME_METER_GATES_REPORT
- MUST:
  - report_id
  - version
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
- Minimum required gates:
  - G1_PATTERNS_EMPTY (S0)
  - G2_SCHEMES_EMPTY (S0)
  - G3_STRESS_POLICY_EMPTY (S0)
  - G4_MODE_MISMATCH (S1)
  - G5_VAGUE_RULES (S1)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/LYRICS_STRUCTURE/RHYME_METER_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load optional tempo/groove/melody constraints.
2) Define meter mode and meter patterns (line counts, syllables/stress maps).
3) Define rhyme scheme library (schemes + variants).
4) Define stress and phrase-fit policies (bar/beat constraints).
5) Run gates and emit artifacts.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: patterns empty.
- S0-2: rhyme schemes empty.
- S0-3: stress/phrase policy missing.
- S0-4: produced artifacts missing schemas/storage targets.
- S0-5: rules are vague adjectives without pattern structure.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- groove/tempo can constrain phrase fit (optional)
- melody can constrain syllable placement (optional)

Downstream:
- lyrics engine writes text constrained by meter/rhyme specs
- vocal performance engine interprets stress patterns and delivery
- arrangement engine aligns backing rhythm to lyrical density

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family template:
  09_SOUND_MUSIC_ENGINES/00__TEMPLATE__ENGINE__SOUND_MUSIC_ENGINES.md
- Family README:
  09_SOUND_MUSIC_ENGINES/00__README__SOUND_MUSIC_ENGINES.md

--- END.

LOCK: OPEN
