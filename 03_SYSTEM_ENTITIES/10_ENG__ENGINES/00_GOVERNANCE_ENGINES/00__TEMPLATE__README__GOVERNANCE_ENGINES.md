# GOVERNANCE ENGINES — REALM README (TEMPLATE)
FILE: 00__README__GOVERNANCE_ENGINES.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
DOC_TYPE: REALM_README
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: DRAFT
VERSION: 0.1
UID: <UE.ENG.GOV.REALM.README.###>
OWNER: <SYSTEM|ROLE|PERSON>
ROLE: Family scope law + boundaries + usage + enforcement philosophy
LOCK: OPEN

---

## 0) PURPOSE (LAW)

Это **REALM README** семейства `00_GOVERNANCE_ENGINES`.  
Он фиксирует:
- границы семейства (что “governance” делает и чего не делает)
- правила использования движков семейства
- обязательные “стики” с другими слоями (dependency/xref/changes)
- требования к шаблонам и к движкам этого семейства

> Канонический список движков и порядок — в `02__INDEX_ALL_ENGINES.md`.  
> Здесь список (если есть) может быть только **reference / non-canon**.

---

## 1) SCOPE (WHAT THIS FAMILY OWNS)

### 1.1 Governance область (владение)
- Канон и право: authority / hierarchy
- Изменения: change control
- Прозрачность: audit log
- Зависимости: dependency registry
- Решения: decision approval
- Риски: risk safety
- Консистентность: consistency checks
- Память версий: versioning & memory
- Влияние: scope impact

### 1.2 Governance НЕ делает (жёстко)
- Не создаёт доменный контент (сюжет/персонажи/мир)
- Не производит media-артефакты (визуал/видео/звук/музыку)
- Не подменяет Core/Domain/Production семейства

---

## 2) FAMILY BOUNDARIES (ANTI-DUP)

### 2.1 Where governance stops
- Governance определяет **правила и контроль**, но не “содержание мира”.

### 2.2 Typical overlaps to avoid
- “Quality checks” ≠ governance enforcement (если есть отдельные QA/VAL — не дублировать)
- “Project workflow” ≠ governance canon law (если есть PRJ слой — governance только задаёт рамки)

### 2.3 Conflict resolution rule
Если 2 движка претендуют на одну область:
1) объявить конфликт в change-control
2) назначить owner
3) прописать DEPENDS_ON и запись в dependency registry
4) при необходимости — deprecated одному из движков

---

## 3) HOW TO USE (WORKFLOW)

### 3.1 Typical governance pipeline (mandatory)
1) **Change Control** — фиксируем намерение и план
2) **Canon Authority** — кто имеет право менять канон
3) **Audit Log** — запись любой правки канона
4) **Consistency** — проверка инвариантов
5) **Dependency Registry** — фиксация/обновление зависимостей
6) **Decision Approval** — если требуется approve
7) **Versioning & Memory** — фиксируем новую версию/память

### 3.2 “No silent change” rule
Любая правка канона:
- должна иметь audit запись
- должна быть видима по ссылкам/xref
- не может быть “внесена просто файлом” без регистрации

---

## 4) TEMPLATES (MANDATORY)

- ENGINE TEMPLATE:
  - `00__TEMPLATE__ENGINE__GOVERNANCE_ENGINES.md`
- README TEMPLATE:
  - `00__TEMPLATE__README__GOVERNANCE_ENGINES.md`

**Rule:** все движки семейства обязаны соответствовать engine-template скелету:
- единый Doc Control
- mini-contract
- hard gates
- failures/edge cases
- xref без дублирования индексов

---

## 5) REQUIRED OUTPUT TYPES (FAMILY STANDARD)

Обычно governance движки производят:
- Audit Record
- Decision Record
- Change Plan / Change Note
- Dependency Record
- Violation/Blocker Record
- Consistency Report

> Каждый движок обязан явно перечислить PRODUCES в mini-contract.

---

## 6) DEPENDENCY POLICY (STRICT)

### 6.1 No hidden dependencies
Если движок требует другой движок:
- он обязан указать это в `DEPENDS_ON`
- и обязан иметь запись в dependency registry (формат стандарта)

### 6.2 Cycles (allowed only with justification)
Циклы допускаются только если:
- описана причина
- указан механизм разрыва цикла (approval/gate/stage)
- одобрено через decision approval

---

## 7) REFERENCE / NON-CANON ROSTER (OPTIONAL)

> Этот блок **не является каноном**. Канон — в глобальном ENG INDEX.

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

## 8) FAMILY QUALITY BAR (WHAT “DONE” MEANS)

Движок семейства считается “готовым” только если:
- соблюдены правила заголовка (STATUS/LOCK/VERSION/UID)
- есть mini-contract
- есть минимум 5 hard-gates
- есть good/bad examples
- есть failure modes
- зависимости объявлены и зарегистрированы
- изменения канона создают audit запись

---
LOCK: <OPEN|FIXED>
