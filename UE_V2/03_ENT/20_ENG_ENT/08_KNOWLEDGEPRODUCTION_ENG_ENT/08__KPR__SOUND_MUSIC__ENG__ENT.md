# SOUND & MUSIC ENGINE (PRODUCTION LAYER) (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/08__SOUND_MUSIC_ENG.md
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 08_KNOWLEDGE_PRODUCTION_ENGINES
CLASS: PRODUCTION (L3)
LEVEL: L3
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.PROD.KP.SOUND.PRODUCTION.001
OWNER: SYSTEM
ROLE: Defines deterministic production-audio specs: dialogue intelligibility rules, SFX/ambience placement, sync cues, audio scene layers, loudness/clarity guardrails (abstract), and validation gates. Does not own deep music composition/harmony/arrangement.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Production Sound & Music Engine created: audio layer plan schema, placement rules, clarity guardrails, and gates. Deep music explicitly excluded."
- REASON: "Production needs ownership of sync/design/placement/clarity; composition belongs to 09_SOUND_MUSIC_ENGINES."
- IMPACT: "Audio becomes auditable and consistent with edits and scene intent."
- CHANGE_ID: UE.CHG.2026-01-08.PROD.KP.SOUND.PRODUCTION.001

---

## 0) PURPOSE (LAW)
This engine owns **PRODUCTION AUDIO** (sync/design/placement/clarity):
- dialogue intelligibility and priority rules
- SFX placement and category constraints
- ambience layers and environmental bed rules
- sync cue mapping to edit/clip timeline
- loudness/clarity guardrails (abstract, vendor-neutral)
- validation gates to prevent mud/clutter and mis-prioritization

Hard rule:
- This engine does NOT compose music (harmony/melody/arrangement/vocal/mix-master) — that belongs to `09_SOUND_MUSIC_ENGINES/*`.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- compose music themes, chord progressions, melodies, arrangements (09 family)
- do final mix/master engineering as deep craft (09 has Mix/Master; here only guardrails and placement plan)
- define editing/montage (editing engine)
- define camera/visual style (visual engines)
- write narrative content

FORBIDDEN:
- “write the soundtrack” tasks
- claiming ownership of deep music theory outputs

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- EDIT_DECISION_LIST (EDL_SPEC) (recommended)
- VIDEO_CLIP_BLUEPRINT / clip list (optional)
- SCENE_PACK (optional)
- ATMOSPHERE_LAYER_SPEC (optional)
- RESONANCE_PROFILE (optional)
- AUDIO_REQUEST (optional)

PRODUCES:
- AUDIO_LAYER_PLAN
- AUDIO_PLACEMENT_RULESET
- SYNC_CUE_MAP
- AUDIO_GATES_REPORT

