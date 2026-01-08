# GOVERNANCE ENGINE — TEMPLATE (CANON)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/00__TEMPLATE__ENGINE__GOVERNANCE_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: TEMPLATE
FAMILY: 00_GOVERNANCE_ENGINES
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.1
UID: UE.TPL.ENG.GOV.ENGINE.001
OWNER: SYSTEM
ROLE: Canonical engine template for governance engines (mandatory skeleton + mini-contract + hard gates)
CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: HOTFIX
- SUMMARY: "Template normalized: full header + raw-only references policy + removed footer duplicates."
- REASON: "Align with marking standards and raw-only navigation rule."
- IMPACT: "All governance engines become structurally uniform and verifiable."
- CHANGE_ID: UE.CHG.2026-01-08.002

---

## 0) IDENTITY (REQUIRED)
ENGINE_NAME: <DISPLAY_NAME>
ENGINE_CODE: <SHORT_CODE>
ENGINE_NUMBER: <NN>                           # must match filename NN__
ENGINE_FILE_NAME: <NN__NAME_ENG.md>
ENGINE_UID: <UE.ENG.GOV.<CODE>.NNN>

---

## 1) PURPOSE (LAW)
- What this engine enforces (1–5 bullets)
- Primary outcome (1 line)
- Non-goals (hard)

---

## 2) BOUNDARY (ANTI-DUPLICATION)
OWNED HERE:
- <owned scope>

NOT OWNED HERE:
- <explicit exclusions>

INTERFACES:
- Inputs read:
- Outputs write:
- Enforcement notes:

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES:
- <1–5 artifact types>

PRODUCES:
- <1–5 artifact types>

DEPENDS_ON:
- []  # or list of engine references (family/file)
OUTPUT_TARGET:
- <storage target>

---

## 4) OPERATION MODEL
TRIGGER:
- when to run

STEPS:
1) collect
2) validate
3) decide/enforce
4) produce
5) link (xref)
6) finalize

OUTPUT SEMANTICS:
- PASS behavior
- FAIL behavior
- NEEDS_APPROVAL behavior (if applicable)

---

## 5) HARD GATES (MANDATORY)
- G1:
- G2:
- G3:
- G4:
- G5:

---

## 6) OUTPUT ARTIFACT FORMS
- define standard formats the engine produces

---

## 7) EXAMPLES (GOOD / BAD)
GOOD:
- <scenario + expected outputs>

BAD:
- <scenario + why blocked + outputs>

---

## 8) FAILURE MODES & EDGE CASES
- failure → cause → recovery
- edge case → handling

---

## 9) REL / XREF (RAW ONLY)
REL:
- REL: <TYPE> | TARGET_UID: <UID> | RAW: <raw link> | WHY: <reason>

XREF:
- XREF_UID: <UID> | RAW: <raw link> | WHY: <reason>

RULE:
- No non-raw links.

--- END.
