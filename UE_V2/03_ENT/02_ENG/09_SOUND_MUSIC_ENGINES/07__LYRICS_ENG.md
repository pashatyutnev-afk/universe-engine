# LYRICS ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/07__LYRICS_ENG.md
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
UID: UE.ENG.SOUND.LYRICS.001
OWNER: SYSTEM
ROLE: Produces deterministic lyric artifacts: lyric concept brief, section-by-section lyric draft plan, constraint-validated lyric draft variants, and gates. Consumes rhyme/meter policies and melody/groove constraints; does not own vocal performance or mix/master.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Lyrics Engine created: lyric brief schema, structured lyric draft artifacts, constraint validation, and gates."
- REASON: "Lyrics must be compatible with meter/rhyme and melody/groove constraints; stamping requires structured outputs."
- IMPACT: "Lyric writing becomes reproducible, constrained, and auditable."
- CHANGE_ID: UE.CHG.2026-01-08.SOUND.LYRICS.001

---

## 0) PURPOSE (LAW)
This engine owns **LYRICS drafting under constraints**:
- generates lyric drafts as structured artifacts (by section/line)
- ensures compatibility with meter/rhyme policies and melody/groove constraints (when provided)
- enforces narrative-safe boundaries (lyrics cannot introduce canon-breaking facts unless explicitly allowed)
- emits gates for constraint violations (meter mismatch, forbidden themes, etc.)

Hard rule:
- Output must be structured and constraint-validated, not freeform prose.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- define rhyme/meter patterns (rhyme/meter engine)
- define melody hooks (melody engine)
- define groove/tempo (rhythm/groove engine)
- define vocal delivery technique (vocal performance engine)
- define arrangement (arrangement engine)
- do mix/master (mix/master engine)
- do production placement/sync (production sound engine)

FORBIDDEN:
- generating lyrics that ignore provided meter/rhyme constraints
- introducing new canon facts as “lyrics lore” without permission

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- METER_PATTERN_SPEC (recommended)
- RHYME_SCHEME_LIBRARY (recommended)
- STRESS_PHRASE_POLICY (optional)
- MELODY_HOOK_CANDIDATE_SET (optional)
- GROOVE_PALETTE / TEMPO_METER_POLICY (optional)
- THEME_MOTIF_BIBLE (optional)
- LYRIC_REQUEST (optional)

PRODUCES:
- LYRIC_CONCEPT_BRIEF
- LYRIC_DRAFT_STRUCTURE
- LYRIC_DRAFT_VARIANTS
- LYRICS_GATES_REPORT

