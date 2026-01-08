# MUSIC TO SCENE ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/12__MUSIC_TO_SCENE_ENG.md
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
UID: UE.ENG.SOUND.MUSIC.TO.SCENE.001
OWNER: SYSTEM
ROLE: Maps deep music assets to narrative/scene needs deterministically: cue intent mapping, scene-to-cue linking, hitpoint plans (abstract), and validation gates. Produces scene-cue plans without owning production sync placement or dialogue clarity.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Music To Scene Engine created: scene-cue mapping schema, intent linking, hitpoint plan (abstract), and gates."
- REASON: "Need a deterministic bridge between narrative moments and composed music assets."
- IMPACT: "Music usage becomes consistent and auditable before production placement."
- CHANGE_ID: UE.CHG.2026-01-08.SOUND.MUSIC.TO.SCENE.001

---

## 0) PURPOSE (LAW)
This engine owns **MUSIC → SCENE mapping**:
- links scenes/scene-windows to cue types and themes/motifs
- defines cue intent for each scene window (tension build, reveal, catharsis)
- defines hitpoint plans as abstract markers (not timeline placement)
- emits gates against missing coverage and contradictory cue intents

Hard rule:
- This engine plans mapping and hitpoints abstractly; production sync placement belongs to production audio engine.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- place cues on exact timestamps in EDL (production sound engine)
- edit montage timing (editing engine)
- compose new music (composition engine)
- mix/master audio (mix/master engine)
- write narrative content

FORBIDDEN:
- outputting exact timecode placements as primary output (only abstract markers / scene-window refs)

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- SCENE_PACK (recommended)
- EVENT_SCHEDULE (optional)
- CUE_TAXONOMY (recommended)
- THEME_MOTIF_BIBLE (optional)
- CUE_STRUCTURE_PLAN (optional)
- RESONANCE_PROFILE (optional)
- MUSIC_ASSET_SET (optional: list of available cues)

PRODUCES:
- SCENE_CUE_MAP
- CUE_INTENT_PLAN
- HITPOINT_PLAN (ABSTRACT)
- MUSIC_TO_SCENE_GATES_REPORT

