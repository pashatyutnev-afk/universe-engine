# DEPENDENCY REGISTRY ENGINE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 00_GOVERNANCE_ENGINES
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ENG.GOV.DEPENDENCY_REGISTRY.001
OWNER: SYSTEM
ROLE: Single canonical dependency registry (HARD/SOFT) for engines. Enforces "no hidden dependencies" and produces/validates DEPENDENCY_RECORDS against engines' DEPENDS_ON.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Dependency registry upgraded to full canonical system: single storage, record format, cycle rules, exception protocol, validation modes."
- REASON: "Prevent invisible coupling and cascading breaks across families/layers."
- IMPACT: "Dependencies become explicit, checkable, and enforceable by Consistency and Change Control."
- CHANGE_ID: UE.CHG.2026-01-08.GOV.DEP.001

---

## 0) PURPOSE (LAW)

Dependency Registry Engine обеспечивает правило:
> Любая зависимость должна быть явной.

Он делает две вещи:
1) Хранит **реестр зависимостей** (DEP RECORDS) в одном каноническом месте.
2) Валидирует согласованность:
   - DEPENDS_ON в движках
   - и DEPENDENCY_RECORDS в реестре

Non-goals:
- не решает “можно/нельзя менять” (это Risk Safety / Canon Authority)
- не применяет изменения (это Change Control)
- не диагностирует все ошибки по всему репо (это Consistency), но Consistency использует его как источник для проверки D5

---

## 1) SINGLE STORAGE POLICY (HARD)

Единственное каноническое хранилище DEPENDENCY_RECORDS:
- `99_LOGS/LOG__CHANGES.md`

Запрещено:
- заводить “ещё один” dependency registry файл как SoT
- хранить зависимости в нескольких местах без явного закона tiering

Если нужен отдельный файл в будущем:
- он должен быть создан как канон и явно объявлен как storage policy change через Change Control + Canon Authority.

---

## 2) MINI-CONTRACT (MANDATORY)

CONSUMES:
- DEPENDENCY_DECLARATIONS          # extracted from engine files' DEPENDS_ON
- CHANGE_NOTE                      # when writing new records
- CHANGE_PACKAGE_RECORD            # when part of a change
- AFFECTED_FILES_LIST              # for delta validation

PRODUCES:
- DEPENDENCY_RECORDS               # canonical record lines (append-only within changes log section)
- DEPENDENCY_VALIDATION_REPORT
- CYCLE_REPORT?                    # when cycles detected
- EXCEPTION_REQUEST?               # when a cycle/forbidden edge must be approved

DEPENDS_ON:
- 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG
- 00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG
- 00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG
- 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG

OUTPUT_TARGET:
- 99_LOGS/LOG__CHANGES.md

---

## 3) RECORD MODEL (CANON)

### 3.1 Allowed dependency types (strict)
TYPE:
- HARD   # cannot run / cannot be valid without dependency
- SOFT   # improves quality or convenience, but not required

### 3.2 Allowed dependency directions
Direction:
- A -> B means: A depends on B (B must exist before A is valid)

### 3.3 Canon record format (single-line)
Every record is exactly:

`<FROM>  ->  <TO>  | TYPE:<HARD|SOFT> | WHY:<short reason> | SCOPE:<LOCAL|FAMILY|LAYER|GLOBAL> | CHANGE_ID:<UE.CHG...>`

Where:
- FROM = `<FAMILY>/<NN__ENGINE_FILE>`
- TO   = `<FAMILY>/<NN__ENGINE_FILE>`
- WHY  = 3..120 chars, must be meaningful
- SCOPE = impact scope of that dependency edge

Example:
`02_DOMAIN_NARRATIVE_ENGINES/04__SCENE_CONSTRUCTION_ENG.md  ->  02_DOMAIN_NARRATIVE_ENGINES/02__STORY_STRUCTURE_ENG.md  | TYPE:HARD | WHY:scenes require story structure | SCOPE:FAMILY | CHANGE_ID:UE.CHG.2026-01-08.X.001`

Hard rule:
- no free-form formats
- no missing fields

---

## 4) SOURCE OF TRUTH RULE (DUAL DECLARATION)

We maintain **dual declaration** for safety:

- Engine file declares:
  `DEPENDS_ON: [ ... ]`

- Registry declares:
  `FROM -> TO ...`

Consistency must enforce:
- every DEPENDS_ON edge has a registry record (at least SOFT/HARD as decided)
- registry record must not reference unknown engines (must exist in ENG index)

This avoids “dependency hidden in one place”.

---

