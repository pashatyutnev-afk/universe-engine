# ENGINE TEMPLATE — GENRE & STYLE ENGINES (ENG)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/06_GENRE_STYLE_ENGINES/00__TEMPLATE__ENGINE__GENRE_STYLE_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
ENTITY_CLASS: ENG
ENGINE_FAMILY: 06_GENRE_STYLE_ENGINES
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.ENG.STYLE.ENGINE.001
OWNER: SYSTEM
ROLE: Canonical template for genre/style ENG engines (tone, atmosphere, resonance, symbolism, metaphor, sensory detail)

---

## 0) IDENTITY (REQUIRED)
ENGINE_NAME: <DISPLAY_NAME>
ENGINE_CODE: <SHORT_CODE>                         # e.g., TONE_MOOD, ATMOSPHERE, SYMBOLISM
ENGINE_NUMBER: <NN>                               # must match filename NN__
ENGINE_FILE_NAME: <NN__NAME_ENG.md>
ENGINE_UID: <UE.ENG.STYLE.<CODE>.NNN>

STYLE_OBJECT:
- What style dimension it owns (1 line)
- What it guarantees (1 line)

---

## 1) PURPOSE (LAW)
Зачем этот движок существует:
- какую “настройку восприятия” он фиксирует
- что он удерживает стабильным (не даёт стилю развалиться)
- какие ошибки стиля предотвращает (разнобой тона/атмосферы/символов)

---

## 2) DOMAIN BOUNDARY (ANTI-DUP) — REQUIRED
OWNED HERE:
- tone/mood/atmosphere/resonance/symbolism/metaphor/sensory detail policies
- style constraints and style profiles

NOT OWNED HERE:
- plot/scene structure (02_DOMAIN_NARRATIVE_ENGINES)
- character psychology/voice rules (03_DOMAIN_CHARACTER_ENGINES)
- world laws/epochs/civilization (04_DOMAIN_WORLD_ENGINES)
- production technical editing/color grading (08_KNOWLEDGE_PRODUCTION_ENGINES)

INTERFACES:
- Narrative interface: how style constrains scene writing
- Character interface: how style affects voice/perception (without owning psychology)
- World interface: how style filters world presentation (without changing laws)

---

## 3) INPUTS / OUTPUTS (MINI-CONTRACT) — REQUIRED
CONSUMES:
- <ARTIFACT_TYPE or UID>
- ...

PRODUCES:
- <ARTIFACT_TYPE or UID>
- ...

STYLE_OUTPUT (REQUIRED):
- OUTPUT_OBJECT: <Style Profile | Style Pack | Tone Map | Symbol Set>
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
- <where projects store style artifacts> (descriptive, no path-nav)

---

## 4) STYLE CONTRACT (HARD) — REQUIRED
TONE & MOOD:
- baseline tone:
- variance limits: (what range is allowed)
- forbidden tone shifts:

ATMOSPHERE:
- core atmosphere signals:
- environment cues:
- pacing feel (not editing timing):

EMOTIONAL RESONANCE:
- target emotions:
- trigger patterns:
- aftertaste / residue:

SYMBOLISM / METAPHOR (if relevant):
- symbol set (allowed):
- symbol bans:
- metaphor rules:

SENSORY DETAIL (if relevant):
- dominant senses:
- texture palette:
- sensory bans:

STYLE CONSISTENCY RULES:
- MUST:
- MUST NOT:
- OPTIONAL:

---

## 5) STYLE GATES (HARD) — REQUIRED
GATE LIST:
- GATE: <name>
  CHECK: <how to verify>
  FAIL SIGNAL: <what indicates failure>
  FIX STRATEGY: <how to fix>

MINIMUM STYLE GATES (default set):
- tone consistency (no random tone shifts)
- atmosphere coherence (signals align)
- motif continuity (symbols don’t contradict)
- sensory palette stability (details feel from same world)
- narrative compatibility (style does not block story clarity)

---

## 6) EXAMPLES (REQUIRED)
GOOD EXAMPLE:
- <short structured example using contract fields>

BAD EXAMPLE:
- <counterexample>
- why fails: <gate>

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
