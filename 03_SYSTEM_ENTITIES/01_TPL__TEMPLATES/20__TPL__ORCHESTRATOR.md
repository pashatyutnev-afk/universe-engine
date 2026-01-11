# TPL ORCHESTRATOR — ENTITY TEMPLATE (CANON)
FILE: 03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/20__TPL__ORCHESTRATOR.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: TEMPLATES (TPL)
DOC_TYPE: TEMPLATE
TEMPLATE_TYPE: ENTITY_ORCHESTRATOR
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.ORC.001
OWNER: SYSTEM
ROLE: Canonical template to create any ORC Orchestrator file (pipeline contract + gates + registration checklist)

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Created ORC orchestrator template: pipeline spec, inputs/outputs, gates, dependency/xref, registration checklist."
- REASON: "Orchestrators must be deterministic and auditable."
- IMPACT: "Stable pipelines + no missing gate/spec."
- CHANGE_ID: UE.CHG.2026-01-11.TPL.ORC.001

---

## 0) PURPOSE
This template creates an ORC file that defines a deterministic pipeline:
- what stages exist
- what entities are invoked (ENG/SPC/CTL/VAL/QA)
- what gates block progression
- what artifacts are produced and where they go

---

## 1) TARGET
TARGET_CLASS: ORC  
TARGET_FOLDER: `03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/`  
REQUIRED_INDEX_OWNER (GLOBAL): `03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/02__INDEX_ALL_ORCHESTRATORS`  
REQUIRED_FAMILY_README: `03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/<FAMILY>/00__README__<FAMILY>.md` (if family uses a README)

---

## 2) STRUCTURE SKELETON (COPY BELOW INTO NEW ORC FILE)
> IMPORTANT: keep the section order exactly.
> ORC must be readable as a pipeline spec without opening any other files.

--- CUT HERE ---

# <ORC TITLE> — ORCHESTRATOR (ORC)
FILE: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/<FAMILY_PATH>/NN__<ORC_NAME>_ORC.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ORCHESTRATORS (ORC)
DOC_TYPE: ORCHESTRATOR
ORC_TYPE: <CORE|DOMAIN|PRODUCTION|MUSIC|META>
LEVEL: <L1|L2|L3>
STATUS: <DRAFT|ACTIVE|DEPRECATED|ARCHIVED>
LOCK: <OPEN|FIXED>
VERSION: <X.Y.Z>
UID: <UE.ORC.<FAMILY>.<NAME>.<NNN>>
OWNER: SYSTEM
ROLE: <One-line: what this orchestrator pipeline does>

CHANGE_NOTE:
- DATE: <YYYY-MM-DD>
- TYPE: <MAJOR|MINOR|PATCH>
- SUMMARY: "<what changed>"
- REASON: "<why>"
- IMPACT: "<impact>"
- CHANGE_ID: <UE.CHG.YYYY-MM-DD....>

---

## 0) PURPOSE (PIPELINE LAW)
- <When this ORC is invoked>
- <What outcome it guarantees>
- <What it must never do (boundaries)>

---

## 1) INPUTS / OUTPUTS (PIPELINE CONTRACT — MANDATORY)
CONSUMES:
- <1..5 input artifacts>

PRODUCES:
- <1..5 output artifacts>

DEPENDS_ON:
- [] OR
- - <RAW link(s) to prerequisite ORC/ENG/CTL>

OUTPUT_TARGET:
- <where produced artifacts are stored>

---

## 2) PIPELINE STAGES (DETERMINISTIC)
Define stages as a strict ordered list.

### Stage 01 — <NAME>
GOAL:
- <what this stage achieves>

INVOKES:
- ENGINES:
  - <RAW: ...> (optional)
- SPECIALISTS:
  - <RAW: ...> (optional)
- CONTROLLERS:
  - <RAW: ...> (optional)
- VALIDATORS:
  - <RAW: ...> (optional)
- QA:
  - <RAW: ...> (optional)

ARTIFACTS OUT:
- <what this stage outputs>

GATES (BLOCKING RULES):
- <which validator/qa/controller blocks progress>

FAIL / FIX:
- FAIL IF: <condition>
- FIX BY: <action>

### Stage 02 — <NAME>
(repeat)

---

## 3) CONTROL LAYER (POLICIES USED)
- CTL references (RAW-only):
  - <RAW: ...>
- Default policies (short):
  - <policy name>: <what it enforces>

---

## 4) VALIDATION MATRIX (WHAT IS CHECKED)
- VAL references (RAW-only):
  - <RAW: ...>
- What each VAL checks:
  - <VAL name> → <check>

---

## 5) QA CHECKS (HUMAN/FAST TESTS)
- QA references (RAW-only):
  - <RAW: ...>
- Minimum QA bar:
  - <test 1>
  - <test 2>

---

## 6) COLLISION / NOVELTY / MEMORY (IF APPLICABLE)
- Catalog memory used? <YES/NO>
- Collision thresholds / rules: <short>
- Novelty injection strategy: <short>

---

## 7) INTEGRATION & XREF (MANDATORY WHEN APPLICABLE)
- Needs XREF map updates? <YES/NO>
- Needs dependency registry record? <YES/NO>
- External interfaces (RAW-only):
  - <RAW: ...>

---

## 8) OUTPUT PACK SPEC (IF THIS ORC PRODUCES A PACK)
Define:
- pack contents list
- naming convention
- release variants (if any)

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: <OPEN|FIXED>

--- END.

--- CUT HERE ---

---

## 3) INDEX + REGISTRATION CHECKLIST (MANDATORY)
When a new ORC is created:
1) Add RAW link to `20_ORC__ORCHESTRATORS/02__INDEX_ALL_ORCHESTRATORS`
2) Ensure correct FAMILY folder + correct numbering `NN__`
3) Ensure gates are explicit (VAL/QA/CTL listed)
4) If it introduces dependencies:
   - register them in the relevant dependency registry / xref map (if required)
5) Ensure OUTPUT_TARGET is defined (no “somewhere”)

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
