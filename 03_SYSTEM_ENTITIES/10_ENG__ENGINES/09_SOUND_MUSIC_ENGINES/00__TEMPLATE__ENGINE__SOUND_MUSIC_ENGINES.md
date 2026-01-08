# SOUND & MUSIC ENGINES — ENGINE TEMPLATE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/00__TEMPLATE__ENGINE__SOUND_MUSIC_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: TEMPLATE
FAMILY: 09_SOUND_MUSIC_ENGINES
CLASS: SOUND (L3)
LEVEL: L3
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.SOUND.TPL.ENGINE.001
OWNER: SYSTEM
ROLE: Mandatory template for SOUND & MUSIC engines (deep music). Enforces canonical header schema, mini-contract law, strict boundaries vs Production Audio, output schemas for composition/arrangement/mix, and raw-only references.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Sound & Music engine template standardized: deep-music ownership, strict separation from production audio, schemas, gates, and S0 blockers."
- REASON: "Stop mixing production audio placement (08) with deep music creation (09)."
- IMPACT: "Music engines become composable, auditable, and safely reusable across formats and productions."
- CHANGE_ID: UE.CHG.2026-01-08.SOUND.TPL.ENGINE.001

---

## 0) HOW TO USE (MANDATORY)

1) Copy this template to create a new engine file in this family.
2) Replace placeholders strictly (title, FILE path, UID, ROLE).
3) Fill MINI-CONTRACT with concrete artifacts (no vague words).
4) Declare boundaries to avoid overlap with:
   - CORE (system identity/state/lifecycle)
   - GOVERNANCE (authority/pipeline/audit)
   - STYLE (tone/mood as constraints owner)
   - KNOWLEDGE PRODUCTION (execution + production audio placement)
5) Output must be deep music artifacts with schemas (composition/harmony/arrangement/vocal/mix).

Rule:
- Missing required sections => engine is incomplete (non-canon).

---

## 1) ENGINE FILE TEMPLATE (COPY FROM HERE)

# <ENGINE TITLE> (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/NN__<ENGINE_NAME>_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 09_SOUND_MUSIC_ENGINES
CLASS: SOUND (L3)
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 0.1.0
UID: UE.ENG.SOUND.<ENGINE_KEY>.001
OWNER: SYSTEM
ROLE: <one sentence: what deep-music capability this engine defines and guarantees>

CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR|MIGRATION|EMERGENCY
- SUMMARY: "<what changed / what was defined>"
- REASON: "<why>"
- IMPACT: "<what this affects>"
- CHANGE_ID: UE.CHG.YYYY-MM-DD.SOUND.<ENGINE_KEY>.<SEQ>

---

## 0) PURPOSE (LAW)

- Define the deep music capability this engine owns (strict).
- Define guarantees (bullets).
- Define non-goals (explicit).

---

## 1) NON-GOALS (HARD)

This engine does NOT:
- place/align sounds to picture as production audio execution (08 owns)
- define camera/editing/scene execution (08 owns)
- define narrative meaning/structure as primary (02 owns)
- define character psychology/dialogue as primary (03 owns)
- define world laws as primary (04 owns)
- define tone/mood as authority (06 owns constraints)
- define authority/pipeline/audit/memory/versioning (00 governance owns)
- define system identity/state/lifecycle (01 core owns)

Critical boundary:
- 08 “Sound & Music (Production Layer)” = sync/design/placement/clarity
- 09 “Sound & Music” = composition/harmony/arrangement/vocal/mix/master

---

## 2) MINI-CONTRACT (MANDATORY)

CONSUMES:
- <1–7 inputs; named artifacts>
  - Example: STYLE_PROFILE, SCENE_INTENT, EMOTIONAL_ARC, TIMING_BUDGET, REFERENCE_TRACKS

PRODUCES:
- <1–7 outputs; deep music artifacts>
  - Example: COMPOSITION_SKETCH, SONG_STRUCTURE, HARMONY_MAP, MELODY_HOOKS, ARRANGEMENT_PLAN, VOCAL_GUIDE, MIX_MASTER_SPEC

