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
VERSION: 1.0.1
UID: UE.ENG.GOV.CANON_AUTHORITY.001
OWNER: SYSTEM
ROLE: Final decision gate for canon-impacting changes (ACCEPT/REJECT/ACCEPT_WITH_CONDITIONS)

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: HOTFIX
- SUMMARY: "UID assigned + header normalized + RAW-only references."
- REASON: "Comply with marking + raw navigation."
- IMPACT: "Authority decisions become link-safe and enforceable."
- CHANGE_ID: UE.CHG.2026-01-08.005

---

## 0) PURPOSE (LAW)
Ворота канона: решение ACCEPT/REJECT/ACCEPT_WITH_CONDITIONS для canon-impacting change.

Non-goals:
- не планирует пайплайн (Change Control)
- не выполняет глубокую проверку (Consistency/VAL)
- не пишет audit вместо Audit Log (требует его)

---

## 1) BOUNDARY (ANTI-DUP)
OWNED HERE:
- final decision for canon-impact changes
- standard decision record (semantics)

NOT OWNED:
- audit recording
- dependency registry

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- CHANGE_PROPOSAL
- CHANGE_NOTE
- AFFECTED_FILES_LIST
- SCOPE_IMPACT_REPORT?      # optional but may become condition
- RISK_SAFETY_REPORT?       # optional but may become condition
- CONSISTENCY_REPORT?       # optional but may become condition

PRODUCES:
- DECISION_RECORD
- CONDITIONS_LIST?          # optional
- AUDIT_RECORD_REF          # required for completion

DEPENDS_ON:
- 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG

OUTPUT_TARGET:
- 99_LOGS/LOG__CHANGES.md (decision record storage)
- 99_LOGS/LOG__AUDIT.md (audit ref)

---

## 3) DECISION STATES (STRICT)
- ACCEPT
- REJECT
- ACCEPT_WITH_CONDITIONS

---

## 4) HARD GATES
- G1 AFFECTED list exists and concrete
- G2 Canon impact declared
- G3 Summary/Reason/Impact present
- G4 Rename/move includes OLD→NEW mapping
- G5 Fixed-index touch requires impact/risk/rollback as conditions
- G6 Decision is incomplete without AUDIT_RECORD_REF

---

## 5) DECISION_RECORD (REQUIRED FORMAT)
- DECISION_ID: UE.DEC.YYYY-MM-DD.NNN
- DATE:
- AUTHOR:
- DECISION: ACCEPT|REJECT|ACCEPT_WITH_CONDITIONS
- CANON_IMPACT: YES|NO
- CHANGE_TYPE:
- SCOPE:
- AFFECTED: (list PATH + optional UID)
- SUMMARY:
- REASON:
- IMPACT:
- CONDITIONS: none|list
- REQUIRED_CHECKS: none|list
- AUDIT_RECORD_REF:
- NOTES:

---

## 6) REL / XREF (RAW ONLY)
REL: REQUIRES | TARGET_UID: UE.ENG.GOV.AUDIT_LOG.001 | RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md | WHY: every decision must be audited
XREF_UID: UE.ENG.GOV.CHANGE_CONTROL.001 | RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md | WHY: decisions apply to change packages

--- END.
