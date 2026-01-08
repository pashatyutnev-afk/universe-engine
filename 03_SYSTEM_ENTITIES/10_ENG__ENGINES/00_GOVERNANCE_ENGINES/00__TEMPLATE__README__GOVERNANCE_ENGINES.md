# README TEMPLATE — GOVERNANCE ENGINES (ENG FAMILY)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/00__TEMPLATE__README__GOVERNANCE_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
ENTITY_CLASS: ENG
ENGINE_FAMILY: 00_GOVERNANCE_ENGINES
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.ENG.GOV.FAMILY_README.001
OWNER: SYSTEM
ROLE: Canonical template for 00_GOVERNANCE_ENGINES family README (scope, rules, engine list policy)

---

## 0) FAMILY IDENTITY (REQUIRED)
FAMILY_NAME: 00_GOVERNANCE_ENGINES
FAMILY_CLASS: GOVERNANCE
FAMILY_UID: UE.ENG.FAMILY.GOV.001

---

## 1) PURPOSE (LAW)
Семейство governance-движков:
- защищает канон, порядок и совместимость
- фиксирует изменения, решения, риски
- управляет зависимостями и конфликтами

---

## 2) GOVERNANCE OWNERSHIP (BOUNDARIES)
OWNED HERE:
- audit trail / change logs
- canon authority decisions
- rule hierarchy & precedence
- consistency checks
- dependency registry
- approvals / escalation
- scope impact & risk safety
- versioning memory

NOT OWNED HERE:
- domain logic (narrative/character/world)
- production media creation
- project-specific content decisions

---

## 3) FAMILY RULES (MANDATORY)
- Every engine file MUST include MINI-CONTRACT:
  CONSUMES / PRODUCES / DEPENDS_ON / OUTPUT_TARGET
- Every engine MUST declare:
  ENFORCEMENT_MODE (HARD_BLOCK | SOFT_WARN | RECORD_ONLY)
- Any canon-impacting change MUST:
  produce an audit record and/or decision record.

---

## 4) REQUIRED TEMPLATES
ENGINE TEMPLATE UID: UE.TPL.ENG.GOV.ENGINE.001
FAMILY README TEMPLATE UID: UE.TPL.ENG.GOV.FAMILY_README.001

---

## 5) ENGINE LIST POLICY (NUMBERING)
- Folder format: `00_GOVERNANCE_ENGINES`
- Engine files: `NN__<NAME>_ENG.md` (NN starts at 01)
- NN in filename MUST match NN in registry / index.
- README is always `00__README__GOVERNANCE_ENGINES.md`
- Templates are always `00__TEMPLATE__...`

---

## 6) REL / XREF (UID-FIRST)
REL:
- REL: <REL_TYPE> | TARGET: <UID> | WHY: <reason>

XREF:
- XREF: <UID> | WHY: <reason>

--- END.
