# DEPENDENCY REGISTRY ENGINE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
LAYER: 03_SYSTEM_ENTITIES
FAMILY: 00_GOVERNANCE_ENGINES
DOC_TYPE: ENGINE
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0.0
UID: <UE.ENG.GOV.DEPENDENCY_REGISTRY.001>
OWNER: SYSTEM
ROLE: Single registry of engine dependencies (HARD/SOFT) with strict record format + enforcement rules
LOCK: FIXED

---

## 0) PURPOSE (LAW)

Этот движок — **единый реестр зависимостей** между движками ENG (и при необходимости — между классами ORC/SPC/CTL/VAL/QA).

What this engine is for:
- фиксировать зависимости в стандартизированном формате
- различать HARD vs SOFT зависимости
- запрещать “скрытые зависимости”
- выдавать dependency records при добавлении/изменении DEPENDS_ON
- быть источником для Consistency Engine (сверка)

Primary outcome:
- у каждой зависимости есть запись в реестре и она совпадает с DEPENDS_ON в движках.

Non-goals:
- не является граф-движком оптимизации (это meta/optimization)
- не решает approve/reject изменений (Canon Authority)
- не заменяет Change Control (но обязателен в change package если зависимости менялись)

---

## 1) BOUNDARY (ANTI-DUPLICATION)

Owned here:
- стандарт dependency record
- реестр (append-style или structured list)
- правила конфликтов (cycles/duplicates)
- политика HARD/SOFT

Not owned here:
- audit логирование (Audit Log)
- процесс изменения (Change Control)
- принятие решений по конфликтам (Canon Authority / Decision Approval)

---

## 2) MINI-CONTRACT (MANDATORY)

CONSUMES:
- <ARTIFACT: DEPENDS_ON_DECLARATIONS>         # extracted from engine docs
- <ARTIFACT: CHANGE_PACKAGE_RECORD?>          # when running in change workflow
- <ARTIFACT: PROPOSED_DEPENDENCY_RECORDS?>    # new/edited records

PRODUCES:
- <ARTIFACT: DEPENDENCY_REGISTRY>             # canonical dependency list
- <ARTIFACT: DEPENDENCY_RECORD>               # record (single)
- <ARTIFACT: CYCLE_REPORT?>                   # optional: detected cycles
- <ARTIFACT: CONSISTENCY_INPUT>               # normalized view for Consistency Engine

DEPENDS_ON:
- [00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG]        # dependency changes should be audited
- [00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG]   # dependency changes must be packaged
- [00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG]   # for conflict resolution references

OUTPUT_TARGET:
- `03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG.md` (this spec)
- + canonical registry storage location:
  - `03_SYSTEM_ENTITIES/00_REG__REGISTRIES/REG__DEPENDENCIES.md` (if you have/choose one)
  - or `99_LOGS/LOG__CHANGES.md` (append records)

---

## 3) DEPENDENCY TYPES (STRICT)

Allowed TYPE values:
- TYPE: HARD   # prerequisite: engine cannot run correctly without it
- TYPE: SOFT   # optional: improves quality but not required for correctness

Allowed SCOPE values:
- SCOPE: ENG_ONLY
- SCOPE: CROSS_CLASS   # if dependency references ORC/SPC/CTL/VAL/QA

Allowed STATUS values:
- STATUS: ACTIVE
- STATUS: DEPRECATED
- STATUS: ARCHIVED

Rule:
- HARD dependency on DEPRECATED/ARCHIVED is allowed only with explicit WHY + migration plan.

---

## 4) CANON RECORD FORMAT (MANDATORY)

### 4.1 Dependency record (single line canonical)
Standard (as defined in your ENG INDEX law):

`<FROM>  ->  <TO>  | TYPE:<HARD|SOFT> | WHY:<short reason>`

Where:
- `<FROM>`: `<FAMILY>/<NN__ENGINE_NAME_ENG>`
- `<TO>`: `<FAMILY>/<NN__ENGINE_NAME_ENG>`

Example:
`02_DOMAIN_NARRATIVE_ENGINES/04__SCENE_CONSTRUCTION_ENG  ->  02_DOMAIN_NARRATIVE_ENGINES/02__STORY_STRUCTURE_ENG  | TYPE:HARD | WHY:scenes require structure`

