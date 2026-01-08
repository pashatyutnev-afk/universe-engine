# ENGINE TEMPLATE — SOUND & MUSIC ENGINES (ENG)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/00__TEMPLATE__ENGINE__SOUND_MUSIC_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
ENTITY_CLASS: ENG
ENGINE_FAMILY: 09_SOUND_MUSIC_ENGINES
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.ENG.MUSIC.ENGINE.001
OWNER: SYSTEM
ROLE: Canonical template for deep sound & music ENG engines (composition, structure, harmony, melody, rhythm, lyrics, arrangement, vocal, sound design, mixing/mastering)

---

## 0) IDENTITY (REQUIRED)
ENGINE_NAME: <DISPLAY_NAME>
ENGINE_CODE: <SHORT_CODE>                         # MUSIC_COMPOSITION | HARMONY_CHORD | MIX_MASTER | etc.
ENGINE_NUMBER: <NN>                               # must match filename NN__
ENGINE_FILE_NAME: <NN__NAME_ENG.md>
ENGINE_UID: <UE.ENG.MUSIC.<CODE>.NNN>

MUSIC_OBJECT:
- what musical layer it owns (1 line)
- what it guarantees (1 line)

---

## 1) PURPOSE (LAW)
Зачем этот deep-music движок существует:
- какую музыкальную функцию он строит (композиция/гармония/аранж/вокал/микс)
- какой тип музыкальных ошибок предотвращает
- какие артефакты музыки выдаёт как “контракт”

---

## 2) CRITICAL BOUNDARY (ANTI-DUP) — ABSOLUTE
OWNED HERE (DEEP MUSIC):
- composition and musical form
- harmony/chords, melody/hook
- rhythm/groove and meter
- lyrics and vocal performance (as music)
- arrangement/instrumentation
- sound design as musical layer
- mixing/mastering (music finalization)
- music-to-scene mapping (emotional scoring logic)

NOT OWNED HERE (PRODUCTION AUDIO):
- dialogue sync/clarity/placement
- foley placement and mix as production utility
- audio leveling for video deliverable
- production sound pipeline checklists
These belong to: 08_KNOWLEDGE_PRODUCTION_ENGINES (production audio).

If an output is primarily "dialogue clarity / sync / placement" — it is NOT this family.

---

## 3) INPUTS / OUTPUTS (MINI-CONTRACT) — REQUIRED
CONSUMES:
- <ARTIFACT_TYPE or UID>
- ...

PRODUCES:
- <ARTIFACT_TYPE or UID>
- ...

MUSIC_OUTPUT (REQUIRED):
- OUTPUT_OBJECT: <Track Spec | Score Blueprint | Harmony Map | Lyric Sheet | Arrangement Chart | Mix Notes | Master Spec>
- OUTPUT_SCHEMA (hard):
  - field: <name> | type: <type> | required: <yes/no> | rules: <short>
  - ...
- OUTPUT_INVARIANTS (hard):
  - <invariant 1>
  - <invariant 2>

DEPENDS_ON:
- <ENG_UID>
- ...

OUTPUT_TARGET:
- <where projects store music artifacts> (descriptive, no path-nav)

---

## 4) MUSIC CONTRACT (HARD) — REQUIRED
STYLE IDENTITY:
- genre/style references (conceptual):
- mood/emotion targets:
- tempo range (if relevant):
- tonal center / mode (if relevant):

FORM / STRUCTURE (if relevant):
- macro form: (A/B/verse-chorus/etc)
- section list:
- transitions rules:

HARMONY / CHORDS (if relevant):
- chord language:
- tension rules:
- resolution rules:

MELODY / HOOK (if relevant):
- motif rules:
- hook constraints:
- memorability target:

RHYTHM / GROOVE (if relevant):
- groove type:
- meter rules:
- syncopation limits:

LYRICS (if relevant):
- theme:
- voice persona:
- rhyme/meter constraints:
- forbidden content (if any):

ARRANGEMENT / INSTRUMENTATION (if relevant):
- instrument palette:
- density curve:
- register rules:

VOCAL PERFORMANCE (if relevant):
- vocal tone:
- articulation:
- dynamic range:

SOUND DESIGN (if relevant):
- sonic palette:
- synthesis/noise rules:
- signature sounds:

MIX / MASTER (if relevant):
- loudness targets (conceptual):
- dynamic range intent:
- stereo field intent:
- deliverable variants:

---

## 5) MUSIC GATES (HARD) — REQUIRED
GATE LIST:
- GATE: <name>
  CHECK: <how to verify>
  FAIL SIGNAL: <what indicates failure>
  FIX STRATEGY: <how to fix>

MINIMUM MUSIC GATES (default set):
- musical coherence (parts fit: harmony/melody/rhythm)
- motif continuity (themes don’t randomly change)
- emotional alignment (music matches target emotion)
- production readiness (deliverable spec is actionable)
- boundary compliance (not drifting into production-audio tasks)

---

## 6) EXAMPLES (REQUIRED)
GOOD EXAMPLE:
- <structured example snippet of output schema + why passes gates>

BAD EXAMPLE:
- <counterexample>
- why fails: <gate list>

---

## 7) FAILURE MODES & EDGE CASES
FAILURES:
- Failure:
  CAUSE:
  RECOVERY:

EDGE CASES:
- Case:
  Handling:

---

## 8) REL / XREF (UID-FIRST)
REL:
- REL: <REL_TYPE> | TARGET: <UID> | WHY: <reason>

XREF:
- XREF: <UID> | WHY: <reason>

RULE:
- No PATH navigation inside content.
- If clickable references are needed, keep them in registries/indexes as RAW.

---

## 9) CHANGE NOTES (OPTIONAL)
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR
- SUMMARY:
- REASON:
- IMPACT:

--- END.
