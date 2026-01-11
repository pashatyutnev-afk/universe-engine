# TPL ENGINE — ENTITY TEMPLATE (CANON)
FILE: 03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/10__TPL__ENGINE.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: TEMPLATES (TPL)
DOC_TYPE: TEMPLATE
TEMPLATE_TYPE: ENTITY_ENGINE
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.ENG.001
OWNER: SYSTEM
ROLE: Canonical template to create any ENG Engine file (structure + mini-contract + registration checklist)

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Rebuilt ENG engine template: canonical header, mandatory mini-contract, RAW-only references, index registration checklist."
- REASON: "Uniform engine files; prevents missing contracts and non-indexed engines."
- IMPACT: "ENG engines become deterministic, readable, and audit-friendly."
- CHANGE_ID: UE.CHG.2026-01-11.TPL.ENG.001

---

## 0) PURPOSE
This template is used to create a new file:
`03_SYSTEM_ENTITIES/10_ENG__ENGINES/<FAMILY>/NN__<ENGINE_NAME>_ENG`

It enforces:
- canonical engine header
- mandatory mini-contract (CONSUMES/PRODUCES/DEPENDS_ON/OUTPUT_TARGET)
- strict sections order
- registration checklist (index + dependency registry)

---

## 1) TARGET
TARGET_CLASS: ENG  
TARGET_FOLDER: `03_SYSTEM_ENTITIES/10_ENG__ENGINES/`  
REQUIRED_INDEX_OWNER (GLOBAL): `03_SYSTEM_ENTITIES/10_ENG__ENGINES/02__INDEX_ALL_ENGINES`  
REQUIRED_FAMILY_README: `03_SYSTEM_ENTITIES/10_ENG__ENGINES/<FAMILY>/00__README__<FAMILY>_ENGINES`

---

## 2) STRUCTURE SKELETON (COPY BELOW INTO NEW ENGINE FILE)
> IMPORTANT: keep the section order exactly.
> NAV references inside engines should be RAW-only whenever possible.

--- CUT HERE ---

# <ENGINE TITLE> — ENGINE (ENG)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/<FAMILY_PATH>/NN__<ENGINE_NAME>_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
ENGINE_TYPE: <GOVERNANCE|CORE|DOMAIN|STYLE|PRODUCTION|SOUND|META>
LEVEL: <L1|L2|L3|L4>
STATUS: <DRAFT|ACTIVE|DEPRECATED|ARCHIVED>
LOCK: <OPEN|FIXED>
VERSION: <X.Y.Z>
UID: <UE.ENG.<FAMILY>.<NAME>.<NNN>>
OWNER: SYSTEM
ROLE: <One-line: what this engine does and why it exists>

CHANGE_NOTE:
- DATE: <YYYY-MM-DD>
- TYPE: <MAJOR|MINOR|PATCH>
- SUMMARY: "<what changed>"
- REASON: "<why>"
- IMPACT: "<what it changes>"
- CHANGE_ID: <UE.CHG.YYYY-MM-DD....>

---

## 0) PURPOSE (ENGINE LAW)
- <What problem this engine solves>
- <When to invoke it>
- <What it guarantees>

---

## 1) SCOPE & BOUNDARIES (CRITICAL)
### 1.1 In scope
- <bullet list>

### 1.2 Out of scope
- <bullet list>

### 1.3 Anti-duplication note
- <What this engine must NOT duplicate; where the neighboring responsibility is>

---

## 2) INPUTS / OUTPUTS (MINI-CONTRACT — MANDATORY)
CONSUMES:
- <1..5 input artifact types or references>

PRODUCES:
- <1..5 output artifact types or references>

DEPENDS_ON:
- [] OR
- - <RAW link to prerequisite engine(s)>

OUTPUT_TARGET:
- <Where outputs are placed (project path / artifact layer / KB / logs etc.)>

---

## 3) WORKFLOW (HOW IT RUNS)
### 3.1 Steps
1) <step>
2) <step>
3) <step>

### 3.2 Default heuristics
- <default rules used if nothing specified>

### 3.3 Failure modes
- <common failure>
- <how to detect>
- <how to fix>

---

## 4) QUALITY BAR (WHAT “DONE” MEANS)
- <acceptance criteria bullets>
- <what must be true in output>

---

## 5) INTEGRATION & XREF (MANDATORY WHEN APPLICABLE)
### 5.1 Required registries / maps
- Dependency registry record needed? <YES/NO>
- XREF map update needed? <YES/NO>

### 5.2 External interfaces (RAW references only)
- <RAW: ...>
- <RAW: ...>

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: <OPEN|FIXED>

--- END.

--- CUT HERE ---

---

## 3) INDEX + REGISTRATION CHECKLIST (MANDATORY)
When a new engine is created:
1) Add its RAW link to `10_ENG__ENGINES/02__INDEX_ALL_ENGINES`
2) Ensure it is placed in the correct FAMILY folder
3) Ensure filename number `NN__` matches index order inside FAMILY
4) Ensure FAMILY README exists and is coherent
5) If DEPENDS_ON is not empty:
   - add record to `00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG`
   - update any required XREF maps (if pipeline uses them)

---

## 4) ANTI-SPRAWL NOTE
Do not create a new template variant for small stylistic differences.
If the engine class changes contract → update this template or create one additional template only if truly necessary.

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
