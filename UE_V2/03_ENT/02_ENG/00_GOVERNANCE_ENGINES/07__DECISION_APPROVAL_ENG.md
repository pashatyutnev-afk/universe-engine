# DECISION APPROVAL ENGINE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/07__DECISION_APPROVAL_ENG.md

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
UID: UE.ENG.GOV.DECISION_APPROVAL.001
OWNER: SYSTEM
ROLE: Approval procedure layer. Defines decision classes, required approvers (roles), quorum/veto, escalation, emergency waivers, and produces canonical APPROVAL_RECORD used by Canon Authority and Change Control.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Decision approval procedure formalized: decision classes D0..D4, approver roles, quorum/veto rules, escalation, emergency waivers, record formats."
- REASON: "Stop implicit approvals and ambiguous ownership."
- IMPACT: "Canon changes gain deterministic approval semantics and auditable governance."
- CHANGE_ID: UE.CHG.2026-01-08.GOV.DAP.001

---

## 0) PURPOSE (LAW)

Decision Approval Engine отвечает за вопрос:
> “Кто имеет право это утвердить, сколько подтверждений нужно и есть ли вето?”

Он не решает “канон/не канон” сам по себе.
Он формирует **процедуру утверждения** и выпускает **APPROVAL_RECORD**,
который затем использует Canon Authority Engine для финального решения.

Non-goals:
- не заменяет Canon Authority (final gate)
- не заменяет Risk Safety (safety blockers)
- не заменяет Change Control (pipeline)
- не хранит audit trail (требует Audit Log)

---

## 1) MINI-CONTRACT (MANDATORY)

CONSUMES:
- CHANGE_PROPOSAL
- CHANGE_NOTE
- CHANGE_PACKAGE_RECORD
- AFFECTED_FILES_LIST
- RISK_SAFETY_REPORT?                 # required for D3/D4, optional for D2
- SCOPE_IMPACT_REPORT?                # required for D2+ when structural/rename/move
- CONFLICT_RESOLUTION_RECORD?          # if hierarchy conflict exists
- REQUESTED_DECISION_CLASS             # D0..D4

PRODUCES:
- APPROVAL_RECORD                      # canonical
- APPROVAL_STATUS                      # APPROVED|REJECTED|NEEDS_CHANGES
- WAIVER_RECORD?                       # emergency only
- ESCALATION_NOTE?                     # if unable to approve

DEPENDS_ON:
- 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG
- 00_GOVERNANCE_ENGINES/09__RISK_SAFETY_ENG
- 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG

OUTPUT_TARGET:
- 99_LOGS/LOG__CHANGES.md

---

## 2) DECISION CLASSES (STRICT SET)

### D0 — Editorial / Non-canon
- Examples: typos in non-canon files, formatting, comments
- Canon impact: NO
- Approval: optional (self-approve)

### D1 — Canon Patch (low risk)
- Examples: small clarification in canon file; raw-link fix without structure change
- Canon impact: YES
- Approval: single approver (role: GOVERNANCE_OWNER) or SYSTEM if owner is SYSTEM

### D2 — Canon Minor (structural within family/layer, non-breaking)
- Examples: add new engine to family, add new section/fields without breaking, reorder non-critical items
- Canon impact: YES
- Approval: quorum 2 (GOVERNANCE_OWNER + STANDARDS_OWNER) OR explicit single “SYSTEM” decision if system-owned and no risk blockers

### D3 — Canon Major (breaking / cross-layer / touches laws/indexes/fixed)
- Examples: change index laws, rename/move canon files, change UID rules, change templates used everywhere
- Canon impact: YES
- Approval: quorum 3 (GOVERNANCE_OWNER + STANDARDS_OWNER + CANON_AUTHORITY) and Risk Safety must be present

### D4 — Emergency (S0 breach fix)
- Examples: broken entrypoint, missing file referenced by index, corrupted UID collision
- Canon impact: YES
- Approval: emergency approval with expiry + waiver required
- Must be converted into D3 within deadline or reverted

---

## 3) APPROVER ROLES (CANON SET)

Allowed roles (strict):
- SYSTEM                            # used when canonical owner is SYSTEM
- GOVERNANCE_OWNER                  # owns governance process
- STANDARDS_OWNER                   # owns standards coherence
- CANON_AUTHORITY                   # final canon gate role
- RISK_OWNER                        # optional for high-risk acceptance
- PROJECT_OWNER                     # only for project-local rules (not for system laws)

Rule:
- A person/name can exist in real life; in docs we reference ROLE, not humans.

---

## 4) QUORUM / VETO RULES

### 4.1 Quorum
- D0: quorum 0..1 (optional)
- D1: quorum 1 (GOVERNANCE_OWNER or SYSTEM)
- D2: quorum 2 (GOVERNANCE_OWNER + STANDARDS_OWNER)
- D3: quorum 3 (GOVERNANCE_OWNER + STANDARDS_OWNER + CANON_AUTHORITY)
- D4: quorum 2 minimum (GOVERNANCE_OWNER + CANON_AUTHORITY) + waiver + expiry

