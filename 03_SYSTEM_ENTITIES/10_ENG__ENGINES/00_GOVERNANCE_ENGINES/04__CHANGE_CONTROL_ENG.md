# CHANGE CONTROL ENGINE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md

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
UID: UE.ENG.GOV.CHANGE_CONTROL.001
OWNER: SYSTEM
ROLE: Defines the mandatory change pipeline for canon artifacts (laws/standards/indexes/engines/registries). Prevents silent drift, enforces audit, and blocks unsafe merges.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Canonical change pipeline defined: change package format, gates, approvals, audit/memory rules, emergency path."
- REASON: "Stop conflicts, missing registry updates, and uncontrolled edits of FIXED canon."
- IMPACT: "Every canon change becomes trackable, reversible, and consistent."
- CHANGE_ID: UE.CHG.2026-01-08.GOV.CC.001

---

## 0) PURPOSE (LAW)

Change Control Engine — это закон “как мы меняем систему”.

Он гарантирует:
- **нет тихих правок** FIXED/ACTIVE канона
- **любая правка** имеет change package, причину, влияние и след в логах
- **любой конфликт** обязан быть либо решён, либо остановлен
- **любое изменение состава/порядка** в индексах фиксируется через audit + memory

Non-goals:
- не определяет “кто главный” (это Rule Hierarchy)
- не определяет “канон/не канон” (это Canon Authority)
- не выполняет факт-проверки структуры репы (это Consistency), но требует её прохождения

---

## 1) MINI-CONTRACT (MANDATORY)

CONSUMES:
- CHANGE_PROPOSAL                     # короткое описание "что меняем и зачем"
- TARGET_LIST                         # список файлов/разделов/UID, которых касается правка
- DIFF_SUMMARY                        # что добавлено/удалено/переименовано
- IMPACT_REPORT?                      # required for MAJOR or cross-layer changes
- RISK_REPORT?                        # required when touching LAW/INDEX/FIXED or wide scope
- CONFLICT_REPORT?                    # if a conflict is detected or suspected
- APPROVAL_CONTEXT?                   # роли/решение/подписи

PRODUCES:
- CHANGE_PACKAGE (CHG)                # единый пакет изменения (формат ниже)
- APPROVAL_RECORD                     # решение: approve/reject/request changes
- AUDIT_LOG_ENTRY                     # запись в аудит
- VERSION_MEMORY_ENTRY                # запись в память версий/переходов
- RELEASE_NOTE?                       # если изменение влияет на usage
- ROLLBACK_PLAN                       # обязательный план отката для MAJOR/HARD changes

DEPENDS_ON:
- 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG
- 00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG
- 00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG
- 00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG
- 00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG
- 00_GOVERNANCE_ENGINES/07__DECISION_APPROVAL_ENG
- 00_GOVERNANCE_ENGINES/08__SCOPE_IMPACT_ENG
- 00_GOVERNANCE_ENGINES/09__RISK_SAFETY_ENG
- 00_GOVERNANCE_ENGINES/10__VERSIONING_MEMORY_ENG

OUTPUT_TARGET:
- 99_LOGS/LOG__AUDIT.md
- 99_LOGS/LOG__CHANGES.md

---

## 2) CANON CHANGE BOUNDARY (WHAT COUNTS AS "CANON CHANGE")

Canon change = любое изменение, которое влияет на:
- `00_INDEX/*` (root indexes / existence laws)
- `01_SYSTEM_LAW/*`
- `02_STANDARDS/*`
- любые `__INDEX__` / `INDEX_ALL_*` / `MASTER INDEX` / registries
- любые файлы со `STATUS: ACTIVE` и/или `LOCK: FIXED`
- структуру путей, нумерацию, UID, порядок в индексах
- cross-links/raw-links, если они обязательны по стандартам

Если правка попадает в этот список — без pipeline она **invalid**.

---

## 3) CHANGE TYPES (STRICT SET)

TYPE:
- PATCH  — мелкая правка без изменения смысла/поведения (опечатки, ясность, формат, ссылка)
- MINOR  — небольшое изменение поведения в одном месте без миграции
- MAJOR  — изменение поведения/структуры/правил, требует impact + rollback
- MIGRATION — перенос/переименование/перестройка структуры, требует migration map
- EMERGENCY — аварийная правка (S0 breach), идёт по специальному emergency-пути

Дополнительно:
- CHANGE_SCOPE: LOCAL | FAMILY | LAYER | GLOBAL
- CHANGE_FORCE: SOFT | HARD
  - HARD = может ломать совместимость или требует обязательной адаптации других артефактов

---

## 4) REQUIRED ARTIFACTS (WHAT MUST EXIST)

