# CANON AUTHORITY ENGINE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md

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
UID: UE.ENG.GOV.CANON_AUTHORITY.001
OWNER: SYSTEM
ROLE: Final canon gate. Produces canonical DECISION_RECORD that determines whether a change becomes canon (ACCEPT/REJECT/ACCEPT_WITH_CONDITIONS).

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Canon Authority upgraded to fully specified decision gate (canon criteria, mandatory inputs, waivers, decision formats, enforcement)."
- REASON: "Eliminate ambiguous canon states and silent acceptance."
- IMPACT: "Canon becomes deterministic: existence/navigation/locks/UID rules enforced through explicit decision."
- CHANGE_ID: UE.CHG.2026-01-08.GOV.AUTH.001

---

## 0) PURPOSE (LAW)

Canon Authority Engine отвечает на один вопрос:
> “Это изменение становится частью канона или нет?”

Он не проверяет качество текста как редактор и не выполняет изменения руками.
Он принимает **решение** на базе:
- закона канона (existence / authority / lock)
- отчётов scope/risk/consistency (когда требуются)
- прозрачности зависимостей и миграции
- наличия audit trail

Primary outcome:
- DECISION_RECORD (canonical) с типом ACCEPT / REJECT / ACCEPT_WITH_CONDITIONS.

Non-goals (hard):
- не является change workflow (это Change Control)
- не является post-verify проверкой (это Consistency)
- не пишет audit вместо Audit Log (но требует audit)
- не хранит “длинную историю” (это Versioning & Memory)

---

## 1) CANON CRITERIA (STRICT)

### 1.1 What "canon" means here
Canon = состояние, где:
- existence определено каноническим индексом/реестром
- navigation ведёт raw-links
- LOCK: FIXED соблюдается (нет правок вне pipeline)
- UID уникален и стабилен
- dependencies прозрачны и записаны

### 1.2 Canon-impacting change (definition)
Change is canon-impacting if any:
- touches a file with LOCK: FIXED
- changes any canonical index/registry/law
- renames/moves/deletes a canonical file
- changes raw-link navigation
- changes mini-contract of any engine
- changes UID rules or UID values of existing canonical entities

Canon-impacting change requires DECISION_RECORD.

---

## 2) MINI-CONTRACT (MANDATORY)

CONSUMES:
- CHANGE_PROPOSAL
- CHANGE_NOTE
- AFFECTED_FILES_LIST
- CHANGE_PACKAGE_RECORD
- SCOPE_IMPACT_REPORT           # mandatory if structural/rename/move/index touched
- RISK_SAFETY_REPORT            # mandatory if cross-layer or high risk or FIXED touched
- CONSISTENCY_REPORT            # mandatory for final closure decision OR required as condition
- DEPENDENCY_RECORDS            # mandatory if DEPENDS_ON changed

PRODUCES:
- DECISION_RECORD
- CONDITIONS_LIST
- WAIVER_RECORD?                # optional, but strict rules apply
- REQUIRED_ACTIONS_LIST

DEPENDS_ON:
- 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG
- 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG
- 00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG
- 00_GOVERNANCE_ENGINES/08__SCOPE_IMPACT_ENG
- 00_GOVERNANCE_ENGINES/09__RISK_SAFETY_ENG

OUTPUT_TARGET:
- 99_LOGS/LOG__CHANGES.md

---

## 3) DECISION STATES (STRICT)

Allowed DECISION:
- ACCEPT
- REJECT
- ACCEPT_WITH_CONDITIONS

Rule:
- ACCEPT_WITH_CONDITIONS is preferred when change is correct but requires follow-ups.
- REJECT when any S0 blocker exists (see section 5).

---

## 4) REQUIRED INPUTS BY CHANGE TYPE

### 4.1 PATCH (non-structural, low risk)
Mandatory:
- CHANGE_NOTE
- AFFECTED_FILES_LIST
- CHANGE_PACKAGE_RECORD
- (Consistency may be waived only if NOT canon-impacting. If canon-impacting, consistency required at close.)

### 4.2 MINOR (additive)
Mandatory:
- CHANGE_NOTE
- AFFECTED_FILES_LIST
- CHANGE_PACKAGE_RECORD
- CONSISTENCY_REPORT at close (or condition)

### 4.3 MAJOR (breaking / structural / index touched / rename-move-delete)
Mandatory:
- SCOPE_IMPACT_REPORT
- RISK_SAFETY_REPORT
- MIGRATION_MAP (inside scope impact)
- DEPENDENCY_RECORDS (if deps changed)
- CONSISTENCY_REPORT required (must be PASS for final closure)

---

## 5) ABSOLUTE BLOCKERS (S0) — AUTO-REJECT

If any is true -> DECISION must be REJECT (no waivers except emergency protocol with expiry):

S0-1 Broken raw-link in canonical entrypoint/index
S0-2 Canonical index references missing/renamed file without migration mapping
S0-3 LOCK: FIXED was changed outside change package pipeline
S0-4 UID duplication/corruption for canonical entities
S0-5 Dependency drift: DEPENDS_ON changed without dependency records
S0-6 Deletion of canonical entity without deprecation + replacement route
S0-7 Authority conflict: two sources claim existence truth (double-SoT)

---

## 6) CONDITIONS MODEL (FOR ACCEPT_WITH_CONDITIONS)

Conditions are explicit tasks that must be satisfied.
Each condition has:
- CID
- TYPE
- WHAT
- WHY
- REQUIRED_ARTIFACT
- DEADLINE (optional)
- OWNER (optional)

