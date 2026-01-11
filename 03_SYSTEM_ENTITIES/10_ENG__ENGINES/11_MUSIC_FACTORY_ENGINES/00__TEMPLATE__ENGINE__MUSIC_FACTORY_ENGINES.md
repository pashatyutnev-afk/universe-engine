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
VERSION: 1.0.0
UID: UE.TPL.ENG.MUSIC_FACTORY.001
OWNER: SYSTEM
ROLE: Canonical engine template for 11_MUSIC_FACTORY_ENGINES (factory pipeline engines)

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Created Music Factory engine template: contract-first + operational steps + outputs."
- REASON: "Factory engines must be runnable and comparable; contract is mandatory."
- IMPACT: "All Music Factory engines become consistent and auditable."
- CHANGE_ID: UE.CHG.2026-01-11.TPL.ENG.MUSIC_FACTORY.001

---

## 0) HOW TO USE THIS TEMPLATE
1) Copy this file content into a new engine file: `NN__<ENGINE_NAME>_ENG.md`
2) Fill mandatory fields and sections.
3) Keep section order unchanged.
4) Do not add extra laws here; reference existing ones.

---

## 1) ENGINE FILE SKELETON (COPY)
--- CUT HERE ---

# <ENGINE NAME> — ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/<NN__ENGINE_NAME_ENG.md>

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
UID: UE.ENG.MF.<SHORT>.<NNN>
OWNER: SYSTEM
ROLE: <one-line: what this engine does in factory pipeline>

CHANGE_NOTE:
- DATE: <YYYY-MM-DD>
- TYPE: <MAJOR|MINOR|PATCH>
- SUMMARY: "<what changed>"
- REASON: "<why>"
- IMPACT: "<impact>"
- CHANGE_ID: <UE.CHG.YYYY-MM-DD.ENG.MF....>

---

## 0) PURPOSE
- What problem this engine solves.
- Where it sits in the pipeline (before/after).
- What quality target it enforces (viral/novelty/no-repeat/etc).

---

## 1) INPUTS (CONSUMES)
List concrete artifact types this engine accepts (1–5):
- <e.g., Group DNA Spec>
- <e.g., Album Blueprint Spec>
- <e.g., Track Brief>
- <e.g., Catalog Memory Snapshot>
- <e.g., Platform Constraints>

---

## 2) OUTPUTS (PRODUCES)
List concrete artifacts produced (1–5):
- <e.g., Group Foundation Pack>
- <e.g., Artist Roster>
- <e.g., Track Variant Set>
- <e.g., Release Pack>
- <e.g., Collision Report>
- <e.g., Take Log Entry>

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [<1..5 items>]
PRODUCES: [<1..5 items>]
DEPENDS_ON: [<engine raw-links or []>]
OUTPUT_TARGET: <where outputs are stored in projects/databases>

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
### In scope
- <what belongs here>

### Out of scope
- <what must be handled by other families (reference them)>

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
- <rule: e.g., “no chorus after 45s for short format”>
- <rule: e.g., “at least 2 distinct hooks per variant set”>
- <rule: e.g., “album must contain track roles distribution”>

---

## 7) FAILURE MODES & FIXES
For each failure mode:
- Symptom:
- Likely cause:
- Fix procedure:
- Escalate to: <which controller/validator/QA>

---

## 8) HANDOFFS (XREF)
Which entities use this output next:
- NEXT ORC:
- NEXT ENG:
- REQUIRED CTL:
- REQUIRED VAL:
- REQUIRED QA:

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
