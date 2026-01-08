# RULE HIERARCHY ENGINE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG.md

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
UID: UE.ENG.GOV.RULE_HIERARCHY.001
OWNER: SYSTEM
ROLE: Defines precedence rules (who wins conflicts) + publishes precedence map format

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: HOTFIX
- SUMMARY: "UID assigned + header normalized + RAW-only references."
- REASON: "Comply with marking + raw navigation."
- IMPACT: "Conflicts become resolvable deterministically."
- CHANGE_ID: UE.CHG.2026-01-08.006

---

## 0) PURPOSE (LAW)
Определяет порядок силы правил: кто побеждает при конфликте.

Non-goals:
- не approve/reject
- не делает проверки всего канона

---

## 1) MINI-CONTRACT
CONSUMES:
- LAYER_ENTRYPOINTS_LIST
- SYSTEM_LAW_PRIORITY
- STANDARDS_PRIORITY?
- EXCEPTION_NOTES?

PRODUCES:
- RULE_PRECEDENCE_MAP
- PRECEDENCE_RECORD

DEPENDS_ON:
- []

OUTPUT_TARGET:
- 99_LOGS/LOG__CHANGES.md (precedence records) or any canonical storage

---

## 2) PRECEDENCE MODEL (DEFAULT)
Levels (L0..L5):
- L0 SYSTEM LAW
- L1 STANDARDS
- L2 SYSTEM ENTITIES REGISTRIES
- L3 KNOWLEDGE BASE
- L4 PROJECTS
- L5 OUTPUT/ASSETS

Within-level order must be explicit or declared GAP.

Exceptions allowed only with WHY + SCOPE (and must be auditable when used).

---

## 3) HARD GATES
- G1 L0 must exist (no ambiguous top authority)
- G2 each level has entries or explicit EMPTY marker
- G3 internal order explicit or GAP declared
- G4 exceptions must have WHY + SCOPE
- G5 determinism: any conflict resolves or yields explicit GAP (never silent)

---

## 4) OUTPUT FORMAT — RULE_PRECEDENCE_MAP
- MAP_ID: UE.RULEMAP.YYYY-MM-DD.NNN
- DATE:
- AUTHOR:
- LEVELS: L0..L5 lists
- WITHIN_LEVEL_ORDER: per level or GAP
- EXCEPTIONS: list
- NOTES:

---

## 5) REL / XREF (RAW ONLY)
XREF_UID: UE.ENG.GOV.CONSISTENCY.001 | RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md | WHY: consistency uses precedence
XREF_UID: UE.ENG.GOV.CHANGE_CONTROL.001 | RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md | WHY: change planning references precedence

--- END.
