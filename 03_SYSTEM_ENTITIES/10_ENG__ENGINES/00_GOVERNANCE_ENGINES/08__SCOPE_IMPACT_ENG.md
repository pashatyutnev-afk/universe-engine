# SCOPE IMPACT ENGINE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/08__SCOPE_IMPACT_ENG.md

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
UID: UE.ENG.GOV.SCOPE_IMPACT.001
OWNER: SYSTEM
ROLE: Computes change blast-radius (required secondary updates across indexes/registries/deps/raw-links)
CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: HOTFIX
- SUMMARY: "UID assigned + header normalized + RAW-only references."
- REASON: "Comply with marking + raw navigation."
- IMPACT: "Structural changes become predictable and safe to plan."
- CHANGE_ID: UE.CHG.2026-01-08.011

---

## 0) PURPOSE (LAW)
Если мы меняем X — что обязаны обновить, чтобы система осталась живой.

---

## 1) MINI-CONTRACT
CONSUMES:
- CHANGE_PROPOSAL
- CHANGE_NOTE
- AFFECTED_FILES_LIST
- INDEX_ENTRYPOINTS?
- RAW_LINKS_LIST?

PRODUCES:
- SCOPE_IMPACT_REPORT
- REQUIRED_UPDATES_LIST
- MIGRATION_MAP?       # for rename/move
- ROLLBACK_HINTS?

DEPENDS_ON:
- 00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG
- 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG

OUTPUT_TARGET:
- 99_LOGS/LOG__CHANGES.md

---

## 2) HARD GATES
- G1 concrete affected list
- G2 rename/move must have OLD→NEW migration map
- G3 index touched implies required updates non-empty
- G4 dependency touched implies registry updates required

---

## 3) OUTPUT FORMAT — SCOPE_IMPACT_REPORT
- REPORT_ID: UE.SCOPE.YYYY-MM-DD.NNN
- CHANGE_TYPE / IMPACT_CLASS
- PRIMARY_AFFECTED
- SECONDARY_AFFECTED (predicted)
- REQUIRED_UPDATES (ordered with severity)
- MIGRATION_MAP
- RAW_LINK_IMPACT
- ROLLBACK_HINTS

---

## 4) REL / XREF (RAW ONLY)
XREF_UID: UE.ENG.GOV.CHANGE_CONTROL.001 | RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md | WHY: used in change package
XREF_UID: UE.ENG.GOV.DEPENDENCY_REGISTRY.001 | RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG.md | WHY: deps are part of blast-radius

--- END.
