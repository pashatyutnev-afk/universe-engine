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
VERSION: 1.0.1
UID: UE.ENG.GOV.CHANGE_CONTROL.001
OWNER: SYSTEM
ROLE: Canon change workflow controller (package + stages + close rules)

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: HOTFIX
- SUMMARY: "UID assigned + header normalized + RAW-only references."
- REASON: "Comply with marking + raw navigation."
- IMPACT: "Canon changes become deterministic and auditable."
- CHANGE_ID: UE.CHG.2026-01-08.007

---

## 0) PURPOSE (LAW)
Единственный допустимый процесс изменения канона: propose → checks → decision → apply → audit → verify → close.

---

## 1) MINI-CONTRACT
CONSUMES:
- CHANGE_PROPOSAL
- CHANGE_NOTE
- AFFECTED_FILES_LIST
- DIFF_SUMMARY?
- SCOPE_IMPACT_REPORT?
- RISK_SAFETY_REPORT?
- CONSISTENCY_REPORT?
- DEPENDENCY_RECORDS?   # if deps changed

PRODUCES:
- CHANGE_PACKAGE_RECORD
- STAGE_CHECKLIST
- ROLLBACK_PLAN?        # conditional
- CLOSEOUT_REPORT
- AUDIT_RECORD_REF

DEPENDS_ON:
- 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG
- 00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG

OUTPUT_TARGET:
- 99_LOGS/LOG__CHANGES.md
- 99_LOGS/LOG__AUDIT.md

---

## 2) STAGES (MANDATORY)
S0 PROPOSE
S1 PRE-CHECK
S2 DECISION
S3 APPLY
S4 AUDIT
S5 POST-VERIFY
S6 CLOSE + MEMORY

Hard rule:
- No CLOSE without DECISION + AUDIT + POST-VERIFY PASS.

---

## 3) HARD GATES
- G1 AFFECTED list required
- G2 Canon-impact requires decision
- G3 Canon-impact requires audit
- G4 FIXED touched requires rollback plan
- G5 dependency change requires dependency records
- G6 post-verify required to close

---

## 4) OUTPUT FORMAT — CHANGE_PACKAGE_RECORD (REQUIRED)
- CHANGE_ID: UE.CHANGE.YYYY-MM-DD.NNN
- DATE/AUTHOR/TYPE/CANON_IMPACT/SCOPE
- AFFECTED list
- SUMMARY/REASON/IMPACT
- REQUIRED_ARTIFACTS list
- STAGES status
- DECISION_REF
- AUDIT_RECORD_REF
- POST_VERIFY_RESULT
- NOTES

---

## 5) REL / XREF (RAW ONLY)
XREF_UID: UE.ENG.GOV.AUDIT_LOG.001 | RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md | WHY: audit mandatory
XREF_UID: UE.ENG.GOV.CANON_AUTHORITY.001 | RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md | WHY: decision mandatory
XREF_UID: UE.ENG.GOV.CONSISTENCY.001 | RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md | WHY: post-verify gate

--- END.
