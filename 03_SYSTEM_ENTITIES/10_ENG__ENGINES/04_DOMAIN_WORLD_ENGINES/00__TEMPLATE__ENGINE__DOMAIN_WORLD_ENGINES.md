# ENGINE TEMPLATE — DOMAIN WORLD ENGINES (ENG)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/00__TEMPLATE__ENGINE__DOMAIN_WORLD_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
ENTITY_CLASS: ENG
ENGINE_FAMILY: 04_DOMAIN_WORLD_ENGINES
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.ENG.DOMAIN.WORLD.ENGINE.001
OWNER: SYSTEM
ROLE: Canonical template for world-domain ENG engines (world structure/laws/epochs/civilizations/economy/tech/ecology)

---

## 0) IDENTITY (REQUIRED)
ENGINE_NAME: <DISPLAY_NAME>
ENGINE_CODE: <SHORT_CODE>                          # e.g., WORLD_STRUCTURE, ECONOMY_RESOURCE
ENGINE_NUMBER: <NN>                                # must match filename NN__
ENGINE_FILE_NAME: <NN__NAME_ENG.md>
ENGINE_UID: <UE.ENG.DOM.WORLD.<CODE>.NNN>

WORLD_OBJECT:
- What world object it owns (1 line): (laws/epochs/civilization/economy/tech/ecology)
- What it guarantees (1 line)

---

## 1) PURPOSE (LAW)
Зачем этот движок существует:
- какую часть мира делает определённой/канонической
- какие противоречия предотвращает
- что даёт сценариям/персонажам как “твёрдую почву”

---

## 2) DOMAIN BOUNDARY (ANTI-DUP) — REQUIRED
OWNED HERE:
- <what this engine owns>

NOT OWNED HERE:
- plot/scene structure (02_DOMAIN_NARRATIVE_ENGINES)
- character psychology/motivation/voice (03_DOMAIN_CHARACTER_ENGINES)
- expression primitives (05_EXPRESSION_ENGINES)
- production/media pipeline (08_KNOWLEDGE_PRODUCTION_ENGINES)

INTERFACES:
- Narrative interface: <what narrative can assume as constraints>
- Character interface: <how characters are affected by this world logic>
- Project interface: <what project artifacts should contain>

---

## 3) INPUTS / OUTPUTS (MINI-CONTRACT) — REQUIRED
CONSUMES:
- <ARTIFACT_TYPE or UID>
- ...

PRODUCES:
- <ARTIFACT_TYPE or UID>
- ...

WORLD_OUTPUT (REQUIRED):
- OUTPUT_OBJECT: <e.g., World Ruleset | Epoch Timeline | Economy Model | Tech Tree | Civilization Map>
- OUTPUT_SCHEMA (short): <fields/structure bullets>
- OUTPUT_INVARIANTS: <what must always be true about world>

DEPENDS_ON:
- <ENG_UID>
- ...

OUTPUT_TARGET:
- <where in projects the output should live> (descriptive, no path-nav)

---

## 4) WORLD MODEL CONTRACT (HARD) — REQUIRED
WORLD STRUCTURE (if relevant):
- Regions / scales:
- Key locations:
- Travel / distance rules:

WORLD LAWS (if relevant):
- Physics/baseline rules:
- Magic/tech rules (if any):
- Constraints (hard bans):

TIME & EPOCHS (if relevant):
- Epoch list:
- Key transitions:
- Calendar/timekeeping:

CIVILIZATION & SOCIETY (if relevant):
- Social structure:
- Institutions:
- Culture norms:

ECONOMY & RESOURCES (if relevant):
- Resource sources:
- Production/flow:
- Scarcity rules:
- (NOTE: в вашей вселенной цивилизации могут быть без валюты — фиксируй как инвариант, если применимо)

POWER & CONFLICT (if relevant):
- Power centers:
- Conflict drivers:
- Balance rules:

TECHNOLOGY / MAGIC (if relevant):
- Capability tiers:
- Limitations/costs:
- Side effects:

ECOLOGY & ENVIRONMENT (if relevant):
- Biomes/climate:
- Survival constraints:
- Long-term stability:

---

## 5) PLAUSIBILITY & CONSISTENCY GATES (HARD) — REQUIRED
GATE LIST:
- GATE: <name>
  CHECK: <how to verify>
  FAIL SIGNAL: <what indicates failure>
  FIX STRATEGY: <how to fix>

MINIMUM WORLD GATES (default set):
- internal consistency (rules don’t contradict)
- causality (institutions/economy follow constraints)
- scalability (local rules hold at global scale)
- narrative usability (rules are usable in scenes)
- timeline coherence (epochs/events order makes sense)

---

## 6) FAILURE MODES & EDGE CASES
FAILURES:
- Failure:
  CAUSE:
  RECOVERY:

EDGE CASES:
- Case:
  Handling:

---

## 7) REL / XREF (UID-FIRST)
REL:
- REL: <REL_TYPE> | TARGET: <UID> | WHY: <reason>

XREF:
- XREF: <UID> | WHY: <reason>

RULE:
- No PATH navigation inside content.
- If clickable references are needed, keep them in registries/indexes as RAW.

---

## 8) CHANGE NOTES (OPTIONAL)
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR
- SUMMARY:
- REASON:
- IMPACT:

--- END.
