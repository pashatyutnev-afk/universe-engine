# DEPENDENCY REGISTRY ENGINE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG.md

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
UID: UE.ENG.GOV.DEPENDENCY_REGISTRY.001
OWNER: SYSTEM
ROLE: Single registry of engine dependencies (HARD/SOFT) with strict record format + enforcement
CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: HOTFIX
- SUMMARY: "UID assigned + header normalized + fixed single storage policy + RAW-only references."
- REASON: "Avoid ghost registries and comply with existence rule."
- IMPACT: "Dependencies become deterministic and checkable."
- CHANGE_ID: UE.CHG.2026-01-08.009

---

## 0) PURPOSE (LAW)
Единый реестр зависимостей. Нет зависимости без записи.

---

## 1) MINI-CONTRACT
CONSUMES:
- DEPENDS_ON_DECLARATIONS
- PROPOSED_DEPENDENCY_RECORDS?

PRODUCES:
- DEPENDENCY_REGISTRY
- DEPENDENCY_RECORD
- CYCLE_REPORT?

DEPENDS_ON:
- 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG
- 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG

OUTPUT_TARGET (SINGLE STORAGE POLICY):
- 99_LOGS/LOG__CHANGES.md   # dependency records live here (canonical)
- (Audit refs go to 99_LOGS/LOG__AUDIT.md)

---

## 2) TYPES (STRICT)
TYPE: HARD | SOFT

Rule:
- HARD on deprecated allowed only with explicit WHY + migration plan (in changes record).

---

## 3) CANON RECORD FORMAT (MANDATORY)
Single-line canonical:
`<FROM>  ->  <TO>  | TYPE:<HARD|SOFT> | WHY:<short reason>`

FROM/TO format:
`<FAMILY>/<NN__ENGINE_NAME_ENG>`

---

## 4) HARD RULES
- R1 engine DEPENDS_ON implies registry record exists
- R2 registry cannot reference engines not in ENG index
- R3 duplicates forbidden
- R4 cycles allowed only with explicit exception + decision + break mechanism

---

## 5) REL / XREF (RAW ONLY)
XREF_UID: UE.ENG.GOV.CONSISTENCY.001 | RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md | WHY: checks alignment
XREF_UID: UE.ENG.GOV.CHANGE_CONTROL.001 | RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md | WHY: dependency updates must be packaged

--- END.