### 4.1 CHANGE_PACKAGE (CHG) — mandatory for any canon change
Формат CHG (обязательные поля):

CHG:
- CHANGE_ID: UE.CHG.YYYY-MM-DD.<DOMAIN>.<SEQ>
- TYPE:
- SCOPE:
- TARGETS: [list of file paths + optional section anchors]
- SUMMARY: 1-3 lines
- REASON:
- IMPACT: short
- COMPATIBILITY: "backward|breaking|mixed"
- DEPENDENCY_UPDATES: [required registry updates]
- CONFLICTS: "none|possible|detected"
- REQUIRED_GATES: [list]
- ROLLBACK_PLAN: (required for MAJOR/MIGRATION/HARD)
- APPROVAL_REQUIRED: YES/NO
- AUDIT_REQUIRED: YES
- MEMORY_REQUIRED: YES

### 4.2 DIFF_SUMMARY — mandatory
- Added files
- Removed files
- Renamed/moved files
- Edited files (meaningful)

### 4.3 IMPACT_REPORT — mandatory if:
- TYPE is MAJOR/MIGRATION/EMERGENCY
- touching LAW / INDEX / FIXED
- changing naming/UID/version policies
- changing “existence rules” or registry structures

### 4.4 RISK_REPORT — mandatory if:
- cross-layer change
- change affects pipelines
- change increases ambiguity/authority conflicts
- change introduces overrides

### 4.5 APPROVAL_RECORD — mandatory if:
- anything touches FIXED or LAW or INDEX
- MAJOR/MIGRATION
- any conflict detected

---

## 5) PIPELINE (MANDATORY GATES)

Pipeline is deterministic. Gates must be passed in order.

### G0 — Proposal Gate (always)
Input: CHANGE_PROPOSAL + TARGET_LIST  
Output: CHG skeleton  
Rule: if target unclear -> stop

### G1 — Classification Gate (always)
Decide TYPE/SCOPE/FORCE  
Rule: misclassification = reject

### G2 — Hierarchy Gate (required if rule conflict is possible)
Call Rule Hierarchy Engine:
- identify applicable tiers
- detect collisions
Output: CONFLICT_REPORT or “none”

### G3 — Impact Gate (conditional)
Required if MAJOR/MIGRATION/LAW/INDEX/FIXED.
Output: IMPACT_REPORT

### G4 — Risk Gate (conditional)
Required if broad scope, overrides, emergency, or hard changes.
Output: RISK_REPORT

### G5 — Dependency Gate (conditional)
If new engine/file added, moved, or changed dependencies:
- update dependency registry records
Output: DEPENDENCY_UPDATES list

### G6 — Consistency Gate (always for canon change)
Run Consistency Engine checks:
- naming/UID/version rules satisfied
- indexes updated
- raw-links valid (where mandatory)
Output: CONSISTENCY_OK or FAIL

### G7 — Approval Gate (conditional)
If approval required (see 4.5):
- Decision Approval Engine issues APPROVAL_RECORD
- Canon Authority validates canon acceptance
Output: APPROVED / REJECTED / NEEDS_CHANGES

### G8 — Audit + Memory Gate (always)
Any canon change must create:
- AUDIT_LOG_ENTRY
- VERSION_MEMORY_ENTRY

### G9 — Publish Gate (always if approved)
- apply changes
- update registries/indexes
- publish release note if needed

No skipping gates.

---

## 6) THE GOLDEN RULE: INDEX + EXISTENCE

If you:
- add a file that is canon-governed
- rename/move a canon file
- delete a canon file
- change the order inside an INDEX

Then you MUST:
1) update the canonical index that controls existence/order
2) record in Audit Log
3) record in Versioning Memory (rename/migration mapping)

If step 1 is missing -> change is invalid (S0).

---

## 7) LOCK ENFORCEMENT (FIXED MEANS FIXED)

If a file has `LOCK: FIXED`:
- direct edits are forbidden outside pipeline
- any proposed change MUST be MAJOR or MIGRATION (never PATCH by default)
- approval is always required
- rollback plan is always required

If FIXED was changed without:
- APPROVAL_RECORD
- AUDIT_LOG_ENTRY
- VERSION_MEMORY_ENTRY
then state is **breach** and must be reverted or emergency-waived.

---

## 8) EMERGENCY PATH (S0 BREACH HANDLING)

Emergency allowed only when:
- S0 breach detected (see section 11)
- system cannot function / canon corrupted / existence broken

Emergency pipeline (compressed but mandatory):
E1 — Create EMERGENCY CHG with minimal scope  
E2 — Risk Safety quick assessment (must exist)  
E3 — Canon Authority provisional approve with EXPIRY (required)  
E4 — Apply fix  
E5 — Audit + Memory immediately  
E6 — Within 72h: convert into proper MAJOR change package or revert

