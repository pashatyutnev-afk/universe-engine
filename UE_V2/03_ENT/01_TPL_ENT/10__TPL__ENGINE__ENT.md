# TPL ENGINE — ENTITY TEMPLATE (CANON)

FILE: 03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/10__TPL__ENGINE.md
SCOPE: Universe Engine (Games volume) / System Entities / Templates (TPL)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
TEMPLATE_TYPE: ENTITY_ENGINE
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.1
UID: UE.TPL.ENG.001
OWNER: SYSTEM
ROLE: Canonical template to create any ENG Engine file (structure + mini-contract + boundaries + registration checklist).

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Cleaned path placeholders (no double slashes), clarified target file naming, added KB scope + RAW-only references."
- REASON: "Prevent malformed file paths and keep template aligned with boot-first runtime."
- IMPACT: "Engine stamping becomes cleaner and less error-prone."
- CHANGE_ID: UE.CHG.2026-01-20.TPL.ENG.002

---

## 0) PURPOSE
This template is used to create a new engine file inside:
- `03_SYSTEM_ENTITIES/10_ENG__ENGINES/<FAMILY_FOLDER>/NN__<ENGINE_NAME>_ENG.md`

It enforces:
- canonical header
- mandatory boundaries
- mandatory mini-contract (CONSUMES/PRODUCES/DEPENDS_ON/OUTPUT_TARGET)
- minimal output schemas
- registration checklist (index + dependency visibility)

---

## 1) TARGET
TARGET_CLASS: ENG  
TARGET_LAYER: 03_SYSTEM_ENTITIES  
TARGET_FOLDER: `03_SYSTEM_ENTITIES/10_ENG__ENGINES/`

REQUIRED_INDEX (GLOBAL):
- `03_SYSTEM_ENTITIES/10_ENG__ENGINES/02__INDEX_ALL_ENGINES.md`

REQUIRED_REALM_README (GLOBAL):
- `03_SYSTEM_ENTITIES/10_ENG__ENGINES/00__README__ENGINES_REALM.md`

REQUIRED_RULESET (GLOBAL):
- `03_SYSTEM_ENTITIES/10_ENG__ENGINES/01__RULES__ENGINES.md`

---

## 2) STRUCTURE SKELETON (COPY BELOW INTO NEW ENGINE FILE)
IMPORTANT:
- keep the section order exactly
- keep RAW references in interfaces where possible
- do not add second STATUS/LOCK blocks at file end

--- CUT HERE ---

# <ENGINE NAME> — ENGINE (ENG)

FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/<FAMILY_FOLDER>/NN__<ENGINE_NAME>_ENG.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: ENGINE
ENGINE_TYPE: <FAMILY_OR_DOMAIN>
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: <UID>
OWNER: SYSTEM
ROLE: <one line: what this engine deterministically does>

CHANGE_NOTE:
- DATE: <YYYY-MM-DD>
- TYPE: <PATCH|MINOR|MAJOR>
- SUMMARY: "<what changed>"
- REASON: "<why>"
- IMPACT: "<impact>"
- CHANGE_ID: <CHANGE_ID>

---

## 0) PURPOSE (ENGINE LAW)
- <what problem it solves>
- <what it outputs>
- <what it guarantees>

---

## 1) SCOPE & BOUNDARIES (CRITICAL)
### 1.1 In scope
- <hard in-scope statements>

### 1.2 Out of scope
- <hard out-of-scope statements>

### 1.3 Collision rule (anti-duplication)
- If overlap with <other family/engine> → route to: <preferred engine/orc/spc> and stop here.

---

## 2) INPUTS / OUTPUTS (MINI-CONTRACT — MANDATORY)
CONSUMES:
- <1..7 concrete input artifacts>

PRODUCES:
- <1..7 concrete output artifacts>

DEPENDS_ON:
- [] OR
- <explicit dependencies>

OUTPUT_TARGET:
- <KB|PRJ|OUT|AST|LOG|DB> (choose at least one primary)

---

## 3) OUTPUT SCHEMAS (MANDATORY)
For each PRODUCES artifact define:

### 3.X <ARTIFACT_NAME>
MUST:
- <fields required>

OPTIONAL:
- <fields optional>

VALIDATION:
- <what must be true to pass>

STORAGE:
- <where it should live and naming expectations>

---

## 4) WORKFLOW (HOW IT RUNS)
### 4.1 Steps (deterministic)
1) <step>
2) <step>
3) <step>

### 4.2 Default heuristics
- <rules of thumb that stay deterministic>

### 4.3 Failure modes
- <S0 blockers>
- <S1 blockers>
- <S2 non-blocking issues>

---

## 5) QUALITY BAR (WHAT “DONE” MEANS)
- <acceptance bar>
- <no drift rules>

---

## 6) INTEGRATION & XREF (WHEN APPLICABLE)
### 6.1 Required registries / maps
- Dependency registry record needed: YES/NO
- XREF map update needed: YES/NO

### 6.2 External interfaces (RAW references only)
- <RAW link 1>
- <RAW link 2>

---

## 7) KNOWLEDGE BASE (KB) SCOPE
KB INPUTS:
- <what knowledge this engine consumes>

KB OUTPUTS:
- none (unless explicitly producing a KB module artifact)

BOUNDARIES:
- <what this engine will never do>

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: <OPEN|FIXED>

--- END.

--- CUT HERE ---

---

## 3) INDEX + REGISTRATION CHECKLIST (MANDATORY)
When a new engine is created:
1) Add its RAW link to:
   - `03_SYSTEM_ENTITIES/10_ENG__ENGINES/02__INDEX_ALL_ENGINES.md`
2) Ensure it is placed in the correct FAMILY folder
3) Ensure filename number `NN__` matches index order inside FAMILY
4) Ensure FAMILY README exists and is coherent
5) Ensure MINI-CONTRACT is concrete (no vague artifacts)
6) Ensure BOUNDARIES + collision rule exist
7) If DEPENDS_ON is not empty:
   - ensure dependency visibility is not hidden (registry/map if applicable)

---

## 4) INTERFACES (RAW ONLY)
- ENG REALM README:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00__README__ENGINES_REALM.md
- ENG RULESET:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/01__RULES__ENGINES.md
- ENG GLOBAL INDEX:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/02__INDEX_ALL_ENGINES.md

--- END.
