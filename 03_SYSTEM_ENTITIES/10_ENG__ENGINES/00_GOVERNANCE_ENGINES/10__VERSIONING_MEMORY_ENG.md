# VERSIONING & MEMORY ENGINE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/10__VERSIONING_MEMORY_ENG.md

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
UID: UE.ENG.GOV.VERSIONING_MEMORY.001
OWNER: SYSTEM
ROLE: Enforces version bumps + in-file change notes + system memory records (audit + changes + optional release)
CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: HOTFIX
- SUMMARY: "UID assigned + header normalized + memory separation clarified + RAW-only references."
- REASON: "Comply with marking standards and avoid double truth."
- IMPACT: "Every canon change becomes traceable and reproducible."
- CHANGE_ID: UE.CHG.2026-01-08.013

---

## 0) PURPOSE (LAW)
Обязательное версионирование + фиксация change note + память (audit факт / changes смысл / release упаковка).

---

## 1) MINI-CONTRACT
CONSUMES:
- CHANGE_PROPOSAL
- CHANGE_SET
- CANON_DECISION
- RISK_SAFETY_REPORT
- AFFECTED_FILES_LIST

PRODUCES:
- VERSION_BUMP_PLAN
- CHANGE_NOTE_BLOCKS
- AUDIT_RECORD
- CHANGELOG_RECORD
- RELEASE_LOG_RECORD?     # optional
- MEMORY_PACKAGE_POINTER

DEPENDS_ON:
- 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG
- 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG

OUTPUT_TARGET:
- 99_LOGS/LOG__AUDIT.md
- 99_LOGS/LOG__CHANGES.md
- 08_DATABASES/DB__RELEASE_LOG.md (optional, if used)

---

## 2) VERSION LAW
MAJOR.MINOR.PATCH
- PATCH: small non-breaking change (still canonical)
- MINOR: additive expansion without breaking
- MAJOR: breaking protocol/contract/structure change (or forced by authority)

Hard rule:
- any canon file edit → at least PATCH bump + in-file CHANGE_NOTE + memory entries.

---

## 3) MEMORY SEPARATION (STRICT)
- AUDIT = факт (что/когда/кем)
- CHANGES = смысл (почему/что меняется/эффект)
- RELEASE = упаковка набора (optional)

---

## 4) STANDARD CHANGE_NOTE TEMPLATE
CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR
- SUMMARY: "<...>"
- REASON: "<...>"
- IMPACT: "<...>"
- CHANGE_ID: UE.CHG.YYYY-MM-DD.NNN

---

## 5) REL / XREF (RAW ONLY)
XREF_UID: UE.ENG.GOV.AUDIT_LOG.001 | RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md | WHY: audit is part of memory
XREF_UID: UE.ENG.GOV.CHANGE_CONTROL.001 | RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md | WHY: versioning runs inside change workflow

--- END.