### 4.2 Veto
Veto allowed only by:
- CANON_AUTHORITY for D2..D4
- RISK_OWNER for D3..D4 when RISK_SAFETY_REPORT says UNSAFE unless mitigated

Veto effect:
- immediate APPROVAL_STATUS = REJECTED
- must be recorded with WHY and blockers list

---

## 5) REQUIRED INPUTS BY CLASS (GATES)

### D1 requires:
- CHANGE_NOTE complete
- CHANGE_PACKAGE_RECORD exists
- AFFECTED_FILES_LIST concrete
- no S0 blockers in risk (if provided)
- (consistency may be condition at close)

### D2 requires:
- scope impact when structural/rename/move
- dependency records when DEPENDS_ON changed
- no unresolved hierarchy conflicts

### D3 requires:
- RISK_SAFETY_REPORT mandatory
- SCOPE_IMPACT_REPORT mandatory (if structural)
- conflict resolution record if any conflict existed
- rollback plan required in change package

### D4 requires:
- RISK_SAFETY_REPORT mandatory
- WAIVER_RECORD mandatory
- EXPIRY_DATE mandatory
- minimal scope (exact affected items only)

---

## 6) WAIVER (EMERGENCY) PROTOCOL (STRICT)

Waiver is allowed ONLY for D4.

WAIVER must include:
- EXPIRY_DATE (max 72h recommended)
- MIGRATION_PLAN (convert to D3 package or revert)
- RISK_ACCEPTANCE statement (what risk is accepted temporarily)
- SCOPE minimal (exact paths)
- APPROVERS list

No expiry -> invalid waiver.

---

## 7) OUTPUT FORMS (CANON)

### 7.1 APPROVAL_RECORD (required)
APPROVAL_RECORD:
- APPROVAL_ID: UE.APP.YYYY-MM-DD.NNN
- DATE: YYYY-MM-DD
- TIME: HH:MM (or NA)
- DECISION_CLASS: D0|D1|D2|D3|D4
- STATUS: APPROVED|REJECTED|NEEDS_CHANGES
- CHANGE_ID: <from CHANGE_NOTE>
- CHANGE_PACKAGE_ID: <from package>
- SCOPE: <short>
- AFFECTED: list (paths)
- REQUIRED_REPORTS:
  - SCOPE_IMPACT: YES|NO
  - RISK_SAFETY: YES|NO
  - CONSISTENCY: YES|NO
- APPROVERS:
  - ROLE: <role>
    ACTION: APPROVE|VETO|REQUEST_CHANGES
    WHY: <short>
- QUORUM_RULE: <string>
- VETO_PRESENT: YES|NO
- CONDITIONS: [] | list
- WAIVER_REF: none | UE.WVR...
- NOTES: <optional>

### 7.2 WAIVER_RECORD (only for D4)
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
- APPROVERS: list roles
- NOTES:

### 7.3 ESCALATION_NOTE (optional)
ESCALATION_NOTE:
- ESC_ID: UE.ESC.YYYY-MM-DD.NNN
- DATE:
- CHANGE_ID:
- WHY_ESCALATED:
- TO_ROLE:
- REQUIRED_ACTION:

---

## 8) HARD GATES (ENFORCEMENT)

- G1 Missing quorum -> STATUS cannot be APPROVED
- G2 Any veto -> STATUS must be REJECTED
- G3 D3/D4 cannot proceed without RISK_SAFETY_REPORT
- G4 D4 cannot proceed without WAIVER_RECORD + EXPIRY_DATE
- G5 Unresolved hierarchy conflict -> NEEDS_CHANGES or REJECTED
- G6 Canon-impacting approval requires audit to be produced by pipeline (enforced by Change Control)

---

## 9) GOOD / BAD EXAMPLES

### GOOD (D2 approved)
- Approvers: GOV + STANDARDS
- Conditions: run consistency post-verify, add dependency records
Status: APPROVED

### BAD (D3 approved without risk report)
- Missing RISK_SAFETY_REPORT -> invalid -> must be NEEDS_CHANGES

### BAD (veto ignored)
- If CANON_AUTHORITY veto present, status cannot be APPROVED.

### GOOD (D4 emergency)
- Waiver with expiry, minimal scope, migration plan to D3 within 72h
Status: APPROVED

---

## 10) INTEGRATION

- Change Control uses APPROVAL_RECORD as mandatory gate for D1+.
- Canon Authority consumes APPROVAL_RECORD but may still REJECT if S0 blockers exist.
- Audit Log records approval id in APPLY/CLOSE audit events.
- Versioning & Memory references approval and waiver in memory package.

---

## 11) REFERENCES (RAW ONLY)

Canon Authority:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md

Risk Safety:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/09__RISK_SAFETY_ENG.md

Change Control:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md

Audit Log:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md

Logs:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/99_LOGS/LOG__CHANGES.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/99_LOGS/LOG__AUDIT.md

--- END.
