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
VERSION: 1.0.1
UID: UE.ENG.GOV.DECISION_APPROVAL.001
OWNER: SYSTEM
ROLE: Decision procedure rules (who approves what, quorum/veto, emergency path) + Decision Record standard
CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: HOTFIX
- SUMMARY: "UID assigned + header normalized + RAW-only references."
- REASON: "Comply with marking + raw navigation."
- IMPACT: "Approvals become structured and auditable."
- CHANGE_ID: UE.CHG.2026-01-08.010

---

## 0) PURPOSE (LAW)
Определяет типы решений и правила апрува/кворума/вето/эскалации.

---

## 1) MINI-CONTRACT
CONSUMES:
- CHANGE_PACKAGE?
- PROPOSED_DECISION
- CONFLICT_REPORT?

PRODUCES:
- DECISION_RECORD
- APPROVAL_STATUS
- WAIVER_RECORD?      # optional
- ESCALATION_NOTE?    # optional

DEPENDS_ON:
- 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG
- 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG

OUTPUT_TARGET:
- 99_LOGS/LOG__CHANGES.md (decision records)
- 99_LOGS/LOG__AUDIT.md (audit refs)

---

## 2) DECISION TYPES (STRICT SET)
D0 Trivial / Editorial
D1 Canon Patch
D2 Canon Structural Change
D3 Law Change
D4 Emergency Decision (requires expiry + migration plan)

---

## 3) HARD RULES
- R1 D2+ requires Decision Record
- R2 no decision → no canon (unapproved state)
- R3 decision must be audited
- R4 emergency requires EXPIRY_DATE + MIGRATION_PLAN

---

## 4) REL / XREF (RAW ONLY)
XREF_UID: UE.ENG.GOV.CANON_AUTHORITY.001 | RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md | WHY: canon gate aligns with approval procedure
XREF_UID: UE.ENG.GOV.AUDIT_LOG.001 | RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md | WHY: decisions must be logged

--- END.