DEPENDS_ON:
- [09_SOUND_MUSIC_ENGINES/01__MUSIC_COMPOSITION_ENG]
(soft) [09_SOUND_MUSIC_ENGINES/02__SONG_STRUCTURE_ENG, 06_GENRE_STYLE_ENGINES/03__EMOTIONAL_RESONANCE_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/MUSIC/TO_SCENE/
OPTIONAL:
- KB/MUSIC/TO_SCENE (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Scene Window: bounded narrative segment that can receive a cue.
- Cue Intent: what the music must accomplish in that window (constraint).
- Hitpoint: abstract marker tied to narrative moment (turn, reveal, impact) without timecode.
- Coverage: all required scene windows have at least a cue intent (or explicit SILENCE).
- Silence Plan: intentional non-music choice as a cue policy.

Enums (baseline):
- intent_type: SUPPORT|CONTRAST|FORESHADOW|REVEAL|BUILD|RELEASE|IRONY|SILENCE
- marker_type: TURN|REVEAL|IMPACT|ENTRY|EXIT|CLIMAX_BEAT
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- mapping scenes to cue types/themes/motifs
- intent planning and coverage rules
- abstract hitpoint plans (scene-relative)

OUT OF SCOPE (HARD):
- timecode placement and sync (production sound engine)
- music composition/harmony/melody creation
- editing montage decisions

COLLISION RULE:
- If request is “place cue at 01:23:10” → production audio engine (08 production layer)
- If request is “write a new cue” → composition/structure/harmony engines
- If request is “change story beats” → narrative engines

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: SCENE_CUE_MAP maps each relevant scene window to at least one cue type or SILENCE.
R2 (HARD) MUST: CUE_INTENT_PLAN declares intent_type and constraints per scene window.
R3 (HARD) MUST: HITPOINT_PLAN defines markers per scene window (entry/exit/turn/reveal) abstractly.
R4 (HARD) FORBIDDEN: specifying exact timecodes as primary output.
R5 (HARD) MUST: gates detect missing coverage and contradictory intents (e.g., SILENCE + BUILD with no resolution rule).
R6 (SOFT) SHOULD: include reuse policy for themes/motifs (avoid random new identities).
R7 (HARD) MUST: produced artifacts have schemas and storage targets.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: SCENE_CUE_MAP
- MUST:
  - map_id
  - version
  - entries[] (non-empty)
  - checks[] (non-empty)
- ENTRY (minimum):
  - entry_id
  - scene_window_ref (scene_id/window_id)
  - recommended_cue_type (from taxonomy)
  - theme_refs[] (optional)
  - motif_refs[] (optional)
  - reuse_policy (optional: REUSE|VARIATE|NEW_ALLOWED)
  - notes
- VALIDATION:
  - entries non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/TO_SCENE/SCENE_CUE_MAP.md

---

ARTIFACT: CUE_INTENT_PLAN
- MUST:
  - plan_id
  - version
  - intents[] (non-empty)
  - conflict_rules[] (non-empty)
  - checks[] (non-empty)
- INTENT (minimum):
  - intent_id
  - scene_window_ref
  - intent_type (SUPPORT|CONTRAST|FORESHADOW|REVEAL|BUILD|RELEASE|IRONY|SILENCE)
  - constraints_summary[] (non-empty)
  - must_reference (THEME|MOTIF|FREE|NONE)
  - forbidden_reference (optional)
  - severity_if_ignored (S0|S1|S2|S3)
- VALIDATION:
  - intents non-empty
  - constraints_summary non-empty for non-SILENCE intents
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/TO_SCENE/CUE_INTENT_PLAN.md

---

ARTIFACT: HITPOINT_PLAN (ABSTRACT)
- MUST:
  - hitpoint_plan_id
  - version
  - hitpoints[] (non-empty)
  - checks[] (non-empty)
- HITPOINT (minimum):
  - hit_id
  - scene_window_ref
  - marker_type (TURN|REVEAL|IMPACT|ENTRY|EXIT|CLIMAX_BEAT)
  - description (testable)
  - required_audio_response (optional: STING|SWELL|DROP|SUSTAIN|SILENCE)
  - severity_if_missing (S0|S1|S2|S3)
- VALIDATION:
  - hitpoints non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/TO_SCENE/HITPOINT_PLAN.md

---

ARTIFACT: MUSIC_TO_SCENE_GATES_REPORT
- MUST:
  - report_id
  - version
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
- Minimum required gates:
  - G1_SCENE_MAP_EMPTY (S0)
  - G2_INTENTS_EMPTY (S0)
  - G3_HITPOINTS_EMPTY (S0)
  - G4_MISSING_COVERAGE (S0)
  - G5_CONTRADICTORY_INTENT (S1)
  - G6_TIMECODE_LEAK (S1)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/MUSIC/TO_SCENE/MUSIC_TO_SCENE_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load scene pack and cue taxonomy (+ motifs/resonance optional).
2) Build scene->cue type mapping (coverage first).
3) Build intent plan for each scene window (support/contrast/build/etc.).
4) Build abstract hitpoint plan (entry/exit/turn/reveal markers).
5) Run gates (coverage missing, contradictions, timecode leak).
6) Emit artifacts.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: scene cue map empty.
- S0-2: intents empty.
- S0-3: hitpoints empty.
- S0-4: missing coverage detected (scene windows with no cue or silence).
- S0-5: produced artifacts missing schemas/storage targets.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- composition provides cue taxonomy and motifs/themes
- narrative scene packs provide windows and beat markers

Downstream:
- production audio engine places cues on timeline using EDL + this mapping
- consistency engine can validate theme reuse across scene mappings
- mix/master finalizes audio later

Boundary:
- exact placement/sync is production layer; this is abstract intent mapping.

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Production placement boundary:
  08_KNOWLEDGE_PRODUCTION_ENGINES/08__SOUND_MUSIC_ENG.md
- Family template:
  09_SOUND_MUSIC_ENGINES/00__TEMPLATE__ENGINE__SOUND_MUSIC_ENGINES.md
- Family README:
  09_SOUND_MUSIC_ENGINES/00__README__SOUND_MUSIC_ENGINES.md

--- END.

LOCK: OPEN