DEPENDS_ON:
- <engine paths> or []
  - (Music engines may consume style constraints, narrative intent, and timing budgets)

OUTPUT_TARGET:
MANDATORY:
- <project output targets, e.g. 05_PROJECTS/.../MUSIC.md or asset paths>

OPTIONAL:
- <assistive notes; never overrides canon>

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)

Deep music artifacts may include:
- structure: sections, motifs, hooks
- harmony: chord progressions, harmonic rhythm
- melody: motifs, contour constraints
- rhythm/groove: pulse, subdivision, groove rules
- lyrics: themes, rhyme/meter constraints (if applicable)
- arrangement: instrumentation, density curve, register plan
- vocal performance: delivery rules, range, articulation
- mix/master: clarity targets, loudness targets, dynamic range targets

Do not define:
- shot-by-shot sound placement (production audio)
- editing cut decisions (montage)
- narrative plot decisions

---

## 4) BOUNDARIES (ANTI-DUPLICATION)

IN SCOPE:
- creating and structuring music as an authored system
- consistent musical identity across episodes/chapters
- transforming constraints into composition/mix plans

OUT OF SCOPE (HARD):
- picture sync and placement of audio events to timeline (08)
- production audio problem-solving (noise cleanup, sync, placement) (08)
- defining tone/mood as the authority (06 supplies constraints)

Collision rule:
- If asked “where exactly this sound hits in the edit” → route to 08.
- If asked “compose the theme/harmony/motif” → 09 owns.

---

## 5) RULESET (THE LAW)

Write numbered rules using MUST/FORBIDDEN/ALLOWED:
- R1 (HARD): ...
- R2 (HARD): ...
- R3 (SOFT): ...

Include:
- strict sets (allowed keys/modes, allowed tempo ranges, allowed instrumentation sets) if needed
- invariants (motif consistency across tracks)
- stop conditions (blockers)

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

For each produced artifact:

ARTIFACT: <NAME>
- MUST: <fields list>
- OPTIONAL: <fields list>
- VALIDATION: <how to detect missing/invalid>
- STORAGE: <target path rule>

Example:
ARTIFACT: SONG_STRUCTURE
- MUST: sections[], section_lengths, tempo_map?, key_map?, motif_refs[]
- VALIDATION: empty sections => invalid

---

## 7) PROCESS (DETERMINISTIC)

1) Validate constraints (style + timing + intent)
2) Compose / design structure (motifs, sections)
3) Define harmony/melody/rhythm rulesets
4) Arrangement plan (instrumentation + density)
5) Vocal/lyrics design (if applicable)
6) Mix/master targets (spec level)
7) Emit artifacts with schemas

---

## 8) QUALITY GATES (MANDATORY)

G1 — Boundary Gate:
- no production placement instructions as primary output

G2 — Schema Gate:
- outputs conform to schemas

G3 — Consistency Gate:
- motif/key/tempo constraints consistent (unless intentionally varied)

G4 — Handoff Gate:
- outputs are consumable by production layer (08) as constraints/specs

---

## 9) S0 BLOCKERS (STOP)

S0-1: Engine outputs production audio placement plan as primary (08 breach)  
S0-2: Engine overwrites style constraints silently (06 breach)  
S0-3: Output artifacts have no schemas where required  
S0-4: Hidden dependencies not declared  
S0-5: Engine numbering mismatch vs index/filename  

---

## 10) INTEGRATION (SYSTEM FIT)

Upstream inputs:
- Style constraints (06)
- Narrative/scene intent (02)
- Format/timing budgets (07)
- Production needs (08) as constraints request (not as owner)

Downstream consumers:
- Production audio layer and implementation engines (08)
- Release/output assembly in projects/assets

---

## 11) REFERENCES (RAW ONLY) (OPTIONAL)

- <raw links>

--- END.

---

## 2) TEMPLATE QUALITY CHECK (FAST)

Before setting a new engine ACTIVE:
- [ ] Header schema correct
- [ ] MINI-CONTRACT concrete
- [ ] Boundary with 08 is explicit
- [ ] Output schemas defined
- [ ] S0 blockers listed
