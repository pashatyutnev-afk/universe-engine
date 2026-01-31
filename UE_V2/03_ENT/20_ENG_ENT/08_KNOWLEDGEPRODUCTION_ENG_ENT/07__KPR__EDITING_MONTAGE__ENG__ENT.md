# EDITING & MONTAGE ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/07__EDITING_MONTAGE_ENG.md
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
UID: UE.ENG.PROD.KP.EDITING.MONTAGE.001
OWNER: SYSTEM
ROLE: Defines deterministic editing/montage specs: screen-time sequencing, cut rhythm rules, continuity editing constraints, montage patterns, and validation gates. Consumes clips/shots and produces edit decision artifacts without owning story-time pacing or deep music composition.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Editing & Montage Engine created: edit decision schema, montage pattern library, cut rhythm rules, and validation gates."
- REASON: "Production needs a separate owner for screen-time rhythm and cut logic, distinct from narrative pacing."
- IMPACT: "Edits become reproducible, auditable, and compatible with upstream constraints."
- CHANGE_ID: UE.CHG.2026-01-08.PROD.KP.EDITING.MONTAGE.001

---

## 0) PURPOSE (LAW)
This engine owns **SCREEN-TIME editing & montage**:
- ordering of clips/shots on the timeline (screen-time, not story-time)
- cut rhythm constraints (pace of cuts, hold times)
- montage pattern selection (match cuts, jump cuts, parallel montage)
- continuity editing constraints (axis, match action, eyeline)
- outputs edit decision artifacts and gates against rhythm/continuity breaks

Hard rule:
- Story-time rhythm belongs to Narrative Pacing engine; this engine owns screen-time rhythm.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- define story-time order or causal logic (narrative/expression engines)
- define camera shot plan (camera engine)
- define lighting/art style (their engines)
- define deep music composition/harmony (sound music family)
- define final sound design mix/master as primary (sound production engine covers placement/clarity)

FORBIDDEN:
- rewriting story structure via edits without explicit story-time schedule reference
- claiming ownership of narrative pacing primitives

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- VIDEO_BATCH_PLAN (optional)
- VIDEO_CLIP_BLUEPRINT (optional)
- SHOT_PLAN (optional)
- EVENT_SCHEDULE (optional; for story-time alignment only)
- GENRE_PROFILE (optional)
- ATMOSPHERE_LAYER_SPEC / RESONANCE_PROFILE (optional)
- EDIT_REQUEST (optional: target deliverable)

PRODUCES:
- EDIT_DECISION_LIST (EDL_SPEC)
- MONTAGE_PATTERN_LIBRARY
- CUT_RHYTHM_PROFILE
- EDITING_GATES_REPORT