## 5) MODES (MANDATORY)

### Mode S — SCAN (extract declarations)
Inputs:
- engine files scope
Output:
- DEPENDENCY_DECLARATIONS list

### Mode V — VALIDATE (registry vs declarations)
Inputs:
- DEPENDENCY_DECLARATIONS
- DEPENDENCY_RECORDS (from storage)
Output:
- DEPENDENCY_VALIDATION_REPORT:
  - missing records
  - orphan registry edges
  - mismatched type (optional policy)
  - cycles

### Mode R — RECORD (write new registry edges)
Inputs:
- CHANGE_NOTE + CHANGE_ID
- list of edges to add/remove/replace
Output:
- append canonical records to storage section in LOG__CHANGES.md

Hard rule:
- RECORD can only be performed as part of a change package (Change Control) if canon-impacting.

---

## 6) CYCLES (RULES)

### 6.1 Cycle definition
Cycle = path A -> ... -> A

### 6.2 Default policy
- Cycles are discouraged.
- Cycles are allowed ONLY if:
  - they are SOFT edges OR
  - explicitly approved with exception record (see 7)

### 6.3 HARD cycles
Any HARD cycle is S0 by default.

Reason:
- hard cycles make ordering impossible and break deterministic pipeline.

---

## 7) EXCEPTIONS (STRICT PROTOCOL)

If a cycle or forbidden edge is needed, you must create an exception request that includes:
- EXC_ID: UE.EXC.YYYY-MM-DD.NNN
- CHANGE_ID:
- EDGE: FROM -> TO
- TYPE: HARD|SOFT
- WHY:
- MITIGATION: how ordering is handled (break edge at runtime? staging? cache?)
- EXPIRY_DATE: optional but strongly recommended
- APPROVER: role/name
- DECISION_REF: decision id (recommended)

Exceptions must be recorded in:
- LOG__CHANGES.md (same change context)

No exception record -> edge must be rejected.

---

## 8) VIOLATIONS (S0..S3)

### S0 (blockers)
- S0-1 Registry references engine not in ENG index (unknown entity)
- S0-2 HARD cycle exists without exception
- S0-3 Canon change introduces new DEPENDS_ON but no registry record
- S0-4 Duplicate edge with conflicting TYPE (HARD vs SOFT) without resolution record
- S0-5 Storage policy violated (dependency records written elsewhere as SoT)

### S1 (high)
- Missing WHY or empty WHY
- SCOPE missing/invalid
- CHANGE_ID missing in record
- Engine DEPENDS_ON list missing entirely (if engine is canon and requires it by template)

### S2 (medium)
- SOFT cycle without explicit note (warn)
- redundant edges (A->B appears but B no longer exists; likely stale)

### S3 (low)
- formatting whitespace issues (still should be normalized)

---

## 9) DEPENDENCY_VALIDATION_REPORT (CANON OUTPUT)

DEPENDENCY_VALIDATION_REPORT:
- REPORT_ID: UE.DEPVAL.YYYY-MM-DD.NNN
- DATE:
- MODE: VALIDATE
- TARGET_SCOPE:
- RESULT: PASS|WARN|FAIL
- COUNTS: S0..S3
- MISSING_RECORDS:
  - <FROM> -> <TO>
- ORPHAN_RECORDS:
  - <FROM> -> <TO>
- CYCLES:
  - cycle path list
- FIX_PLAN:
  - ordered actions

---

## 10) GOOD / BAD EXAMPLES

### GOOD
Engine:
DEPENDS_ON: [00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md]

Registry record exists:
`00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md  ->  00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md  | TYPE:HARD | WHY:decisions must be auditable | SCOPE:FAMILY | CHANGE_ID:UE.CHG.2026-01-08.GOV.AUTH.001`

### BAD (hidden dependency)
Engine lists DEPENDS_ON, registry missing -> S0-3 FAIL

### BAD (unknown engine)
Registry points to file not in ENG index -> S0-1 FAIL

### BAD (hard cycle)
A HARD->B and B HARD->A without exception -> S0-2 FAIL

---

## 11) INTEGRATION

- Consistency Engine uses this for dependency checks (D5).
- Change Control requires dependency updates when DEPENDS_ON changes.
- Canon Authority can reject changes with S0 dependency violations.
- Audit Log records that dependency records were updated (as part of change package).

---

## 12) REFERENCES (RAW ONLY)

Storage:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/99_LOGS/LOG__CHANGES.md

Consistency:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md

Change Control:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md

Canon Authority:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md

Rule Hierarchy:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG.md

Audit Log:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md

--- END.