### 4.2 Extended record (optional block)
If a line is not enough, add an extended block (still canonical):

- RECORD_ID: <UE.DEP.YYYY-MM-DD.NNN>
- FROM: <FAMILY>/<ENGINE>
- TO: <FAMILY>/<ENGINE>
- TYPE: <HARD|SOFT>
- WHY:
- SCOPE:
- CREATED_DATE:
- OWNER:
- MIGRATION_PLAN: <optional>
- NOTES:

Rule:
- If extended block exists, the single-line record must still exist.

---

## 5) REGISTRY STRUCTURE (RECOMMENDED)

### 5.1 Registry grouped by FROM engine
- FROM: 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG
  - -> 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG | TYPE:HARD | WHY: must audit canon changes
  - -> 00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG | TYPE:HARD | WHY: requires decisions
  - -> 00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG | TYPE:SOFT | WHY: recommended post-verify

### 5.2 Optional: adjacency list by family
For quick scanning, but do not duplicate canon source. Keep one registry file.

---

## 6) HARD RULES (ENFORCEMENT)

- R1: No hidden dependency  
  If engine A lists DEPENDS_ON engine B → registry MUST contain record A -> B (S1/S0 depending on policy)

- R2: Registry cannot contain non-existing engines  
  If a record references an engine not registered in `02__INDEX_ALL_ENGINES.md` → S0

- R3: Duplicate dependency lines forbidden  
  Same FROM->TO duplicates must be merged into one record.

- R4: Cycles policy  
  Cycles are allowed only if:
  - recorded as cycle exception
  - WHY includes “cycle reason”
  - break mechanism described (stage gate/approval/ordering)
  - approved by decision (Canon Authority/Decision Approval)

- R5: HARD on deprecated  
  HARD dependency on DEPRECATED requires MIGRATION_PLAN or explicit waiver.

---

## 7) OPERATION MODEL (HOW IT WORKS)

### 7.1 Trigger
Run when:
- DEPENDS_ON section changes in any engine
- new engine is added
- engine is deprecated/archived
- family structure changes

### 7.2 Steps
1) Extract DEPENDS_ON declarations from engines (or accept as input list)
2) Normalize names into `<FAMILY>/<NN__ENGINE_ENG>`
3) Compare against registry
4) Produce:
   - missing records list
   - stale records list
   - cycle report (optional)
5) Update registry (append or structured update) via change control

---

## 8) OUTPUT ARTIFACTS

### 8.1 DEPENDENCY_REGISTRY (REQUIRED)
- A canonical list of dependency records in the standard format.

### 8.2 CYCLE_REPORT (OPTIONAL)
FORMAT:
- CYCLE_ID
- NODES: [A, B, C]
- WHY
- BREAK_MECHANISM
- APPROVAL_REF

---

## 9) EXAMPLES (GOOD / BAD)

### 9.1 Good example
Engine:
- 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG lists DEPENDS_ON Audit Log + Canon Authority
Registry contains:
- Change_Control -> Audit_Log | TYPE:HARD | WHY: must audit
- Change_Control -> Canon_Authority | TYPE:HARD | WHY: decision required

### 9.2 Bad example
Engine DEPENDS_ON includes:
- 02_DOMAIN_NARRATIVE_ENGINES/99__SOMETHING_ENG
But engine not in index.
Result:
- S0 violation (non-existing dependency)

Fix:
- register engine in index or remove dependency.

---

## 10) REL / XREF (UID-FIRST)

REL:
- REL: SUPPORTS | TARGET_UID: <UE.ENG.GOV.CONSISTENCY.001> | WHY: consistency checks registry alignment
- REL: REQUIRES | TARGET_UID: <UE.ENG.GOV.CHANGE_CONTROL.001> | WHY: dependency updates must be packaged
- REL: COORDINATES | TARGET_UID: <UE.ENG.GOV.AUDIT_LOG.001> | WHY: dependency changes must be auditable

RULE:
- raw links in indices; here is registry format and policy.
- records must reference engines exactly as in index naming.

--- END.
