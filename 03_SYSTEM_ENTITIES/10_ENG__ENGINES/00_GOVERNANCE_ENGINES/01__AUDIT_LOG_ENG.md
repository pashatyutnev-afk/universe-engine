# AUDIT LOG ENGINE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md

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
UID: UE.ENG.GOV.AUDIT_LOG.001
OWNER: SYSTEM
ROLE: Mandatory audit recorder for any canon-impacting change (append-only records)

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: HOTFIX
- SUMMARY: "UID assigned + header normalized + RAW-only references + removed footer duplicates."
- REASON: "Comply with marking standards and raw-only navigation."
- IMPACT: "Audit Log becomes fully canonical and link-safe."
- CHANGE_ID: UE.CHG.2026-01-08.004

---

## 0) PURPOSE (LAW)
Этот движок — “чёрный ящик” канона: любое изменение канона должно оставлять audit-след.

Non-goals (hard):
- не принимает решение approve/reject
- не применяет изменения
- не создаёт доменный/production контент

---

## 1) BOUNDARY (ANTI-DUPLICATION)
OWNED HERE:
- единый формат audit записи
- правило “no silent change”
- политика append-only (не переписываем старое)

NOT OWNED HERE:
- approve/reject (Canon Authority)
- change workflow (Change Control)

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- CHANGE_NOTE
- AFFECTED_FILES_LIST
- DECISION_RECORD?        # optional
- DIFF_SUMMARY?           # optional

PRODUCES:
- AUDIT_RECORD

DEPENDS_ON:
- []

OUTPUT_TARGET:
- 99_LOGS/LOG__AUDIT.md

---

## 3) OPERATION MODEL
TRIGGER:
- любой canon-impacting change (index/rules/templates/engines/registries/rename/move/delete)

STEPS:
1) collect inputs
2) validate required fields
3) normalize affected items (PATH + optional UID)
4) append AUDIT_RECORD

---

## 4) HARD GATES
- G1 Required fields present (DATE/CHANGE_TYPE/AFFECTED/SUMMARY/REASON/IMPACT/AUTHOR)
- G2 AFFECTED is concrete (PATH + ITEM type per entry)
- G3 Canon-impact declared (IMPACT clearly states scope)
- G4 Linkability (PATH + optional UID exist)
- G5 Append-only intent (corrections are new records)

---

## 5) OUTPUT FORMAT — AUDIT_RECORD (REQUIRED)
- RECORD_ID: UE.AUDIT.YYYY-MM-DD.NNN
- DATE: YYYY-MM-DD (or ISO)
- CHANGE_TYPE: PATCH|MINOR|MAJOR|HARD-RESET|HOTFIX|DEPRECATION|RENAMING|MOVE|DELETE|ADD
- AUTHOR:
- SCOPE:
- AFFECTED:
  - ITEM: DOC|INDEX|TEMPLATE|ENGINE|REGISTRY|MAP
    PATH:
    UID: <optional>
- SUMMARY:
- REASON:
- IMPACT:
- DECISION_REF: <optional>
- NOTES: <optional>

---

## 6) EXAMPLES
GOOD:
- change: update governance template
- audit: contains exact PATH + summary/reason/impact

BAD:
- “почистил кучу файлов” без AFFECTED list → FAIL

---

## 7) EDGE CASES
- rename/move must include OLD_PATH→NEW_PATH in NOTES
- correction creates new record (never edit old)

---

## 8) REL / XREF (RAW ONLY)
XREF_UID: UE.ENG.GOV.CHANGE_CONTROL.001 | RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md | WHY: change workflow requires audit
XREF_UID: UE.ENG.GOV.CANON_AUTHORITY.001 | RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md | WHY: decisions should be auditable

--- END.
