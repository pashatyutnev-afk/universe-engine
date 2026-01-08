# GOVERNANCE ENGINE — TEMPLATE (CANON)
FILE: NN__<ENGINE_NAME>_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
DOC_TYPE: ENGINE
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: DRAFT
VERSION: 0.1
UID: <UE.ENG.GOV.ENGINE.NN.###>
OWNER: <SYSTEM|ROLE|PERSON>
ROLE: Governance engine spec + enforcement contract
LOCK: OPEN

---

## 0) PURPOSE (LAW)

**What this engine is for:**
- <1–3 sentences: what governance rule/process it enforces>

**Primary outcome:**
- <1 sentence: what becomes true after running this engine>

**Non-goals (hard):**
- Does NOT produce domain narrative/character/world content
- Does NOT generate production artifacts (visual/audio/video) directly
- Does NOT replace other governance engines unless explicitly declared in rules

---

## 1) BOUNDARY (ANTI-DUPLICATION)

### 1.1 Owned area (this engine owns)
- <bullet list: exact governance area>

### 1.2 Forbidden overlap (this engine must NOT do)
- <bullet list of engines/areas it must not duplicate>
- If overlap is unavoidable → must be declared in `DEPENDS_ON` + dependency registry record

### 1.3 Interface contract (what it touches)
- Can read: indexes, registries, audit logs, decisions, change plans, risk notes
- Can require: status/lock/version/uid compliance
- Cannot silently modify canon (any change must go through change control)

---

## 2) MINI-CONTRACT (MANDATORY)

CONSUMES:
- <ARTIFACT_TYPE_1>
- <ARTIFACT_TYPE_2>
- <... up to 5>

PRODUCES:
- <ARTIFACT_TYPE_1>
- <ARTIFACT_TYPE_2>
- <... up to 5>

DEPENDS_ON:
- []  # or:
- - 00_GOVERNANCE_ENGINES/NN__<ENGINE>_ENG
- - 01_CORE_ENGINES/NN__<ENGINE>_ENG

OUTPUT_TARGET:
- <Where outputs live, as a path rule / storage map reference>
- Example: `99_LOGS/LOG__AUDIT.md` or `03_SYSTEM_ENTITIES/.../00_REG__...`

---

## 3) OPERATION MODEL (HOW IT WORKS)

### 3.1 Trigger (when to run)
- <event or condition>
- Examples:
  - any canon index edit
  - new engine added
  - status/lock change
  - dependency added/removed

### 3.2 Inputs (minimal required)
- <required inputs with conditions>

### 3.3 Steps (deterministic pipeline)
1) **Collect** required inputs (indexes/headers/records)
2) **Validate** invariants (status/lock/uid/versioning rules)
3) **Detect** violations or missing records
4) **Decide**: allow / block / require approval
5) **Produce** outputs (audit / decision / change plan / registry record)
6) **Link** outputs (xref) and finalize

### 3.4 Output semantics
- If PASS → what gets written/updated
- If FAIL → what block/violation artifact is produced
- If NEEDS_APPROVAL → what decision artifact is required

---

## 4) HARD GATES (ENFORCEMENT)

> If any HARD gate fails → engine returns **BLOCK** (cannot proceed).

### 4.1 Gate list
- G1: <Gate name> — <condition> — FAIL action: <what happens>
- G2: <...>
- G3: <...>
- G4: <...>
- G5: <...>

### 4.2 Typical gate set for governance (recommended)
- Single-source-of-truth index respected (existence rule)
- Header compliance (STATUS/LOCK/VERSION/UID single instance)
- Numbering + naming match (NN in name == registry order)
- Dependency declared (DEPENDS_ON + registry record)
- Audit record created for any canon change

---

## 5) OUTPUT ARTIFACTS (STANDARD FORMS)

### 5.1 Audit Record (if applicable)
- Minimal fields:
  - DATE
  - CHANGE_TYPE
  - AFFECTED_FILES
  - REASON
  - IMPACT
  - APPROVER (if required)
  - UID references

### 5.2 Decision Record (if applicable)
- Problem / Options / Decision / Rationale / Consequences
- Approval chain (who can approve)

### 5.3 Violation/Blocker Record (if applicable)
- Rule violated
- Evidence (file/section)
- Severity (S0–S3 if your standards use it)
- Fix instructions

---

## 6) EXAMPLES (GOOD / BAD)

### 6.1 Good example
- <short scenario + correct outputs>

### 6.2 Bad example
- <short scenario + why blocked + what artifact produced>

---

## 7) FAILURE MODES & EDGE CASES

- Cyclic dependency discovered → allowed only if explicitly documented + approved
- Partial updates (index updated but file missing) → BLOCK
- File exists but not in index → ignored / non-canon (report optionally)
- Deprecated engine still depended on → warn or block depending on policy

---

## 8) REL / XREF (UID-FIRST)

- XREF: <related registries / maps>
- Related engines:
  - 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG
  - 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG
  - 00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG
- Notes:
  - Keep xref as stable references; avoid duplicating index lists

---
LOCK: <OPEN|FIXED>
