# ENGINE TEMPLATE — CORE ENGINES (ENG)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/00__TEMPLATE__ENGINE__CORE_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
ENTITY_CLASS: ENG
ENGINE_FAMILY: 01_CORE_ENGINES
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.ENG.CORE.ENGINE.001
OWNER: SYSTEM
ROLE: Canonical template for core-class ENG engines (identity/state/lifecycle)

---

## 0) IDENTITY (REQUIRED)
ENGINE_NAME: <DISPLAY_NAME>
ENGINE_CODE: <SHORT_CODE>                  # e.g., CORE_IDENTITY, CORE_STATE, CORE_LIFECYCLE
ENGINE_NUMBER: <NN>                        # must match filename NN__
ENGINE_FILE_NAME: <NN__NAME_ENG.md>
ENGINE_UID: <UE.ENG.CORE.<CODE>.NNN>

CORE_OBJECT:
- What “thing” this engine defines or updates (1 line)
- What “truth” it owns (1 line)

---

## 1) PURPOSE (LAW)
Этот core-движок задаёт базовую истину системы:
- какая истина фиксируется (identity/state/lifecycle)
- почему без неё система распадается
- какие downstream-слои на это опираются

---

## 2) DEFINITIONS (CANON TERMS)
KEY TERMS:
- TERM: <name> — <definition>
- TERM: <name> — <definition>

INVARIANTS (ABSOLUTE):
- Invariant:
- Invariant:

---

## 3) INPUTS / OUTPUTS (MINI-CONTRACT) — REQUIRED
CONSUMES:
- <ARTIFACT_TYPE or UID>
- ...

PRODUCES:
- <ARTIFACT_TYPE or UID>
- ...

STATE_EFFECT (REQUIRED):
- SETS: <what it sets>
- UPDATES: <what it updates>
- GUARANTEES: <what must be true after run>

DEPENDS_ON:
- <ENG_UID>
- ...

OUTPUT_TARGET:
- <where the produced artifact/state must live> (descriptive, no path-nav)

---

## 4) CORE MODEL (STRUCTURE)
MODEL:
- ENTITY/STATE FIELDS:
  - FIELD: <name> | TYPE: <type> | REQUIRED: <yes/no> | MEANING: <short>
  - ...

DEFAULTS:
- FIELD: <name> = <default> | WHY:

VALID STATES (if applicable):
- STATE: <name> | ENTRY: <conditions> | EXIT: <conditions>

---

## 5) RULES (HARD)
HARD RULES:
- Rule:
  WHY:
  HOW TO CHECK:

SOFT RULES (OPTIONAL):
- Rule:
  WHY:
  RECOMMENDED:

---

## 6) FAILURE MODES & RECOVERY
FAILURES:
- Failure: <what breaks>
  SIGNAL:
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
- If a clickable reference is needed, use RAW in indexes/registries, not here.

---

## 8) CHANGE NOTES (OPTIONAL)
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR
- SUMMARY:
- REASON:
- IMPACT:

--- END.