DEPENDS_ON:
- [09_SOUND_MUSIC_ENGINES/06__RHYME_METER_ENG]
(soft) [09_SOUND_MUSIC_ENGINES/04__MELODY_HOOK_ENG, 09_SOUND_MUSIC_ENGINES/05__RHYTHM_GROOVE_ENG, 09_SOUND_MUSIC_ENGINES/01__MUSIC_COMPOSITION_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/MUSIC/LYRICS/
OPTIONAL:
- KB/MUSIC/LYRICS (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Lyric Concept: subject, POV, emotional direction, banned topics.
- Lyric Draft Structure: section and line scaffold aligned to meter/rhyme.
- Variant: alternative draft under the same constraints.
- Line Fit: meter + stress compliance proxy.
- Rhyme Fit: scheme compliance proxy.

Enums (baseline):
- section_type: INTRO|VERSE|CHORUS|BRIDGE|OUTRO|HOOK_LINE
- variant_quality: RAW|CLEAN|POLISHED
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- producing structured lyric drafts under constraints
- validating meter/rhyme compliance and banned-topic constraints
- producing variants with controlled differences

OUT OF SCOPE (HARD):
- composing melody or harmony
- vocal technique and delivery nuance
- mixing/mastering
- production sync placement

COLLISION RULE:
- If request is “change meter/rhyme rules” → rhyme/meter engine
- If request is “change melody contour to fit words” → melody engine
- If request is “how to perform it” → vocal performance engine
- If request is “arrange instrumentation under lyrics” → arrangement engine

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: LYRIC_CONCEPT_BRIEF declares POV, subject constraints, and forbidden topics.
R2 (HARD) MUST: LYRIC_DRAFT_STRUCTURE includes sections and lines mapped to meter pattern and rhyme scheme.
R3 (HARD) MUST: LYRIC_DRAFT_VARIANTS provide at least 1 variant draft.
R4 (HARD) MUST: each variant includes line-level compliance notes (meter/rhyme fit proxy).
R5 (HARD) FORBIDDEN: drafts that violate required meter/rhyme rules without being flagged.
R6 (SOFT) SHOULD: provide 2–3 variants with controlled stylistic differences.
R7 (HARD) MUST: gates detect meter mismatch, rhyme mismatch, forbidden-topic breach, and canon injection risk.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: LYRIC_CONCEPT_BRIEF
- MUST:
  - brief_id
  - version
  - pov (FIRST|SECOND|THIRD|OMNI)
  - subject (testable)
  - emotional_direction (optional)
  - allowed_topics[] (optional)
  - forbidden_topics[] (non-empty recommended)
  - language (optional)
  - checks[] (non-empty)
- VALIDATION:
  - subject present
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/LYRICS/LYRIC_CONCEPT_BRIEF.md

---

ARTIFACT: LYRIC_DRAFT_STRUCTURE
- MUST:
  - structure_id
  - version
  - meter_pattern_ref (required)
  - rhyme_scheme_ref (required)
  - sections[] (non-empty)
  - checks[] (non-empty)
- SECTION (minimum):
  - section_id
  - section_type
  - line_count (integer)
  - target_syllables_per_line[] (optional; from meter spec)
  - rhyme_group_map[] (optional; from scheme)
  - notes
- VALIDATION:
  - sections non-empty
  - refs present
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/LYRICS/LYRIC_DRAFT_STRUCTURE.md

---

ARTIFACT: LYRIC_DRAFT_VARIANTS
- MUST:
  - variants_id
  - version
  - structure_ref
  - variants[] (non-empty)
  - checks[] (non-empty)
- VARIANT (minimum):
  - variant_id
  - quality (RAW|CLEAN|POLISHED)
  - sections[] (non-empty)
  - compliance_notes (required)
- VARIANT SECTION (minimum):
  - section_id
  - lines[] (non-empty)
- LINE (minimum):
  - line_id
  - text
  - rhyme_group (optional)
  - meter_fit_proxy (0..100 optional)
  - issues[] (optional)
- COMPLIANCE NOTES (minimum):
  - meter_fit_summary (PASS|WARN|FAIL)
  - rhyme_fit_summary (PASS|WARN|FAIL)
  - forbidden_topic_breaches[] (optional)
  - canon_injection_risk (LOW|MED|HIGH)
- VALIDATION:
  - at least 1 variant
  - each variant has sections and lines
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/LYRICS/LYRIC_DRAFT_VARIANTS.md

---

ARTIFACT: LYRICS_GATES_REPORT
- MUST:
  - report_id
  - version
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
  - recommended_repairs[] (required if S0)
- Minimum required gates:
  - G1_STRUCTURE_MISSING (S0)
  - G2_VARIANTS_EMPTY (S0)
  - G3_METER_MISMATCH (S0 if required)
  - G4_RHYME_MISMATCH (S1)
  - G5_FORBIDDEN_TOPIC_BREACH (S0)
  - G6_CANON_INJECTION_RISK_HIGH (S0)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/LYRICS/LYRICS_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load meter/rhyme constraints and optional melody/groove constraints.
2) Build lyric concept brief (POV, subject, forbidden topics).
3) Build draft structure (sections/lines mapped to meter + rhyme).
4) Produce 1..N lyric variants under structure.
5) Compute compliance proxies (meter/rhyme) and flag breaches.
6) Run gates and emit artifacts.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: draft structure missing or refs missing.
- S0-2: variants empty.
- S0-3: forbidden topic breach detected.
- S0-4: high canon injection risk.
- S0-5: produced artifacts missing schemas/storage targets.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- rhyme/meter defines constraints
- melody/groove provide fit constraints (optional)
- motifs can inform lyrical bindings (optional)

Downstream:
- vocal performance engine maps delivery to stress patterns
- arrangement engine supports lyric density with instrumentation choices
- mix/master finalizes (separate engine)

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family template:
  09_SOUND_MUSIC_ENGINES/00__TEMPLATE__ENGINE__SOUND_MUSIC_ENGINES.md
- Family README:
  09_SOUND_MUSIC_ENGINES/00__README__SOUND_MUSIC_ENGINES.md

--- END.

LOCK: OPEN
