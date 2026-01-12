# TEMPLATE — ENGINE (TREND / GENRE ENGINES)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/00__TEMPLATE__ENGINE__TREND_GENRE_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: TEMPLATE
TEMPLATE_TYPE: ENGINE_TEMPLATE
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.ENG.TREND_GENRE.001
OWNER: SYSTEM
ROLE: Canonical engine template for 12_TREND_GENRE_ENGINES (taxonomy/fusion/fingerprint/hooks/ugc/prompt compiler).

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created missing Trend/Genre engine template."
- REASON: "All TG engines must be comparable and runnable; prevents drift and broken contracts."
- IMPACT: "Faster stamping, consistent docs, deterministic outputs."
- CHANGE_ID: UE.CHG.2026-01-12.TPL.ENG.TREND_GENRE.001

---

## 0) HOW TO USE THIS TEMPLATE
1) Copy “ENGINE FILE SKELETON” into a new engine file inside this family.
2) Keep section order unchanged.
3) Make procedure deterministic (numbered steps).
4) Outputs must be structured and reusable by Music Factory.

---

## 1) ENGINE FILE SKELETON (COPY)

--- CUT HERE ---

#  — ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/NN__<NAME>_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
ENGINE_FAMILY: 12_TREND_GENRE_ENGINES
DOC_TYPE: ENGINE
ENGINE_TYPE: TREND_GENRE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.TG.<NAME>.001
OWNER: SYSTEM
ROLE:

CHANGE_NOTE:
- DATE:
- TYPE:
- SUMMARY: ""
- REASON: ""
- IMPACT: ""
- CHANGE_ID:

---

## 0) PURPOSE (LAW)
- What exactly this engine decides/outputs.
- Where it sits in the TG pipeline (before/after).
- Why it matters for prompt fidelity / viral / identity.

---

## 1) INPUTS (CONSUMES)
- List concrete artifacts this engine requires (1–6).
- Avoid “vague” inputs.

---

## 2) OUTPUTS (PRODUCES)
- List concrete outputs (1–6).
- At least one output must be structured (schema/table/spec).

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [ ]
PRODUCES: [ ]
DEPENDS_ON: [ ]
OUTPUT_TARGET: ""

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
### In scope
-

### Out of scope
- (name the family that owns it)

---

## 5) CORE MODEL (DEFINITIONS)
- Vocabulary / taxonomy / schema / rule system.
- Define the “tokens” that later engines will reuse.

---

## 6) PROCEDURE (DETERMINISTIC)
1)
2)
3)
4)

---

## 7) OUTPUT SCHEMA (MANDATORY IF APPLICABLE)
Provide a simple structured format:
- fields
- allowed values
- examples (optional, short)

---

## 8) FAILURE MODES & FIXES
1) Symptom:
- Likely cause:
- Fix:
- Escalate to:

---

## 9) HANDOFFS (XREF)
Used by:
- Music Factory engines (Group/Album/Track)
- Controllers/Validators/QAs (if any)

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: OPEN

--- END.

--- CUT HERE ---

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
