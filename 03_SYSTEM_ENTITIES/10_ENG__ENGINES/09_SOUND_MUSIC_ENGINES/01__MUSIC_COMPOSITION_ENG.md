# MUSIC COMPOSITION ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/01__MUSIC_COMPOSITION_ENG.md
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
UID: UE.ENG.SOUND.MUSIC.COMPOSITION.001
OWNER: SYSTEM
ROLE: Defines deterministic deep-music composition outputs: themes/motifs, tonal center policies, harmonic direction constraints, cue taxonomy, and validation gates. Produces composition-ready artifacts (not production placement plans).

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Music Composition Engine created: theme/motif bible schema, cue taxonomy, tonal policies, and gates."
- REASON: "Deep music requires its own canonical primitives separate from production audio placement."
- IMPACT: "Music identity becomes stampable, reusable, and auditable across scenes and formats."
- CHANGE_ID: UE.CHG.2026-01-08.SOUND.MUSIC.COMPOSITION.001

---

## 0) PURPOSE (LAW)
This engine owns **DEEP MUSIC COMPOSITION primitives**:
- defines musical identity at composition level (themes, motifs, leitmotifs)
- defines cue taxonomy and intent mapping (what music *should do* compositionally)
- defines tonal center and harmonic direction constraints (high-level, not full harmony engine yet)
- emits validation gates to prevent “random music” and ensure thematic consistency

Hard rule:
- This engine composes/defines *music identity*; it does NOT do production placement/sync/clarity (that is `08_KNOWLEDGE_PRODUCTION_ENGINES/08__SOUND_MUSIC_ENG`).

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- do production audio placement, dialogue clarity, sync cues (08 production sound engine)
- define montage/edit rhythm (editing engine)
- define full harmonic system details (that is owned by `03__HARMONY_CHORD_ENG` in this family)
- define melody hooks in detail (that is `04__MELODY_HOOK_ENG`)
- do arrangement/instrumentation (08 in this family)
- do mix/master implementation (13 in this family)
- write narrative content

FORBIDDEN:
- “music plan” that is only mood adjectives without motifs/themes/taxonomy

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- RESONANCE_PROFILE (optional)
- ATMOSPHERE_LAYER_SPEC (optional)
- THEME_MEANING_NOTES (optional; narrative engine output if exists)
- SCENE_PACK (optional)
- CUE_REQUEST (optional: list of needed cues)

PRODUCES:
- THEME_MOTIF_BIBLE
- CUE_TAXONOMY
- TONAL_DIRECTION_POLICY
- COMPOSITION_GATES_REPORT

