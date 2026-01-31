# ARRANGEMENT / INSTRUMENTATION ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/08__ARRANGEMENT_INSTRUMENTATION_ENG.md
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
UID: UE.ENG.SOUND.ARRANGEMENT.INSTR.001
OWNER: SYSTEM
ROLE: Defines deterministic arrangement artifacts: instrumentation palette, role assignment per section, register/voicing policies (abstract), texture density maps, and validation gates. Consumes harmony/melody/rhythm/structure and outputs arrangement specs without owning mix/master.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Arrangement/Instrumentation Engine created: instrumentation palette schema, section role assignment, texture density map, and gates."
- REASON: "Deep music requires translation from composition/harmony/melody into orchestrated textures."
- IMPACT: "Arrangements become reusable, bounded, and auditable across cues."
- CHANGE_ID: UE.CHG.2026-01-08.SOUND.ARRANGEMENT.INSTR.001

---

## 0) PURPOSE (LAW)
This engine owns **ARRANGEMENT / INSTRUMENTATION**:
- defines instrumentation palette (allowed instruments and roles)
- assigns musical roles per section (bass/harmony/lead/rhythm/pads/fx)
- defines register/voicing policies in abstract terms (no DAW specifics)
- defines texture density per section to support tension curves
- emits gates for role coverage, overcrowding, and register collisions

Hard rule:
- This engine orchestrates; it does NOT mix/master and does NOT do production placement.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- define themes/motifs identity (composition engine)
- define macro structure templates (song structure engine)
- define harmony rules (harmony engine)
- define melody hooks identity (melody engine)
- define groove rules (rhythm engine)
- define vocal performance technique (vocal engine)
- do mix/master (mix/master engine)
- do production placement/sync (production audio engine)

FORBIDDEN:
- DAW-specific routing as mandatory output (only abstract roles/specs)

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- CUE_STRUCTURE_PLAN (recommended)
- CHORD_LEXICON / PROGRESSION_RULESET (optional)
- MELODY_HOOK_CANDIDATE_SET (optional)
- GROOVE_PALETTE / TEMPO_METER_POLICY (optional)
- THEME_MOTIF_BIBLE (optional)
- ARRANGEMENT_REQUEST (optional)

PRODUCES:
- INSTRUMENTATION_PALETTE
- SECTION_ROLE_ASSIGNMENT
- REGISTER_VOICING_POLICY
- TEXTURE_DENSITY_MAP
- ARRANGEMENT_GATES_REPORT

