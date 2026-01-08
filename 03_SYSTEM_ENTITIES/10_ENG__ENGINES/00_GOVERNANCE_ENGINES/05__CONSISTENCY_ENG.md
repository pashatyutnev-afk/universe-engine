# CONSISTENCY ENGINE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md

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
UID: UE.ENG.GOV.CONSISTENCY.001
OWNER: SYSTEM
ROLE: Canon integrity inspector (headers + naming + indexes + raw-links + deps + boundaries) producing CONSISTENCY_REPORT
CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: HOTFIX
- SUMMARY: "UID assigned + header normalized + RAW-only references."
- REASON: "Comply with marking + raw navigation."
- IMPACT: "Consistency report becomes canonical gate for change close."
- CHANGE_ID: UE.CHG.2026-01-08.008

---

## 0) PURPOSE (LAW)
Диагностирует нарушения стандартов и конфликты: структура, индексы/реестры, raw-links, зависимости, границы семейств.

---

## 1) MINI-CONTRACT
CONSUMES:
- TARGET_SCOPE
- CHANGE_PACKAGE_RECORD?    # for change gate mode
- RULESET_REFERENCES?

PRODUCES:
- CONSISTENCY_REPORT
- VIOLATION_LIST
- FIX_PLAN

DEPENDS_ON:
- 00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG
- 00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG
- 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG

OUTPUT_TARGET:
- 99_LOGS/LOG__CHANGES.md (refs)

---

## 2) CHECK DOMAINS (D0..D5)
D0 Header compliance + single truth
D1 Naming/Numbering integrity
D2 Index/Registry coherence (existence rule)
D3 RAW link integrity
D4 Dependency transparency (DEPENDS_ON + registry record)
D5 Anti-dup boundaries (semantic risk)

Severity:
- S0 blockers break navigation/existence/entrypoints
- S1 high integrity breaks (missing mini-contract / broken raw in canon index)
- S2 semantic overlaps / drift
- S3 cosmetic

---

## 3) HARD ENFORCEMENT RULES
- R1 broken raw-link in canonical entrypoint/index → S0
- R2 index references missing file → S0
- R3 engine missing mini-contract → S1
- R4 DEPENDS_ON missing → S1
- R5 duplicate STATUS/LOCK/VERSION truth → S1
- R6 dependency change without registry record → S0/S1 (policy)

---

## 4) OUTPUT FORMAT — CONSISTENCY_REPORT
- REPORT_ID: UE.CNS.YYYY-MM-DD.NNN
- DATE/MODE/TARGET_SCOPE
- RESULT: PASS|WARN|FAIL
- COUNTS: S0..S3
- VIOLATIONS (normalized)
- FIX_PLAN (ordered)

---

## 5) REL / XREF (RAW ONLY)
XREF_UID: UE.ENG.GOV.RULE_HIERARCHY.001 | RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG.md | WHY: conflict resolution
XREF_UID: UE.ENG.GOV.DEPENDENCY_REGISTRY.001 | RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG.md | WHY: dependency alignment

--- END.
