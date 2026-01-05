# ENG GOVERNANCE ENGINES — REALM (FAMILY README)
FILE: 00__README__GOVERNANCE_ENGINES.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
CLASS: GOVERNANCE (L1)
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
ROLE: Realm rules + boundaries + interfaces for Governance engine family

---

## 0) PURPOSE (REALM LAW)

Эта FAMILY определяет **правила управления каноном** и **порядок изменений** всей системы Universe Engine.

Governance отвечает за:
- кто имеет право менять канон, и как фиксируется “истина”
- как оформляются изменения (pipeline)
- как проверяется целостность (consistency)
- как описываются зависимости и XREF
- как хранится память версий, решений и аудита

---

## 1) SCOPE (WHAT THIS FAMILY OWNS)

### THIS FAMILY OWNS
- Canon authority & decision rights
- Change control pipeline
- Audit logging / traceability
- Consistency checking rules
- Dependency registry (официальный реестр зависимостей)
- Risk & safety policy (граничные условия)
- Scope impact analysis
- Versioning & memory policy

### THIS FAMILY DOES NOT OWN
- Domain-содержание (нарратив, персонажи, мир)
- Production-процессы (монтаж, визуал и т.п.)
- Валидаторы/QA/контроллеры (это отдельные entity groups)
- Содержательные “движки” кроме governance-логики

---

## 2) CANON PIPELINE (MANDATORY)

Любая правка в любой другой FAMILY считается канонической только если:
1) зафиксирована в `01__AUDIT_LOG_ENG.md`
2) прошла `04__CHANGE_CONTROL_ENG.md`
3) подтверждена `02__CANON_AUTHORITY_ENG.md`
4) проверена `05__CONSISTENCY_ENG.md` (если применимо)
5) обновила `10__VERSIONING_MEMORY_ENG.md` (если меняет правила/структуру)

---

## 3) FAMILY ORDER (CANON)

Файлы внутри семейства идут строго так:

01 — Audit Log Engine  
02 — Canon Authority Engine  
03 — Rule Hierarchy Engine  
04 — Change Control Engine  
05 — Consistency Engine  
06 — Dependency Registry Engine  
07 — Decision Approval Engine  
08 — Scope Impact Engine  
09 — Risk Safety Engine  
10 — Versioning & Memory Engine  

---

## 4) INTERFACES (INPUT/OUTPUT TYPES)

### GOVERNANCE INPUT TYPES (typical)
- CHANGE_REQUEST
- PROPOSAL
- DECISION_RECORD
- DEPENDENCY_DECLARATION
- CANON_DIFF
- RISK_NOTE
- SCOPE_IMPACT_NOTE

### GOVERNANCE OUTPUT TYPES (typical)
- APPROVED_CHANGE
- REJECTED_CHANGE
- AUDIT_ENTRY
- VERSION_TAG
- CONSISTENCY_REPORT
- DEPENDENCY_GRAPH_ENTRY
- CANON_RULE_UPDATE

---

## 5) BOUNDARIES (ANTI-DUPLICATION)

- Governance **не пишет контент**, он **регулирует правила контента**.
- Governance **не заменяет QA**, он задаёт стандарт и требования к проверкам.
- Governance **не заменяет validators**, он указывает, что и где должно быть отражено.

---

## 6) REQUIRED LINKS

- INDEX (global): `../02__INDEX_ALL_ENGINES.md`
- Dependency owner: `06__DEPENDENCY_REGISTRY_ENG.md`
- Change pipeline: `04__CHANGE_CONTROL_ENG.md`
- Canon authority: `02__CANON_AUTHORITY_ENG.md`

---

## 7) RULES FOR AUTHORS (MANDATORY)

- Любой governance engine **обязан** иметь mini-contract.
- Любая правка governance правил **обязана** идти через audit + versioning memory.
- В конце файла допускается только `LOCK`, без повторного `STATUS`.

---

OWNER: Universe Engine
LOCK: OPEN
