# RISK SAFETY ENGINE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/09__RISK_SAFETY_ENG.md

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
UID: UE.ENG.GOV.RISK_SAFETY.001
OWNER: SYSTEM
ROLE: Safety gates + blockers + risk scoring for canon changes
CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: HOTFIX
- SUMMARY: "UID assigned + header normalized + RAW-only references."
- REASON: "Comply with marking + raw navigation."
- IMPACT: "Unsafe changes can be blocked deterministically."
- CHANGE_ID: UE.CHG.2026-01-08.012

---

## 0) PURPOSE (LAW)
Ставит safety-gates: что запрещено ломать, какие стоп-факторы (S0), какие условия mitigation обязательны.

---

## 1) MINI-CONTRACT
CONSUMES:
- CHANGE_PROPOSAL
- SCOPE_IMPACT_REPORT
- AFFECTED_FILES_LIST
- DEPENDENCY_DIFF?
- UID_DIFF?
- LOCK_STATUS_DIFF?

PRODUCES:
- RISK_SAFETY_REPORT
- SAFETY_GATE_DECISION (SAFE|CONDITIONAL|UNSAFE)
- BLOCKERS_LIST (S0)
- MITIGATION_PLAN
- RISK_SCORE_CARD

DEPENDS_ON:
- 00_GOVERNANCE_ENGINES/08__SCOPE_IMPACT_ENG
- 00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG
- 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG

OUTPUT_TARGET:
- 99_LOGS/LOG__CHANGES.md

---

## 2) S0 BLOCKERS (ABSOLUTE STOP)
- broken raw-links in canonical entrypoints/indexes
- FIXED touched outside pipeline
- UID corruption/duplication
- dependency drift without registry record
- rename/move/delete without migration map + required updates
- authority conflict (two sources of existence truth)

---

## 3) OUTPUT FORMAT — RISK_SAFETY_REPORT
- REPORT_ID: UE.RISK.YYYY-MM-DD.NNN
- DECISION: SAFE|CONDITIONAL|UNSAFE
- RISK_LEVEL: L0..L4
- BLOCKERS: list
- SCORE_CARD: D1..D6 + total
- MITIGATION_PLAN: M1..M6 checklist

---

## 4) REL / XREF (RAW ONLY)
XREF_UID: UE.ENG.GOV.SCOPE_IMPACT.001 | RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/08__SCOPE_IMPACT_ENG.md | WHY: blast radius inputs
XREF_UID: UE.ENG.GOV.CONSISTENCY.001 | RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md | WHY: post-verify mitigation

--- END.