DEPENDS_ON:
- [] (base for music family; other music engines refine components)

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/MUSIC/COMPOSITION/
OPTIONAL:
- KB/MUSIC/COMPOSITION (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Theme: a core musical identity object (can be reused/varied).
- Motif: smaller unit tied to idea/character/place/feeling (composition-level).
- Leitmotif: motif with explicit recurrence rules.
- Cue: a piece/unit of music designed for a scene/segment purpose.
- Tonal Center: primary tonal gravity target(s) (key centers as constraints).
- Harmonic Direction: high-level movement constraints (e.g., “tension increases via chromatic mediants” — detailed in harmony engine later).

Enums (baseline):
- scope: GLOBAL|ARC|SCENE_WINDOW
- cue_type: THEME_STATEMENT|MOTIF_CALL|TENSION_BUILD|RELEASE|TRANSITION|AMBIENT_MUSIC|ACTION|MYSTERY
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- theme/motif definitions and recurrence rules
- cue taxonomy and intent mapping
- tonal center policy and high-level harmonic direction constraints
- gates for thematic consistency and coverage

OUT OF SCOPE (HARD):
- production placement and sync
- detailed harmony/chord progressions (next engine)
- detailed melody/hook design (04)
- arrangement/orchestration (08)
- mix/master (13)

COLLISION RULE:
- If request is “place cues on timeline / sync to edit” → production sound engine (08 production layer)
- If request is “write chord progression rules” → `03__HARMONY_CHORD_ENG`
- If request is “write the hook melody” → `04__MELODY_HOOK_ENG`
- If request is “instrumentation arrangement” → `08__ARRANGEMENT_INSTRUMENTATION_ENG`

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: THEME_MOTIF_BIBLE contains at least one theme and one motif (unless explicitly “motifless ambient-only” with reason).
R2 (HARD) MUST: each theme/motif has identity fields and variation constraints.
R3 (HARD) MUST: CUE_TAXONOMY lists cue types and required coverage rules (what must exist).
R4 (HARD) MUST: TONAL_DIRECTION_POLICY defines allowed tonal centers and harmonic direction constraints (high-level).
R5 (HARD) FORBIDDEN: compositions described only in adjectives without musical identity objects.
R6 (SOFT) SHOULD: include recurrence rules for leitmotifs (frequency and scope).
R7 (HARD) MUST: gates detect missing coverage (no cues), missing identity objects, and contradictions with resonance/atmosphere inputs (if provided).

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: THEME_MOTIF_BIBLE
- MUST:
  - bible_id
  - version
  - themes[] (non-empty)
  - motifs[] (non-empty)
  - leitmotifs[] (optional)
  - variation_rules[] (non-empty)
  - checks[] (non-empty)
- THEME (minimum):
  - theme_id
  - name
  - identity_descriptors[] (non-empty; controlled words)
  - interval_signature (optional; described textually)
  - rhythmic_signature (optional)
  - default_tonal_center_refs[] (optional)
  - allowed_variations[] (non-empty)
  - forbidden_variations[] (optional)
  - scope (GLOBAL|ARC)
- MOTIF (minimum):
  - motif_id
  - name
  - binds_to (CHARACTER|PLACE|IDEA|FACTION|FEELING|EVENT)
  - bind_ref (optional id)
  - identity_descriptors[] (non-empty)
  - recurrence_rule_ref (optional)
  - allowed_variations[] (non-empty)
- LEITMOTIF (optional):
  - leit_id
  - motif_id
  - recurrence (testable; e.g., "once per episode when X appears")
  - variation_bounds (optional)
- VARIATION RULE (minimum):
  - rule_id
  - applies_to (theme_id/motif_id)
  - statement (testable)
  - severity_if_broken (S0|S1|S2|S3)
- VALIDATION:
  - themes and motifs non-empty
  - each item has identity_descriptors
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/COMPOSITION/THEME_MOTIF_BIBLE.md

---

ARTIFACT: CUE_TAXONOMY
- MUST:
  - taxonomy_id
  - version
  - cue_types[] (non-empty)
  - mapping_rules[] (non-empty)
  - coverage_requirements[] (non-empty)
  - checks[] (non-empty)
- CUE TYPE (minimum):
  - cue_type (enum or controlled)
  - purpose (testable)
  - typical_duration_proxy (optional)
  - typical_intensity_proxy (0..100 optional)
- MAPPING RULE (minimum):
  - rule_id
  - condition (testable; e.g., "climax window")
  - recommended_cue_type
  - must_reference (THEME|MOTIF|FREE)
- COVERAGE REQUIREMENT (minimum):
  - requirement_id
  - statement (testable)
  - severity_if_missing (S0|S1|S2|S3)
- VALIDATION:
  - cue_types non-empty
  - coverage_requirements non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/COMPOSITION/CUE_TAXONOMY.md

---

ARTIFACT: TONAL_DIRECTION_POLICY
- MUST:
  - policy_id
  - version
  - allowed_tonal_centers[] (non-empty; names or tags)
  - modulation_policy (required; high-level)
  - tension_release_map (optional)
  - forbidden_centers[] (optional)
  - checks[] (non-empty)
- MODULATION POLICY (minimum):
  - allowed_moves[] (non-empty; described)
  - forbidden_moves[] (optional)
  - when_to_modulate (testable)
- VALIDATION:
  - allowed_tonal_centers non-empty
  - allowed_moves non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/COMPOSITION/TONAL_DIRECTION_POLICY.md

---

ARTIFACT: COMPOSITION_GATES_REPORT
- MUST:
  - report_id
  - version
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
- Minimum required gates:
  - G1_THEMES_EMPTY (S0)
  - G2_MOTIFS_EMPTY (S0)
  - G3_CUE_TAXONOMY_EMPTY (S0)
  - G4_TONAL_POLICY_EMPTY (S0)
  - G5_RES_ATMOS_CONTRADICTION (S1)
  - G6_VAGUE_DESCRIPTORS_ONLY (S1)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/COMPOSITION/COMPOSITION_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load optional resonance/atmosphere and any cue requests.
2) Define theme set (global identity).
3) Define motif set (bindings and recurrence rules).
4) Define cue taxonomy and mapping rules (when to use which cue type).
5) Define tonal direction policy (allowed centers, modulation rules).
6) Run gates (missing identity objects, missing taxonomy/policy, contradictions).
7) Emit artifacts.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: themes[] empty.
- S0-2: motifs[] empty (unless explicitly justified ambient-only mode).
- S0-3: cue taxonomy missing.
- S0-4: tonal policy missing.
- S0-5: produced artifacts missing schemas/storage targets.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- resonance/atmosphere provide emotional constraints (optional)
- narrative theme/meaning notes can inform what motifs bind to (optional)

Downstream:
- `02__SONG_STRUCTURE_ENG` can structure songs/cues using motifs
- `03__HARMONY_CHORD_ENG` refines harmonic language
- `04__MELODY_HOOK_ENG` defines hook melodies consistent with motifs
- `08__ARRANGEMENT_INSTRUMENTATION_ENG` orchestrates themes into instruments
- production audio engine (08 production layer) places composed cues on the edit timeline

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
