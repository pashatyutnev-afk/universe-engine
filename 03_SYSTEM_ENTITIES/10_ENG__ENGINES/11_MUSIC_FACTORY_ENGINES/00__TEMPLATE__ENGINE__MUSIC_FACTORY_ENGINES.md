# TEMPLATE — ENGINE (MUSIC FACTORY ENGINES)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/00__TEMPLATE__ENGINE__MUSIC_FACTORY_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: TEMPLATE
TEMPLATE_TYPE: ENGINE_TEMPLATE
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.TPL.ENG.MUSIC_FACTORY.001
OWNER: SYSTEM
ROLE: Canonical engine template for 11_MUSIC_FACTORY_ENGINES (factory pipeline engines).

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MINOR
- SUMMARY: "Reformatted template to multi-line + added handoff hints for memory/collision/qa wiring."
- REASON: "Operational copy/paste must be safe; hints reduce missing dependencies."
- IMPACT: "Faster stamping, fewer broken engines."
- CHANGE_ID: UE.CHG.2026-01-12.TPL.ENG.MUSIC_FACTORY.002

---

## 0) HOW TO USE THIS TEMPLATE
1) Copy this file content into a new engine file: `NN__<NAME>_ENG.md`
2) Fill mandatory fields and sections.
3) Keep section order unchanged.
4) Do not add new laws here; reference existing ones.

---

## 1) ENGINE FILE SKELETON (COPY)

--- CUT HERE ---

#  — ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/NN__<NAME>_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
ENGINE_FAMILY: 11_MUSIC_FACTORY_ENGINES
DOC_TYPE: ENGINE
ENGINE_TYPE: MUSIC_FACTORY
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.MF.<NAME>.001
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

## 0) PURPOSE
- What problem this engine solves.
- Where it sits in the pipeline (before/after).
- What quality target it enforces (viral / novelty / no-repeat / packaging / etc).

---

## 1) INPUTS (CONSUMES)
List concrete artifact types this engine accepts (1–5):
- 
- 
- 
- 
- 

---

## 2) OUTPUTS (PRODUCES)
List concrete artifacts produced (1–5):
- 
- 
- 
- 
- 

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [<1..5 items>]
PRODUCES: [<1..5 items>]
DEPENDS_ON: []
OUTPUT_TARGET: ""

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
### In scope
- 

### Out of scope
- 

---

## 5) WORKFLOW (OPERATIONAL STEPS)
Provide a deterministic step list:
1) Step name — what is decided/constructed
2) Step name — what is checked/locked
3) Step name — what is generated
4) Step name — what is validated
5) Step name — what is logged

---

## 6) DECISION RULES (FACTORY LOGIC)
Hard rules that must be applied:
- 
- 
- 

---

## 7) FAILURE MODES & FIXES
For each failure mode:
- Symptom:
- Likely cause:
- Fix procedure:
- Escalate to:

---

## 8) HANDOFFS (XREF)
Which entities use this output next:
- NEXT ORC:
- NEXT ENG:

Required enforcement (hint: most MF engines wire at least memory + collision + QA):
- REQUIRED CTL: (e.g., catalog memory / duration policy / prompt contract)
- REQUIRED VAL: (e.g., repeat guard / collision blocker / hook timing)
- REQUIRED QA:  (e.g., loop 15s / recognition 10s / regression guard)

---

## 9) OUTPUT PACK (MANDATORY LIST)
This engine must emit:
- 1) Primary artifact:
- 2) Secondary artifact:
- 3) Log record:
- 4) Validation report (if any):

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
