# ENGINE TEMPLATE — DOMAIN CHARACTER ENGINES (ENG)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/00__TEMPLATE__ENGINE__DOMAIN_CHARACTER_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
ENTITY_CLASS: ENG
ENGINE_FAMILY: 03_DOMAIN_CHARACTER_ENGINES
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.ENG.DOMAIN.CHARACTER.ENGINE.001
OWNER: SYSTEM
ROLE: Canonical template for character-domain ENG engines (identity, motivation, psychology, behavior, dialogue, relationships, growth)

---

## 0) IDENTITY (REQUIRED)
ENGINE_NAME: <DISPLAY_NAME>
ENGINE_CODE: <SHORT_CODE>                         # e.g., CHARACTER_CORE, MOTIVATION_DESIRE
ENGINE_NUMBER: <NN>                               # must match filename NN__
ENGINE_FILE_NAME: <NN__NAME_ENG.md>
ENGINE_UID: <UE.ENG.DOM.CHR.<CODE>.NNN>

CHARACTER_OBJECT:
- What character object it owns (1 line): (identity / motivation / values / psyche / behavior / relationship / dialogue / growth)
- What it guarantees (1 line)

---

## 1) PURPOSE (LAW)
Зачем этот движок существует:
- какую “дыру” в персонаже он закрывает
- какие типовые ошибки персонажей предотвращает (картон / нелогичность / непоследовательность)
- что он делает каноном и фиксирует

---

## 2) DOMAIN BOUNDARY (ANTI-DUP) — REQUIRED
OWNED HERE:
- <what this engine owns>

NOT OWNED HERE:
- plot/scene structure (02_DOMAIN_NARRATIVE_ENGINES)
- world laws/economy/epochs (04_DOMAIN_WORLD_ENGINES)
- media production timing/editing (08_KNOWLEDGE_PRODUCTION_ENGINES)

INTERFACES:
- Upstream expectations: <what must exist before>
- Downstream outputs: <what can rely on this>

---

## 3) INPUTS / OUTPUTS (MINI-CONTRACT) — REQUIRED
CONSUMES:
- <ARTIFACT_TYPE or UID>
- ...

PRODUCES:
- <ARTIFACT_TYPE or UID>
- ...

CHARACTER_OUTPUT (REQUIRED):
- OUTPUT_OBJECT: <e.g., Character Sheet | Motivation Map | Values Matrix | Dialogue Rules | Relationship Graph>
- OUTPUT_SCHEMA (short): <fields/structure bullets>
- OUTPUT_INVARIANTS: <what must always be true about character>

DEPENDS_ON:
- <ENG_UID>
- ...

OUTPUT_TARGET:
- <where in projects the output should live> (descriptive, no path-nav)

---

## 4) CHARACTER CONTRACT (HARD) — REQUIRED
IDENTITY CORE:
- Name/Role: <...>
- Core wound / core need (if applicable): <...>
- Primary desire: <...>
- Primary fear: <...>

VALUES & MORALS:
- Non-negotiables: <...>
- Taboo lines: <...>
- Trade-offs: <...>

PSYCHO-LOGIC:
- Trigger → Emotion → Thought → Action chain (pattern):
  - Trigger:
  - Emotion:
  - Thought:
  - Action:

BEHAVIORAL INVARIANTS:
- Always:
- Never:
- Under pressure:

RELATIONSHIP RULES (if relevant):
- Attachment pattern:
- Conflict pattern:
- Trust / betrayal rules:

DIALOGUE RULES (if relevant):
- Voice: <tone/lexicon>
- Rhythm: <short/long, interruptions, pauses>
- Forbidden phrases / tells:

GROWTH TRACK (if relevant):
- Before → After:
- Growth driver:
- Relapse risk:

---

## 5) CORE MECHANISM (HOW IT WORKS)
MECHANISM:
- Step 1:
- Step 2:
- Step 3:

TOOLS / MODELS (OPTIONAL):
- Model:
  WHY:

---

## 6) QUALITY GATES (HARD) — REQUIRED
GATE LIST:
- GATE: <name>
  CHECK: <how to verify>
  FAIL SIGNAL: <what indicates failure>
  FIX STRATEGY: <how to fix>

MINIMUM CHARACTER GATES (default set):
- consistency (actions match motives/values)
- believability (human/agent-like causal psychology)
- continuity (no contradictions across scenes)
- voice stability (dialogue style holds)
- growth logic (change has cause and cost)

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