Emergency without expiry is forbidden.

---

## 9) ROLLBACK LAW (REQUIRED FOR MAJOR/MIGRATION/HARD)

Rollback plan must include:
- ROLLBACK_TRIGGER (what signals failure)
- ROLLBACK_STEPS (ordered)
- AFFECTED_INDEXES (list)
- RESTORE_TARGET_VERSION (exact)
- DATA_LOSS_NOTE (if any)
- OWNER/RESPONSIBLE

If rollback is impossible -> must be stated explicitly and escalated to Risk Safety.

---

## 10) RENAMES / MOVES / DELETES (MIGRATION MAP LAW)

Any rename/move/delete of canon file requires MIGRATION_MAP entry:

MIGRATION_MAP:
- OLD_PATH:
- NEW_PATH: (or DELETED)
- OLD_UID:
- NEW_UID: (usually same; change must be justified)
- WHY:
- IMPACT:
- REFERENCES_TO_UPDATE: [indexes, xrefs, registries]
- MEMORY_REF: required

If you rename but forget memory mapping -> future navigation breaks (S0).

---

## 11) ABSOLUTE BLOCKERS (S0) — STOP CONDITIONS

S0-1 Index not updated while affecting existence/order
S0-2 Any conflict detected but not resolved nor escalated
S0-3 FIXED canon edited outside pipeline
S0-4 UID collision or UID changed without justification + memory
S0-5 Dependency introduced but not registered
S0-6 Raw-link required by standard but missing/broken in index
S0-7 Two “single source of truth” docs compete in same scope (authority collision)

If S0 -> REJECT or EMERGENCY with expiry.

---

## 12) QUALITY RULES (TO PREVENT FUTURE DRIFT)

Mandatory principles:
- **one change package** per coherent intent (no mixed unrelated edits)
- **no hidden changes** (diff summary must mention everything)
- **no silent overrides** (override protocol must be used if deviating)
- **no orphan files** (if not in canon index -> treated as non-existent)
- **no duplicate registries** for same domain unless explicitly tiered

---

## 13) OUTPUT RECORD FORMATS (CANON)

### 13.1 AUDIT_LOG_ENTRY (minimal)
AUDIT:
- DATE:
- CHANGE_ID:
- TYPE:
- TARGETS:
- SUMMARY:
- APPROVAL: (ref)
- LINKS: (paths)
- NOTES:

### 13.2 VERSION_MEMORY_ENTRY (minimal)
MEMORY:
- DATE:
- CHANGE_ID:
- BEFORE: (version/path)
- AFTER: (version/path)
- MIGRATION_MAP?: (ref)
- WHY:
- COMPATIBILITY:
- NOTES:

### 13.3 APPROVAL_RECORD (minimal)
APPROVAL:
- DATE:
- CHANGE_ID:
- DECISION: APPROVE | REJECT | NEEDS_CHANGES
- CONDITIONS: []
- APPROVER_ROLE:
- WHY:

---

## 14) HOW THIS ENGINE FITS THE SYSTEM (INTEGRATION)

- Rule Hierarchy Engine: определяет, кто главнее при конфликтах
- Canon Authority Engine: утверждает канон и право правки FIXED
- Decision Approval Engine: формализует “approve/reject”
- Scope Impact Engine: делает impact report стандартным
- Risk Safety Engine: запрещает опасные правки без обоснования
- Dependency Registry Engine: делает зависимости явными и проверяемыми
- Consistency Engine: валидирует структуру/UID/индексы/ссылки
- Versioning Memory Engine: сохраняет историю изменений и миграций
- Audit Log Engine: фиксирует каждую правку канона

Change Control — это “позвоночник”, который заставляет всех работать вместе.

---

## 15) REFERENCES (RAW ONLY)

Audit Log Engine:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md

Canon Authority Engine:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md

Rule Hierarchy Engine:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG.md

Consistency Engine:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md

Dependency Registry Engine:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG.md

Decision Approval Engine:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/07__DECISION_APPROVAL_ENG.md

Scope Impact Engine:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/08__SCOPE_IMPACT_ENG.md

Risk Safety Engine:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/09__RISK_SAFETY_ENG.md

Versioning Memory Engine:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/10__VERSIONING_MEMORY_ENG.md

Root / Laws / Standards:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/00_INDEX/00__ROOT_INDEX.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__INDEX__SYSTEM_LAW.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/00__INDEX__STANDARDS.md

Logs:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/99_LOGS/LOG__AUDIT.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/99_LOGS/LOG__CHANGES.md

--- END.
