# ENGINE TEMPLATE — PRODUCTION FORMAT ENGINES (ENG)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/07_PRODUCTION_FORMAT_ENGINES/00__TEMPLATE__ENGINE__PRODUCTION_FORMAT_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
ENTITY_CLASS: ENG
ENGINE_FAMILY: 07_PRODUCTION_FORMAT_ENGINES
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.ENG.FORMAT.ENGINE.001
OWNER: SYSTEM
ROLE: Canonical template for production format ENG engines (genre, blending, adaptation, book/series/short/youtube/game)

---

## 0) IDENTITY (REQUIRED)
ENGINE_NAME: <DISPLAY_NAME>
ENGINE_CODE: <SHORT_CODE>                       # GENRE | GENRE_BLENDING | FORMAT_ADAPTATION | BOOK_FORMAT | SERIES_EPISODE | SHORT_CONTENT | YOUTUBE_LONGFORM | GAME_NARRATIVE
ENGINE_NUMBER: <NN>                             # must match filename NN__
ENGINE_FILE_NAME: <NN__NAME_ENG.md>
ENGINE_UID: <UE.ENG.FORMAT.<CODE>.NNN>

FORMAT_OBJECT:
- owned format capability (1 line)
- what it guarantees (1 line)

---

## 1) PURPOSE (LAW)
Зачем этот движок существует:
- какой формат/упаковку он задаёт
- какие ограничения носителя он “фиксирует”
- какие выходы он стандартизирует (chapters/episodes/shorts/quests)

---

## 2) DOMAIN BOUNDARY (ANTI-DUP) — REQUIRED
OWNED HERE:
- format contracts (structure, length, cadence, packaging)
- adaptation rules between formats (loss/keep/transform)
- deliverables definitions for a format

NOT OWNED HERE:
- story logic / scene construction (02_DOMAIN_NARRATIVE_ENGINES)
- character psychology/voice (03_DOMAIN_CHARACTER_ENGINES)
- world law (04_DOMAIN_WORLD_ENGINES)
- visual/audio technical production (08_KNOWLEDGE_PRODUCTION_ENGINES)

INTERFACES:
- Narrative interface: how format constrains story structure
- Production interface: what deliverables downstream engines consume
- Marketing interface: how packaging affects distribution (without owning marketing)

---

## 3) INPUTS / OUTPUTS (MINI-CONTRACT) — REQUIRED
CONSUMES:
- <ARTIFACT_TYPE or UID>
- ...

PRODUCES:
- <ARTIFACT_TYPE or UID>
- ...

FORMAT_OUTPUT (REQUIRED):
- OUTPUT_OBJECT: <Format Contract | Release Plan | Episode Grid | Chapter Blueprint | Quest Loop Spec>
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
- <where projects store format artifacts> (descriptive, no path-nav)

---

## 4) FORMAT CONTRACT (HARD) — REQUIRED
FORMAT TYPE:
- type: <BOOK|SERIES|SHORT|YOUTUBE|GAME|OTHER>
- primary unit: <chapter|episode|short|video|quest>
- secondary units: <scenes|beats|segments|loops>

STRUCTURE:
- macro structure: <e.g., seasons/acts/chapters/levels>
- unit structure: <beat grid per unit>
- required beats: <list>
- optional beats: <list>
- forbidden patterns: <list>

LENGTH & DURATION:
- target duration: <range>
- min/max hard limits:
- pacing constraints: <format-level pacing, not editing>

CADENCE / RELEASE:
- release cadence: <weekly/batch/etc>
- consistency rule: <what must remain stable>

PACKAGING:
- title rules:
- hook rules:
- recap rule (if any):
- cliffhanger rule (if any):
- onboarding rule (first unit):

ADAPTATION NOTES (if relevant):
- what is preserved:
- what is transformed:
- what is dropped:

---

## 5) FORMAT GATES (HARD) — REQUIRED
GATE LIST:
- GATE: <name>
  CHECK: <how to verify>
  FAIL SIGNAL: <what indicates failure>
  FIX STRATEGY: <how to fix>

MINIMUM FORMAT GATES (default set):
- structure coherence (units follow contract)
- duration compliance (inside limits)
- cadence compliance (release plan consistent)
- narrative compatibility (format does not break story clarity)
- production compatibility (deliverables usable downstream)

---

## 6) EXAMPLES (REQUIRED)
GOOD EXAMPLE:
- <structured example of a unit blueprint + why it passes gates>

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
