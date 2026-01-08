# README TEMPLATE — ENG FAMILY UNIVERSAL (BASE)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00__TEMPLATE__README__ENG_FAMILY_UNIVERSAL.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
LEVEL: <L1|L2|L3|L4>
STATUS: ACTIVE
VERSION: 1.0.0
ROLE: Universal base template for any ENG family README

LOCK: FIXED
UID: <UE.TPL.ENG.UNIVERSAL.FAMILY_README.###>  # MUST follow UID_RULES

---

## 0) FAMILY IDENTITY (REQUIRED)
FAMILY_NAME: <NN_FAMILY_ENGINES>
CLASS: <GOVERNANCE|CORE|DOMAIN|EXPRESSION|STYLE|PRODUCTION|SOUND|META>
LEVEL_TAG: <L1|L2|L3|L4>
FAMILY_UID: <UE.ENG.FAMILY.<FAMILY>.###>

---

## 1) PURPOSE (LAW)
- What problems this family solves
- Typical use-cases
- Typical outputs (high level)

---

## 2) CRITICAL BOUNDARY (ANTI-DUP) — ABSOLUTE
OWNED HERE:
- ...

NOT OWNED HERE:
- ...

---

## 3) FAMILY GATES (MANDATORY)
- <family-specific gates, if any>
- Otherwise: obey universal gates from engine template

---

## 4) TEMPLATE POLICY
- Family must have:
  - ENGINE TEMPLATE file (this family)
  - README TEMPLATE file (this family)

---

## 5) ROSTER POLICY (IMPORTANT)
- Canonical roster & order live ONLY in 02__INDEX_ALL_ENGINES.md
- README roster (if present) is NON-CANON mirror

---

## 6) NUMBERING POLICY
- README: 00__README__<FAMILY>.md
- Engines: NN__<ENGINE_NAME>_ENG.md (NN starts at 01)
- Templates: 00__TEMPLATE__...

---

## 7) REL / XREF (UID-FIRST)
REL:
- REL: <REL_TYPE> | TARGET_UID: <UID> | WHY: <reason>

XREF:
- XREF_UID: <UID> | WHY: <reason>

--- END.
