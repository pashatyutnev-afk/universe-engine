# GOVERNANCE ENGINES — REALM README
FILE: 00__README__GOVERNANCE_ENGINES.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0
ROLE: Governance mechanics for ENG layer — authority, hierarchy, change, consistency, dependencies, risk, memory

---

## PURPOSE

Это семейство содержит **ENG-движки управления**, которые задают:
- что считается каноном и кто имеет право менять
- как разрешаются конфликты правил
- как фиксируются изменения (лог + версии)
- как обеспечивается согласованность и зависимости
- как оцениваются риски и влияние изменений

---

## BOUNDARY (ENG vs CTL/VAL/QA)

ENG (это семейство) = **механика / закон / контракт**.

- CTL = **процедуры исполнения** (пайплайн, шаги внедрения, гейты применения).
- VAL = **проверки** (валидаторы, тесты консистентности, автоматические проверки).
- QA  = **качество** (практики, метрики, критерии “достаточно хорошо”).

Если документ описывает “как команда делает шаги” — это CTL.
Если документ описывает “как проверять” — это VAL.
Если документ описывает “как повышать качество” — это QA.

---

## OUTPUTS (WHAT THIS FAMILY PRODUCES)

Типовые артефакты/выходы:
- записи аудита (Audit Events)
- решения об утверждении (Decision Records)
- приоритеты и источники канона (Authority Sources)
- правила разрешения конфликтов (Conflict Resolution Rules)
- политика изменений (Change Policy)
- инварианты целостности (Consistency Invariants)

---

## FAMILY CONTENT

01 — AUDIT_LOG_ENG  
02 — CANON_AUTHORITY_ENG  
03 — RULE_HIERARCHY_ENG  
04 — CHANGE_CONTROL_ENG  
05 — CONSISTENCY_ENG  
06 — DEPENDENCY_REGISTRY_ENG  
07 — DECISION_APPROVAL_ENG  
08 — SCOPE_IMPACT_ENG  
09 — RISK_SAFETY_ENG  
10 — VERSIONING_MEMORY_ENG  

---

## FAMILY RULE

Если новая сущность описывает “власть / конфликты / изменения / целостность / риски / память” —
она живёт в GOVERNANCE.

---
OWNER: Universe Engine
STATUS: FIXED
