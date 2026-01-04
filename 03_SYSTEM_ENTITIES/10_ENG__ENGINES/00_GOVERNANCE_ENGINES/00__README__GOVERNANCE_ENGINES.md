# Governance Engines Realm (README)
FILE: 00__README__GOVERNANCE_ENGINES.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
INDEX_REF: 02__INDEX_ALL_ENGINES.md
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0
ROLE: Realm file (family law) — boundaries, terminology, usage order, integration rules for Governance engines

LOCK: FIXED

---

## 0) REALM PURPOSE (LAW)
Семейство **00_GOVERNANCE_ENGINES** — это “надстройка закона” над всем Universe Engine.

Здесь живут движки, которые:
- определяют **кто имеет право** менять канон
- задают **иерархию правил** и приоритеты
- фиксируют **аудит**, версии и память изменений
- обеспечивают **контроль изменений**, проверку консистентности и зависимости

### ABSOLUTE RULE
> Если правило/реестр/процесс влияет на канон — он обязан проходить через governance слой.

---

## 1) WHAT THIS REALM COVERS
Governance покрывает 5 функций:

1) **Authority** — кто принимает решения и что является каноном  
2) **Process** — как вносятся изменения (pipeline)  
3) **Integrity** — как ловятся ошибки и несостыковки  
4) **Traceability** — как фиксируются изменения и версии  
5) **Dependencies** — как управляются зависимости и циклы  

---

## 2) FAMILY CONTENT (CANON LIST)
Эта семья обязана содержать только движки из INDEX.

Canonical engines:
- 01__AUDIT_LOG_ENG.md
- 02__CANON_AUTHORITY_ENG.md
- 03__RULE_HIERARCHY_ENG.md
- 04__CHANGE_CONTROL_ENG.md
- 05__CONSISTENCY_ENG.md
- 06__DEPENDENCY_REGISTRY_ENG.md
- 07__DECISION_APPROVAL_ENG.md
- 08__SCOPE_IMPACT_ENG.md
- 09__RISK_SAFETY_ENG.md
- 10__VERSIONING_MEMORY_ENG.md

### EXISTENCE RULE
> Любой governance-движок, которого нет в INDEX, считается **non-canon**.

---

## 3) HOW TO USE (ORDER OF WORK)
### 3.1 Reader path (default)
Если ты “читатель” и хочешь быстро понять как всё устроено:

1) **03 Rule Hierarchy** — чтобы понять приоритеты закона  
2) **02 Canon Authority** — кто утверждает канон  
3) **04 Change Control** — как легально менять систему  
4) **01 Audit Log** — где фиксируется каждое изменение  
5) **10 Versioning & Memory** — как устроены версии/память  
6) **06 Dependency Registry** — где лежат зависимости  
7) **05 Consistency** — как проверяем, что всё сходится  
8) **07 Decision Approval** — механизм утверждения решений  
9) **08 Scope Impact** — оценка последствий изменений  
10) **09 Risk Safety** — риски и безопасность канона  

### 3.2 Builder path (when you change canon)
Если ты хочешь добавить/изменить движок/правило:

- сначала **Rule Hierarchy → Canon Authority → Change Control**
- только потом любые изменения файлов
- затем **Audit → Versioning → Dependency Registry → Consistency**

---

## 4) KEY TERMS (TERMINOLOGY)
- **Canon** — то, что официально принято системой как истина.
- **Non-canon / ignored** — файл/правило существует, но **не зарегистрировано** в INDEX или нарушает pipeline.
- **Lock**:
  - `LOCK: FIXED` — закреплено, менять только через Change Control.
  - `LOCK: OPEN` — в разработке, но всё равно под governance.
- **S1 Critical** — критическое нарушение канона (блокирует принятие изменений).

---

## 5) BOUNDARIES (ANTI-DUPLICATION)
### 5.1 What governance must NOT do
Governance не пишет доменную историю, персонажей, мир, стиль, формат, производство и т.п.

Он:
- не генерирует контент
- не решает “что в сюжете”
- не описывает “как выглядит мир”
- не заменяет production-layer процессы

Он только:
- задаёт закон, процесс, контроль, зависимости, версии.

### 5.2 Governance vs Meta Evolution
- **Governance** — закон и контроль (что считается правильным)
- **Meta Evolution** — улучшение системы (как стать лучше)

---

## 6) HARD RULES (MANDATORY)
### 6.1 Single-status rule
В каждом файле семьи:
- один статус в шапке
- в конце файла второй `STATUS:` запрещён

### 6.2 Mini-contract rule
Каждый движок обязан иметь блок:
CONSUMES / PRODUCES / DEPENDS_ON / OUTPUT_TARGET

Иначе движок **incomplete** и не может считаться каноном.

### 6.3 Link rule
Все ссылки на движки и README должны быть:
- либо через INDEX (raw link),
- либо внутренние канонические пути.

### 6.4 Dependency sync
`DEPENDS_ON` в движках обязан совпадать с `06__DEPENDENCY_REGISTRY_ENG.md`.

---

## 7) GOVERNANCE PIPELINE (CANON GATE)
Любое изменение канона обязано проходить:

1) `04__CHANGE_CONTROL_ENG.md`
2) `01__AUDIT_LOG_ENG.md`
3) `10__VERSIONING_MEMORY_ENG.md`
4) `06__DEPENDENCY_REGISTRY_ENG.md` (если затронуты зависимости)
5) `05__CONSISTENCY_ENG.md`

Если pipeline пропущен — изменение считается **non-canon**.

---

## 8) FAMILY OUTPUT TARGETS
Governance-результаты кладутся в:
- audit logs (a.k.a. `01__AUDIT_LOG_ENG.md` outputs)
- version history / memory (`10__VERSIONING_MEMORY_ENG.md`)
- dependency registry (`06__DEPENDENCY_REGISTRY_ENG.md`)
- change control records (`04__CHANGE_CONTROL_ENG.md`)

---

## 9) QUICK LINKS
- Family in INDEX:
  `03_SYSTEM_ENTITIES/10_ENG__ENGINES/02__INDEX_ALL_ENGINES.md`
- Dependency registry:
  `03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG.md`

---

## FINAL REALM LAW (LOCK)
> 00_GOVERNANCE_ENGINES — это закон и контроль канона.  
> Любое изменение канона без governance считается non-canon.

OWNER: Universe Engine
LOCK: FIXED
