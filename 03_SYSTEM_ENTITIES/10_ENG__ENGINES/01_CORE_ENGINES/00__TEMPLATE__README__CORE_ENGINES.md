# README TEMPLATE — CORE ENGINES (ENG FAMILY)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/00__TEMPLATE__README__CORE_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
ENTITY_CLASS: ENG
ENGINE_FAMILY: 01_CORE_ENGINES
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.ENG.CORE.FAMILY_README.001
OWNER: SYSTEM
ROLE: Canonical template for 01_CORE_ENGINES family README (scope, invariants, engine list policy)

---

## 0) FAMILY IDENTITY (REQUIRED)
FAMILY_NAME: 01_CORE_ENGINES
FAMILY_CLASS: CORE
FAMILY_UID: UE.ENG.FAMILY.CORE.001

---

## 1) PURPOSE (LAW)
Семейство core-движков определяет базовые “опоры” системы:
- кто мы (identity)
- где мы и что сейчас (state)
- как мы живём и меняемся (lifecycle)

---

## 2) CORE OWNERSHIP (BOUNDARIES)
OWNED HERE:
- system identity model
- system state model
- lifecycle / stage progression model
- invariants that all layers must respect

NOT OWNED HERE:
- governance decisions / approvals / audit logs
- domain logic (narrative/character/world)
- media production logic

---

## 3) FAMILY INVARIANTS (ABSOLUTE)
- Invariant:
- Invariant:
- Invariant:

---

## 4) REQUIRED TEMPLATES
ENGINE TEMPLATE UID: UE.TPL.ENG.CORE.ENGINE.001
FAMILY README TEMPLATE UID: UE.TPL.ENG.CORE.FAMILY_README.001

---

## 5) ENGINE LIST POLICY (NUMBERING)
- Folder format: `01_CORE_ENGINES`
- Engine files: `NN__<NAME>_ENG.md` (NN starts at 01)
- NN in filename MUST match NN in registry / index.
- README is always `00__README__CORE_ENGINES.md`
- Templates are always `00__TEMPLATE__...`

---

## 6) REL / XREF (UID-FIRST)
REL:
- REL: <REL_TYPE> | TARGET: <UID> | WHY: <reason>

XREF:
- XREF: <UID> | WHY: <reason>

--- END.