DEPENDS_ON:
- [] (can run with partial inputs, but best with structure/harmony/melody)

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/MUSIC/ARRANGEMENT/
OPTIONAL:
- KB/MUSIC/ARRANGEMENT (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Instrumentation Palette: allowed instruments grouped by roles and families.
- Role: function in arrangement (LEAD, HARMONY, BASS, RHYTHM, PAD, FX, VOCAL_SPACE).
- Register: LOW/MID/HIGH ranges (abstract).
- Voicing Policy: how harmony is distributed across voices (spread/cluster) as tags.
- Texture Density: proxy 0..100 for layer thickness per section.
- Collision: register overlap causing mud (abstract gate).

Enums (baseline):
- role: LEAD|HARMONY|BASS|RHYTHM|PAD|FX|VOCAL_SPACE
- register: LOW|MID|HIGH
- voicing_tag: OPEN|CLOSE|CLUSTER|SPREAD
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- defining instrument sets and assigning roles per section
- register/voicing policies and texture density maps
- arrangement validation gates (overcrowding, missing role coverage)

OUT OF SCOPE (HARD):
- writing harmony rules (harmony engine)
- writing melodies (melody engine)
- performance nuance (vocal engine)
- mixing/mastering implementation (mix/master engine)
- production placement/sync (production layer)

COLLISION RULE:
- If request is “change chord progression” → harmony engine
- If request is “change hook melody” → melody engine
- If request is “how to mix and master” → mix/master engine
- If request is “where to place cue in edit” → music-to-scene / production audio placement

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: INSTRUMENTATION_PALETTE lists allowed instruments and role compatibility.
R2 (HARD) MUST: SECTION_ROLE_ASSIGNMENT assigns required roles per section (at least LEAD or PAD/HARMONY, and BASS when needed).
R3 (HARD) MUST: REGISTER_VOICING_POLICY defines register bounds and voicing tags per role.
R4 (HARD) MUST: TEXTURE_DENSITY_MAP provides density targets per section aligned to tension curve if present.
R5 (HARD) FORBIDDEN: arrangements that specify only “add strings” without roles/register policies.
R6 (SOFT) SHOULD: define “space reservation” rules for vocals if lyrics/vocals exist.
R7 (HARD) MUST: gates detect missing role coverage and register collisions.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: INSTRUMENTATION_PALETTE
- MUST:
  - palette_id
  - version
  - instruments[] (non-empty)
  - role_maps[] (non-empty)
  - forbidden_combinations[] (optional)
  - checks[] (non-empty)
- INSTRUMENT (minimum):
  - instrument_id
  - name
  - family (STRINGS|BRASS|WOODWIND|PERCUSSION|SYNTH|GUITAR|KEYS|BASS|VOICE|OTHER)
  - default_register (LOW|MID|HIGH|MIXED)
  - allowed_roles[] (non-empty)
  - when_to_use (testable)
- ROLE MAP (minimum):
  - role
  - preferred_families[] (optional)
  - max_layer_count (optional)
- VALIDATION:
  - instruments non-empty
  - each instrument has allowed_roles
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/ARRANGEMENT/INSTRUMENTATION_PALETTE.md

---

ARTIFACT: SECTION_ROLE_ASSIGNMENT
- MUST:
  - assignment_id
  - version
  - sections[] (non-empty)
  - checks[] (non-empty)
- SECTION ASSIGNMENT (minimum):
  - section_id
  - section_type (optional)
  - roles_present[] (non-empty)
  - lead_ref (optional: motif/theme/melody ref)
  - harmony_ref (optional)
  - rhythm_ref (optional)
  - notes
- VALIDATION:
  - each section has roles_present non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/ARRANGEMENT/SECTION_ROLE_ASSIGNMENT.md

---

ARTIFACT: REGISTER_VOICING_POLICY
- MUST:
  - policy_id
  - version
  - role_register_bounds[] (non-empty)
  - voicing_tags_allowed[] (non-empty)
  - collision_rules[] (non-empty)
  - checks[] (non-empty)
- ROLE REGISTER BOUNDS (minimum):
  - role
  - allowed_registers[] (non-empty)
  - preferred_register (optional)
  - max_overlap_with_roles[] (optional)
- COLLISION RULE (minimum):
  - rule_id
  - statement (testable)
  - severity_if_broken (S0|S1|S2|S3)
- VALIDATION:
  - role_register_bounds non-empty
  - collision_rules non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/ARRANGEMENT/REGISTER_VOICING_POLICY.md

---

ARTIFACT: TEXTURE_DENSITY_MAP
- MUST:
  - density_map_id
  - version
  - section_density[] (non-empty)
  - bounds (min,max 0..100)
  - anti_patterns[] (non-empty)
  - checks[] (non-empty)
- SECTION DENSITY (minimum):
  - section_id
  - density_target (0..100)
  - density_bounds (min,max)
  - max_layers (optional)
  - notes
- VALIDATION:
  - section_density non-empty
  - bounds valid
  - anti_patterns non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/ARRANGEMENT/TEXTURE_DENSITY_MAP.md

---

ARTIFACT: ARRANGEMENT_GATES_REPORT
- MUST:
  - report_id
  - version
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
- Minimum required gates:
  - G1_PALETTE_EMPTY (S0)
  - G2_SECTION_ASSIGNMENT_EMPTY (S0)
  - G3_REGISTER_POLICY_MISSING (S0)
  - G4_DENSITY_MAP_EMPTY (S0)
  - G5_ROLE_COVERAGE_MISSING (S1)
  - G6_REGISTER_COLLISION_RISK (S1)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/ARRANGEMENT/ARRANGEMENT_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load structure plan and optional harmony/melody/rhythm inputs.
2) Define instrumentation palette (instruments + allowed roles).
3) Assign roles per section (lead/harmony/bass/rhythm/pad/fx/vocal space).
4) Define register and voicing policy (bounds + collision rules).
5) Define texture density map per section (aligned to tension curve if present).
6) Run gates and emit artifacts.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: instrumentation palette empty.
- S0-2: section role assignment empty.
- S0-3: register/voicing policy missing.
- S0-4: density map missing.
- S0-5: produced artifacts missing schemas/storage targets.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- structure defines sections
- harmony/melody/rhythm define musical material constraints
- lyrics/vocal needs can request “vocal space” (optional)

Downstream:
- vocal performance engine uses arrangement constraints to shape delivery
- sound design engine can add FX layers (separate engine 10)
- mix/master engine finalizes loudness and balance

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family template:
  09_SOUND_MUSIC_ENGINES/00__TEMPLATE__ENGINE__SOUND_MUSIC_ENGINES.md
- Family README:
  09_SOUND_MUSIC_ENGINES/00__README__SOUND_MUSIC_ENGINES.md

--- END.

LOCK: OPEN