DEPENDS_ON:
- [] (may consume camera/video artifacts but not required)
(soft) [05_EXPRESSION_ENGINES/08__EVENT_SCHEDULING_ENG] for story-time alignment refs

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/PRODUCTION/VIDEO/EDITING/
OPTIONAL:
- KB/PRODUCTION/VIDEO/EDITING (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Screen-time: the timeline as experienced by the audience.
- Story-time: narrative chronology (external reference only).
- EDL Spec: structured edit decision list (clip order, in/out, transitions, notes).
- Cut Rhythm: distribution of shot lengths (holds) and cut density.
- Montage Pattern: named editing pattern with constraints and usage conditions.
- Continuity Editing: rules that preserve spatial/temporal coherence (or intentionally break it with label).

Enums (baseline):
- transition: CUT|DISSOLVE|FADE|WIPE|MATCH_CUT|JUMP_CUT
- rhythm_mode: STEADY|ACCELERATING|DECELERATING|PUNCTUATED|CHAOTIC_CONTROLLED
- continuity_mode: STRICT|STYLED|DISRUPTIVE
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- screen-time sequencing and transitions
- cut rhythm constraints and profiles
- montage pattern library
- continuity editing constraints and intentional breaks
- validation gates (continuity/rhythm/constraint drift)

OUT OF SCOPE (HARD):
- story-time pacing and narrative beat rhythm (narrative pacing engine)
- camera shot design (camera engine)
- deep music composition (sound music family)
- production audio placement/clarity as primary (next engine 08)

COLLISION RULE:
- If request is “story-time pacing / dramatic rhythm” → `02_DOMAIN_NARRATIVE_ENGINES/05__PACING_RHYTHM_ENG`
- If request is “shot plan / lens / movement” → camera engine
- If request is “music composition choices” → 09_SOUND_MUSIC_ENGINES/*
- If request is “dialogue mix / SFX placement clarity” → `08__SOUND_MUSIC_ENG` (production layer)

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: EDL_SPEC defines ordered clips with in/out and transitions.
R2 (HARD) MUST: CUT_RHYTHM_PROFILE defines hold bounds and rhythm mode per segment.
R3 (HARD) MUST: MONTAGE_PATTERN_LIBRARY defines patterns with when-to-use/when-forbidden.
R4 (HARD) MUST: continuity mode declared; if DISRUPTIVE, breaks must be labeled and justified.
R5 (HARD) FORBIDDEN: silently changing story-time order (must reference EVENT_SCHEDULE if alignment matters).
R6 (SOFT) SHOULD: include “breathing room” rules to avoid constant cut density unless genre demands.
R7 (HARD) MUST: gates detect illegal breaks (unlabeled discontinuity) and rhythm violations.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: EDIT_DECISION_LIST (EDL_SPEC)
- MUST:
  - edl_id
  - version
  - timeline_fps (optional)
  - continuity_mode (STRICT|STYLED|DISRUPTIVE)
  - items[] (non-empty)
  - global_rules_refs[] (optional)
  - checks[] (non-empty)
- ITEM (minimum):
  - item_id
  - source_clip_id (or shot_id)
  - order_index
  - in_point (timecode or seconds proxy)
  - out_point (timecode or seconds proxy)
  - transition_out (CUT|DISSOLVE|FADE|WIPE|MATCH_CUT|JUMP_CUT)
  - audio_placeholder (optional: VO|SFX|MUSIC|SILENCE)
  - continuity_notes (optional)
  - intentional_break (optional):
    - enabled (bool)
    - type (TIME_JUMP|SPACE_BREAK|AXIS_BREAK|STYLE_BREAK)
    - justification (required if enabled)
  - notes
- VALIDATION:
  - items ordered and non-empty
  - in_point < out_point (proxy validation)
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/VIDEO/EDITING/EDIT_DECISION_LIST.md

---

ARTIFACT: CUT_RHYTHM_PROFILE
- MUST:
  - rhythm_id
  - version
  - rhythm_mode (STEADY|ACCELERATING|DECELERATING|PUNCTUATED|CHAOTIC_CONTROLLED)
  - hold_bounds_seconds (min,max)
  - segment_profiles[] (optional)
  - anti_patterns[] (non-empty)
  - checks[] (non-empty)
- SEGMENT PROFILE (optional):
  - segment_id
  - applies_to_item_ids[] (optional)
  - hold_bounds_seconds (min,max)
  - target_cut_density (optional proxy)
  - notes
- VALIDATION:
  - hold bounds valid
  - anti_patterns non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/VIDEO/EDITING/CUT_RHYTHM_PROFILE.md

---

ARTIFACT: MONTAGE_PATTERN_LIBRARY
- MUST:
  - library_id
  - version
  - patterns[] (non-empty)
  - checks[] (non-empty)
- PATTERN (minimum):
  - pattern_id
  - name
  - description (testable)
  - allowed_transitions[] (non-empty)
  - when_to_use (testable)
  - when_forbidden (optional)
  - continuity_mode_compatibility[] (STRICT|STYLED|DISRUPTIVE)
  - risks[] (optional)
- VALIDATION:
  - patterns non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/VIDEO/EDITING/MONTAGE_PATTERN_LIBRARY.md

---

ARTIFACT: EDITING_GATES_REPORT
- MUST:
  - report_id
  - version
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
- Minimum required gates:
  - G1_EDL_EMPTY (S0)
  - G2_IN_OUT_INVALID (S0)
  - G3_RHYTHM_BOUNDS_INVALID (S0)
  - G4_UNLABELED_CONTINUITY_BREAK (S1)
  - G5_STORYTIME_REORDER_UNDECLARED (S1)
  - G6_PATTERN_LIBRARY_EMPTY (S0)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/PRODUCTION/VIDEO/EDITING/EDITING_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load clips/shots (and optional story-time schedule for reference).
2) Choose continuity mode and montage patterns.
3) Build cut rhythm profile (bounds + mode + anti-patterns).
4) Assemble EDL:
   - ordered items with in/out and transitions
   - label any intentional breaks
5) Run gates:
   - empty EDL, invalid in/out, rhythm bounds invalid, unlabeled breaks
6) Emit artifacts.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: EDL items[] empty.
- S0-2: any item has invalid in/out.
- S0-3: rhythm bounds invalid.
- S0-4: pattern library empty.
- S0-5: produced artifacts missing schemas/storage targets.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- video generation provides clip candidates
- camera engine provides shot plan
- style/resonance can constrain rhythm feel (as constraints only)

Downstream:
- `08__SOUND_MUSIC_ENG` (production audio placement/design) aligns audio placeholders to edit
- delivery/export pipelines consume EDL and rhythm profile
- narrative engines may validate story-time coherence using event schedule refs

Critical boundary:
- story-time rhythm belongs to Narrative Pacing engine; this engine owns screen-time rhythm.

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Narrative pacing boundary:
  02_DOMAIN_NARRATIVE_ENGINES/05__PACING_RHYTHM_ENG.md
- Family template:
  08_KNOWLEDGE_PRODUCTION_ENGINES/00__TEMPLATE__ENGINE__KNOWLEDGE_PRODUCTION_ENGINES.md
- Family README:
  08_KNOWLEDGE_PRODUCTION_ENGINES/00__README__KNOWLEDGE_PRODUCTION_ENGINES.md

--- END.

LOCK: OPEN
