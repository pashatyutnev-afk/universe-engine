# SONG STRUCTURE ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/02__SONG_STRUCTURE_ENG.md
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
UID: UE.ENG.SOUND.SONG.STRUCTURE.001
OWNER: SYSTEM
ROLE: Defines deterministic song/cue macro-structure: section models, form templates, recurrence rules, tension mapping by section, and validation gates. Produces structure artifacts for music cues without composing harmony/melody details.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Song Structure Engine created: section schema, form templates, recurrence rules, and gates."
- REASON: "Composition themes need structured forms to be reusable across cues and tracks."
- IMPACT: "Cues can be planned consistently before harmony/melody/arrangement."
- CHANGE_ID: UE.CHG.2026-01-08.SOUND.SONG.STRUCTURE.001

---

## 0) PURPOSE (LAW)
This engine owns **macro-structure** for songs/cues:
- defines section types (intro/verse/chorus/bridge/etc.) as a controlled model
- defines form templates (AABA, verse-chorus, through-composed, underscore cue forms)
- defines recurrence and variation rules (what repeats, what must change)
- defines tension mapping by section (as a plan, not harmony details)
- emits gates for structure completeness and coherence

Hard rule:
- This engine outputs structure, not harmony/chords, melody, arrangement, or mix.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- define harmony/chord progressions (03 engine)
- define hook melody details (04 engine)
- define rhythm/groove micro-patterns (05 engine owns groove)
- define lyrics (07 engine)
- define arrangement/instrumentation (08 engine)
- do production placement/sync (08 production layer engine)

FORBIDDEN:
- “structure” described only as “it builds then drops” without section model.

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- THEME_MOTIF_BIBLE (recommended)
- CUE_TAXONOMY (optional)
- RESONANCE_PROFILE (optional)
- CUE_REQUEST (optional)

PRODUCES:
- SECTION_MODEL_SPEC
- FORM_TEMPLATE_LIBRARY
- CUE_STRUCTURE_PLAN
- SONG_STRUCTURE_GATES_REPORT

DEPENDS_ON:
- [09_SOUND_MUSIC_ENGINES/01__MUSIC_COMPOSITION_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/MUSIC/STRUCTURE/
OPTIONAL:
- KB/MUSIC/STRUCTURE (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Section: named block with function (INTRO, BUILD, PEAK, RELEASE).
- Form Template: ordered list of sections with recurrence rules.
- Cue Structure Plan: chosen form + mapping of motifs to sections.
- Tension Curve: planned tension proxy (0..100) by section.
- Recurrence Rule: what repeats and how it varies.

Enums (baseline):
- section_type: INTRO|VERSE|CHORUS|BRIDGE|BREAKDOWN|BUILD|DROP|OUTRO|AMBIENT_BED|STINGER
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- section and form modeling
- cue-level structure plans
- tension mapping as proxy by section
- validation gates for structure completeness

OUT OF SCOPE (HARD):
- chord progressions and harmonic rules
- melody hooks
- arrangement/instrument choices
- mix/master and production sync

COLLISION RULE:
- If request is “chord map for sections” → `03__HARMONY_CHORD_ENG`
- If request is “melody/hook for chorus” → `04__MELODY_HOOK_ENG`
- If request is “instrumentation per section” → `08__ARRANGEMENT_INSTRUMENTATION_ENG`
- If request is “place cue to scene” → `12__MUSIC_TO_SCENE_ENG` or production layer placement

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: SECTION_MODEL_SPEC defines allowed section types and required fields.
R2 (HARD) MUST: FORM_TEMPLATE_LIBRARY contains at least 3 templates (unless project is constrained).
R3 (HARD) MUST: CUE_STRUCTURE_PLAN maps motifs/themes to sections (or explicitly FREE).
R4 (HARD) MUST: tension curve exists (0..100) across sections.
R5 (HARD) FORBIDDEN: plans without explicit section ordering.
R6 (SOFT) SHOULD: include “variation rules” for repeated sections.
R7 (HARD) MUST: gates detect missing section model, missing tension curve, empty templates, empty plan.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: SECTION_MODEL_SPEC
- MUST:
  - section_model_id
  - version
  - section_types[] (non-empty)
  - required_fields[] (non-empty)
  - checks[] (non-empty)
- REQUIRED FIELD (baseline):
  - section_id
  - section_type
  - function (testable)
  - duration_proxy (optional)
  - tension_target (0..100)
  - motif_refs[] (optional)
  - variation_rule_ref (optional)
- VALIDATION:
  - section_types non-empty
  - required_fields non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/STRUCTURE/SECTION_MODEL_SPEC.md

---

ARTIFACT: FORM_TEMPLATE_LIBRARY
- MUST:
  - library_id
  - version
  - templates[] (non-empty)
  - checks[] (non-empty)
- TEMPLATE (minimum):
  - template_id
  - name
  - section_sequence[] (non-empty; uses section_type)
  - recurrence_rules[] (optional)
  - when_to_use (testable)
  - when_forbidden (optional)
- VALIDATION:
  - templates non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/STRUCTURE/FORM_TEMPLATE_LIBRARY.md

---

ARTIFACT: CUE_STRUCTURE_PLAN
- MUST:
  - plan_id
  - version
  - cue_ref (optional)
  - chosen_template_id (required)
  - sections[] (non-empty; expanded from template)
  - tension_curve[] (non-empty; per section)
  - motif_mapping[] (optional)
  - checks[] (non-empty)
- SECTION INSTANCE (minimum):
  - section_id
  - section_type
  - order_index
  - function
  - duration_proxy (optional)
  - variation_notes (optional)
- TENSION CURVE ENTRY (minimum):
  - section_id
  - tension_target (0..100)
  - tension_bounds (min,max optional)
- MOTIF MAPPING (optional):
  - section_id
  - motif_or_theme_ref
  - mode (STATEMENT|VARIATION|FRAGMENT|ABSENT)
- VALIDATION:
  - sections non-empty and ordered
  - tension_curve covers all sections
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/STRUCTURE/CUE_STRUCTURE_PLAN.md

---

ARTIFACT: SONG_STRUCTURE_GATES_REPORT
- MUST:
  - report_id
  - version
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
- Minimum required gates:
  - G1_SECTION_MODEL_MISSING (S0)
  - G2_TEMPLATES_EMPTY (S0)
  - G3_PLAN_EMPTY (S0)
  - G4_TENSION_CURVE_MISSING (S0)
  - G5_TEMPLATE_INVALID (S1)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/STRUCTURE/SONG_STRUCTURE_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load motif/theme bible and cue needs.
2) Define section model and required fields.
3) Define form templates (library).
4) Select a template per cue request.
5) Expand template into section instances.
6) Map motifs/themes to sections and set tension curve.
7) Run gates and emit artifacts.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: section model missing or empty.
- S0-2: template library empty.
- S0-3: structure plan empty.
- S0-4: tension curve missing or incomplete.
- S0-5: produced artifacts missing schemas/storage targets.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- composition engine provides motifs/themes and cue taxonomy (optional)

Downstream:
- harmony/chord engine assigns harmonic language per section
- melody/hook engine writes section melodies consistent with motifs
- arrangement engine orchestrates sections
- music-to-scene engine aligns cue structure to scene needs

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family template:
  09_SOUND_MUSIC_ENGINES/00__TEMPLATE__ENGINE__SOUND_MUSIC_ENGINES.md
- Family README:
  09_SOUND_MUSIC_ENGINES/00__README__SOUND_MUSIC_ENGINES.md

--- END.

LOCK: OPEN