Allowed CONDITION_TYPE:
- FIX_RAW_LINKS
- ADD_MISSING_UIDS
- ADD_DEPENDENCY_RECORDS
- PROVIDE_MIGRATION_MAP
- RUN_CONSISTENCY_POST_VERIFY
- BUMP_VERSIONS_AND_MEMORY
- DEPRECATE_WITH_REPLACEMENT
- RESOLVE_AUTHORITY_CONFLICT
- OTHER (must include strict WHY)

Rule:
- Conditions must be checkable (not vague).

---

## 7) WAIVER MODEL (STRICT, DANGEROUS)

Waiver = временное разрешение пропустить правило.

Waivers are allowed ONLY for:
- Emergency (D4) situations where system is blocked and must be restored.

Waiver must include:
- EXPIRY_DATE
- MIGRATION_PLAN
- RISK_ACCEPTANCE
- DECISION_APPROVER (role)
- SCOPE narrow (exact paths)

If any waiver missing required fields -> invalid (treat as no waiver).

---

## 8) OUTPUT FORMS (CANON)

### 8.1 DECISION_RECORD (REQUIRED)
DECISION_RECORD:
- DECISION_ID: UE.DEC.YYYY-MM-DD.NNN
- DATE: YYYY-MM-DD
- TIME: HH:MM (or NA)
- AUTHOR: <string>
- CHANGE_ID: <from CHANGE_NOTE>
- CHANGE_PACKAGE_ID: <from package>
- DECISION: ACCEPT|REJECT|ACCEPT_WITH_CONDITIONS
- CANON_IMPACT: YES|NO
- CHANGE_TYPE: PATCH|MINOR|MAJOR|...
- SCOPE: <short>
- AFFECTED: (must match AFFECTED_FILES_LIST)
- BLOCKERS: [] | list
- CONDITIONS: [] | list
- REQUIRED_ARTIFACTS: [] | list
- WAIVER_REF: none | UE.WVR...
- AUDIT_REQUIRED: YES
- CLOSE_CRITERIA:
  - CONSISTENCY: PASS required? YES/NO
  - VERSIONING_MEMORY: required? YES/NO
- NOTES: <optional>

### 8.2 WAIVER_RECORD (OPTIONAL, emergency only)
WAIVER_RECORD:
- WAIVER_ID: UE.WVR.YYYY-MM-DD.NNN
- DATE:
- CHANGE_ID:
- EXPIRY_DATE:
- SCOPE:
- RULES_WAIVED: list
- WHY:
- MIGRATION_PLAN:
- RISK_ACCEPTANCE:
- APPROVER:
- NOTES:

---

## 9) HARD GATES (ENFORCEMENT)

- G1 CHANGE_ID coherence:
  CHANGE_NOTE.CHANGE_ID == DECISION_RECORD.CHANGE_ID == CHANGE_PACKAGE_RECORD.CHANGE_ID

- G2 AFFECTED coherence:
  decision AFFECTED must match the package list (same paths)

- G3 If canon-impacting -> AUDIT_REQUIRED = YES (no exceptions)

- G4 Structural/rename/move/index touched -> scope impact required

- G5 High risk / cross-layer / fixed touched -> risk safety required

- G6 If decision ACCEPT or ACCEPT_WITH_CONDITIONS for canon-impacting change:
  close criteria must include CONSISTENCY PASS

- G7 If any S0 blocker detected -> REJECT (unless emergency waiver with expiry)

---

## 10) INTEGRATION WITH PIPELINE

### With Change Control
- Canon Authority must be called at stage S2 (DECISION).
- Close is forbidden if decision requires consistency and report is missing.

### With Audit Log
- For canon-impacting change, Audit Log must record APPLY and CLOSE events referencing DECISION_ID and CHANGE_ID.

### With Consistency
- Consistency report is mandatory for close.
- Authority can accept with condition “Run consistency post-verify”.

### With Versioning & Memory
- Authority can require version bumps + memory package as close criteria.

---

## 11) EXAMPLES

### 11.1 ACCEPT (simple patch)
- Touch: one engine text clarification, no structure changes, still canon-impacting (LOCK: FIXED)
- Required: package + decision + later close with consistency pass.

Decision:
- DECISION: ACCEPT
- CONDITIONS: ["RUN_CONSISTENCY_POST_VERIFY", "BUMP_VERSIONS_AND_MEMORY"]

### 11.2 ACCEPT_WITH_CONDITIONS (rename)
- Rename engine file
- Must include migration map + update raw-links in index
Decision:
- DECISION: ACCEPT_WITH_CONDITIONS
- CONDITIONS: PROVIDE_MIGRATION_MAP, FIX_RAW_LINKS, RUN_CONSISTENCY_POST_VERIFY

### 11.3 REJECT (broken entrypoint raw-link)
- Index raw-link points to deleted file
Decision:
- DECISION: REJECT
- BLOCKERS: [S0-1, S0-2]

### 11.4 Emergency waiver (temporary)
- System is blocked due to a missing UID in 1 file preventing tooling
Decision:
- ACCEPT_WITH_CONDITIONS + WAIVER with expiry date + plan to backfill UID

---

## 12) EDGE CASES

- Multiple packages share same change id -> forbidden (must be unique)
- Partial rollback -> should create a new change id (recommended) and decision record
- Deleting non-canon files -> CANON_IMPACT: NO (decision optional, but audit recommended if touches logs/registries)

---

## 13) REFERENCES (RAW ONLY)

Audit Log:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md

Change Control:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md

Consistency:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md

Scope Impact:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/08__SCOPE_IMPACT_ENG.md

Risk Safety:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/09__RISK_SAFETY_ENG.md

Logs:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/99_LOGS/LOG__CHANGES.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/99_LOGS/LOG__AUDIT.md

--- END.
