# ENGINE TEMPLATE — DOMAIN NARRATIVE ENGINES (ENG)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/00__TEMPLATE__ENGINE__DOMAIN_NARRATIVE_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
ENTITY_CLASS: ENG
ENGINE_FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.ENG.DOMAIN.NARRATIVE.ENGINE.001
OWNER: SYSTEM
ROLE: Canonical template for narrative-domain ENG engines (story logic, structure, scenes, meaning)

---

## 0) IDENTITY (REQUIRED)
ENGINE_NAME: <DISPLAY_NAME>
ENGINE_CODE: <SHORT_CODE>                      # e.g., NARRATIVE_LOGIC, STORY_STRUCTURE
ENGINE_NUMBER: <NN>                            # must match filename NN__
ENGINE_FILE_NAME: <NN__NAME_ENG.md>
ENGINE_UID: <UE.ENG.DOM.NARR.<CODE>.NNN>

DOMAIN_OBJECT:
- What narrative object it owns (1 line): (plot / arc / scene / tension / theme / continuity)
- What it guarantees (1 line)

---

## 1) PURPOSE (LAW)
Зачем этот движок существует:
- какую “дырку” в повествовании он закрывает
- какой тип ошибок предотвращает
- какую структуру делает обязательной

---

## 2) DOMAIN BOUNDARY (ANTI-DUP) — REQUIRED
OWNED HERE:
- <what this engine owns>

NOT OWNED HERE:
- <what is owned by other engines/families> (name the target family/type, no path-nav)

INTERFACES:
- Upstream expectations: <what inputs must already exist>
- Downstream outputs: <what other engines can rely on>

---

## 3) INPUTS / OUTPUTS (MINI-CONTRACT) — REQUIRED
CONSUMES:
- <ARTIFACT_TYPE or UID>
- ...

PRODUCES:
- <ARTIFACT_TYPE or UID>
- ...

NARRATIVE_OUTPUT (REQUIRED):
- OUTPUT_OBJECT: <e.g., Story Outline | Beat Sheet | Scene List | Arc Map | Theme Statement>
- OUTPUT_SCHEMA (short): <bullets describing fields/structure>
- OUTPUT_INVARIANTS: <what must always be true>

DEPENDS_ON:
- <ENG_UID>
- ...

OUTPUT_TARGET:
- <where in projects the output should live> (descriptive, no path-nav)

---

## 4) CORE MECHANISM (HOW IT WORKS)
MECHANISM:
- Step 1:
- Step 2:
- Step 3:

HEURISTICS (OPTIONAL):
- Heuristic:
  WHY:

---

## 5) QUALITY GATES (HARD) — REQUIRED
GATE LIST:
- GATE: <name>
  CHECK: <how to verify>
  FAIL SIGNAL: <what indicates failure>
  FIX STRATEGY: <how to fix>

MINIMUM NARRATIVE GATES (default set):
- coherence (cause-effect)
- escalation (tension/stakes do not stagnate)
- clarity (reader can follow)
- payoff (setups have resolution or declared intentional)
- continuity (no contradictions with canon)

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