DEPENDS_ON:
- [08_KNOWLEDGE_PRODUCTION_ENGINES/07__EDITING_MONTAGE_ENG]
(soft) [06_GENRE_STYLE_ENGINES/02__ATMOSPHERE_ENG, 06_GENRE_STYLE_ENGINES/03__EMOTIONAL_RESONANCE_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/PRODUCTION/AUDIO/
OPTIONAL:
- KB/PRODUCTION/AUDIO (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Audio Layer: DIALOGUE, SFX, AMBIENCE, MUSIC_BED (placeholder), FOLEY, UI_SFX.
- Placement: where layers appear in time and how they prioritize.
- Sync Cue: explicit cue aligned to timecodes or clip markers.
- Intelligibility: dialogue clarity threshold (abstract proxy).
- Masking: frequency/time collision that hides priority elements (proxy checks).
- Guardrail: constraint preventing overload (too many layers, too loud, too dense).

Enums (baseline):
- layer_type: DIALOGUE|SFX|AMBIENCE|MUSIC_BED|FOLEY|UI_SFX
- priority: P1|P2|P3
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- production audio planning (layers, placement, sync cues)
- clarity/priority guardrails and validation
- rulesets for dialogue/SFX/ambience balance (abstract)

OUT OF SCOPE (HARD):
- composing music (09 family)
- deep mixing/mastering craft beyond guardrails
- editing cuts and montage patterns

COLLISION RULE:
- If request is “compose melody/harmony/arrangement” → `09_SOUND_MUSIC_ENGINES/*`
- If request is “final master chain specifics” → `09_SOUND_MUSIC_ENGINES/13__MIX_MASTER_ENG.md`
- If request is “cut rhythm changes” → editing/montage engine
- If request is “soundtrack theme” → `09_SOUND_MUSIC_ENGINES/01__MUSIC_COMPOSITION_ENG.md`

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: AUDIO_LAYER_PLAN defines layer stack by segment/time window.
R2 (HARD) MUST: AUDIO_PLACEMENT_RULESET enforces priority (dialogue P1 by default unless explicitly overridden).
R3 (HARD) MUST: SYNC_CUE_MAP aligns cues to EDL items/time markers when EDL is provided.
R4 (HARD) MUST: guardrails prevent masking of P1 layer and prevent layer overload.
R5 (HARD) FORBIDDEN: outputting deep music composition artifacts (melody/chords/arrangement).
R6 (SOFT) SHOULD: include “silence windows” policy to support clarity and rhythm.
R7 (HARD) MUST: gates detect missing dialogue plan (if dialogue exists), missing sync cues for required beats, and overload.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: AUDIO_LAYER_PLAN
- MUST:
  - plan_id
  - version
  - segments[] (non-empty)
  - default_priority_policy (required)
  - guardrails (required)
  - checks[] (non-empty)
- SEGMENT (minimum):
  - segment_id
  - applies_to (edl_item_ids[] optional OR time_window)
  - layers[] (non-empty)
  - notes
- LAYER ENTRY (minimum):
  - layer_id
  - layer_type (DIALOGUE|SFX|AMBIENCE|MUSIC_BED|FOLEY|UI_SFX)
  - priority (P1|P2|P3)
  - density_target (0..100)
  - placement_notes (testable)
  - allowed_overlap_with[] (optional layer types)
- DEFAULT PRIORITY POLICY (minimum):
  - dialogue_priority (P1 default)
  - override_conditions (testable)
- GUARDRAILS (minimum):
  - max_simultaneous_layers (integer)
  - max_density_p2_p3 (0..100)
  - p1_masking_forbidden (bool)
- VALIDATION:
  - segments non-empty
  - each segment has layers
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/AUDIO/AUDIO_LAYER_PLAN.md

---

ARTIFACT: AUDIO_PLACEMENT_RULESET
- MUST:
  - ruleset_id
  - version
  - rules[] (non-empty)
  - checks[] (non-empty)
- RULE (minimum):
  - rule_id
  - type (MUST|FORBIDDEN|ALLOWED)
  - scope (GLOBAL|SEGMENT)
  - statement (testable)
  - severity_if_broken (S0|S1|S2|S3)
- VALIDATION:
  - rules non-empty
  - at least one FORBIDDEN rule (anti-masking / anti-overload)
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/AUDIO/AUDIO_PLACEMENT_RULESET.md

---

ARTIFACT: SYNC_CUE_MAP
- MUST:
  - cue_map_id
  - version
  - time_base (TIMECODE|SECONDS_PROXY)
  - cues[] (non-empty)
  - checks[] (non-empty)
- CUE (minimum):
  - cue_id
  - cue_type (SFX_HIT|AMB_SHIFT|DIALOGUE_BEAT|MUSIC_BED_ENTRY|MUSIC_BED_EXIT|SILENCE_WINDOW)
  - target (edl_item_id or time)
  - instruction (testable)
  - priority (P1|P2|P3)
  - severity_if_missing (S0|S1|S2|S3)
- VALIDATION:
  - cues non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/AUDIO/SYNC_CUE_MAP.md

---

ARTIFACT: AUDIO_GATES_REPORT
- MUST:
  - report_id
  - version
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
- Minimum required gates:
  - G1_LAYER_PLAN_EMPTY (S0)
  - G2_RULESET_EMPTY (S0)
  - G3_SYNC_CUES_EMPTY_WHEN_REQUIRED (S1)
  - G4_P1_MASKING_RISK (S0)
  - G5_LAYER_OVERLOAD (S1)
  - G6_DEEP_MUSIC_LEAK (S1)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/AUDIO/AUDIO_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load EDL/time windows and optional scene/style context.
2) Build audio layer plan:
   - segments with layer stacks and priority
3) Build placement ruleset:
   - must/forbidden constraints (clarity, masking, overload)
4) Build sync cue map:
   - cues aligned to EDL items/time markers
5) Run gates:
   - empty plans/rules, masking risk, overload, deep-music leak
6) Emit artifacts.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: AUDIO_LAYER_PLAN segments empty.
- S0-2: ruleset empty.
- S0-3: P1 masking risk (dialogue unintelligible) detected.
- S0-4: produced artifacts missing schemas/storage targets.
- S0-5: outputs include deep music composition artifacts.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- editing engine provides EDL structure
- style/atmosphere/resonance provide feel constraints (optional)

Downstream:
- sound music family (09) can supply composed music assets that are then placed under this plan
- QA validates audio clarity and masking guardrails
- final production pipeline implements layer plan and sync cues

Critical boundary:
- production audio here; deep music composition and mix/master craft in 09 family.

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family template:
  08_KNOWLEDGE_PRODUCTION_ENGINES/00__TEMPLATE__ENGINE__KNOWLEDGE_PRODUCTION_ENGINES.md
- Family README:
  08_KNOWLEDGE_PRODUCTION_ENGINES/00__README__KNOWLEDGE_PRODUCTION_ENGINES.md
- Deep music boundary:
  09_SOUND_MUSIC_ENGINES/*

--- END.

LOCK: OPEN
