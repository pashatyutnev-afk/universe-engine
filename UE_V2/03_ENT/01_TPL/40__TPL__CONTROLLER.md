# TPL CONTROLLER — ENTITY TEMPLATE (CANON)
FILE: 03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/40__TPL__CONTROLLER.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: TEMPLATES (TPL)
DOC_TYPE: TEMPLATE
TEMPLATE_TYPE: ENTITY_CONTROLLER
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.CTL.001
OWNER: SYSTEM
ROLE: Canonical template to create any CTL Controller file (policy contract + enforcement rules + integration checklist)

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Created CTL controller template: policy definition, enforcement checks, fail/fix, and pipeline integration."
- REASON: "Controllers must be explicit policies used by ORC pipelines."
- IMPACT: "CTL files become deterministic and enforceable."
- CHANGE_ID: UE.CHG.2026-01-11.TPL.CTL.001

---

## 0) PURPOSE
This template creates a CTL Controller policy file:
`03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/<FAMILY>/NN__<POLICY_NAME>_CTL`

Controllers:
- define policies and constraints used by ORC pipelines
- are not creative engines; they are rule/policy layers
- must be readable and enforceable

---

## 1) TARGET
TARGET_CLASS: CTL  
TARGET_FOLDER: `03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/`  
REQUIRED_INDEX_OWNER (GLOBAL): `03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/02__INDEX_ALL_CONTROLLERS`  
REQUIRED_FAMILY_README: `03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/<FAMILY>/00__README__...` (if family uses a README)

---

## 2) STRUCTURE SKELETON (COPY BELOW INTO NEW CTL FILE)
> IMPORTANT: keep the section order exactly.
> CTL must be explicit and testable.

--- CUT HERE ---

# <CONTROLLER TITLE> — CONTROLLER (CTL)
FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/<FAMILY_PATH>/NN__<CONTROLLER_NAME>_CTL.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: CONTROLLERS (CTL)
DOC_TYPE: CONTROLLER
CONTROLLER_TYPE: <MUSIC|NARRATIVE|VISUAL|PIPELINE|GOVERNANCE|OTHER>
LEVEL: <L1|L2|L3>
STATUS: <DRAFT|ACTIVE|DEPRECATED|ARCHIVED>
LOCK: <OPEN|FIXED>
VERSION: <X.Y.Z>
UID: <UE.CTL.<FAMILY>.<NAME>.<NNN>>
OWNER: SYSTEM
ROLE: <One-line: what policy this controller enforces>

CHANGE_NOTE:
- DATE: <YYYY-MM-DD>
- TYPE: <MAJOR|MINOR|PATCH>
- SUMMARY: "<what changed>"
- REASON: "<why>"
- IMPACT: "<impact>"
- CHANGE_ID: <UE.CHG.YYYY-MM-DD....>

---

## 0) POLICY INTENT (LAW)
- WHAT IT CONTROLS: <domain>
- WHY IT EXISTS: <reason>
- OUTCOME GUARANTEE: <what it guarantees if followed>

---

## 1) SCOPE & BOUNDARIES
### 1.1 Applies to
- <pipelines/entities/artifacts>

### 1.2 Does not apply to
- <out of scope list>

---

## 2) POLICY RULESET (MANDATORY)
Write the rules as a strict list.

### 2.1 Hard rules (blockers)
- RULE: <rule>
  - CHECK: <how to check>
  - FAIL: <what counts as fail>
  - FIX: <how to fix>

(repeat)

### 2.2 Soft rules (recommendations)
- RULE: <rule>
  - CHECK: <how to check>
  - FAIL: <what counts as fail>
  - FIX: <how to fix>

---

## 3) DEFAULTS (IF INPUTS ARE MISSING)
- <default assumption 1>
- <default assumption 2>

---

## 4) NEGATIVE SPEC (WHAT TO AVOID)
- <avoid 1>
- <avoid 2>

---

## 5) INTEGRATION (WHERE USED)
- Typical ORC stages that must apply this CTL:
  - <stage label>
- Entities influenced by this CTL:
  - ENGINES: <RAW optional>
  - SPECIALISTS: <RAW optional>
  - VALIDATORS: <RAW optional>
  - QA: <RAW optional>

---

## 6) OUTPUT IMPACT (WHAT THIS CHANGES)
- What it changes in prompts/contracts:
  - <field>
- What artifacts it affects:
  - <artifact>

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: <OPEN|FIXED>

--- END.

--- CUT HERE ---

---

## 3) INDEX + REGISTRATION CHECKLIST (MANDATORY)
When a new CTL file is created:
1) Add RAW link to `40_CTL__CONTROLLERS/02__INDEX_ALL_CONTROLLERS`
2) Ensure correct FAMILY folder + correct numbering `NN__`
3) Ensure ORC pipelines that rely on it reference it explicitly
4) If this CTL introduces “hard blockers” → ensure matching VAL/QA exists (if required)

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
