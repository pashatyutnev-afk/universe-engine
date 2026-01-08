# CANON PROTOCOL (LAW) — CANON
FILE: 01_SYSTEM_LAW/04__CANON_PROTOCOL.md

SCOPE: Universe Engine
LAYER: 01_SYSTEM_LAW
DOC_TYPE: LAW
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.LAW.CANON_PROTOCOL.001
OWNER: SYSTEM
ROLE: Defines canon enforcement rules: header truth, existence-by-index, raw-only navigation, anti-duplication, and canon change constraints.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Canon protocol hardened: header-only truth, existence-by-index, raw-only navigation, anti-duplication, and canon change gating."
- REASON: "Stop drift, conflicting metadata, broken navigation, and orphan files."
- IMPACT: "All canon artifacts become deterministic, index-driven, and compatible across layers."
- CHANGE_ID: UE.CHG.2026-01-08.LAW.CANON_PROTOCOL.001

---

## 0) PURPOSE (LAW)

Этот закон фиксирует, что такое КАНОН и как он удерживается стабильным:
- канон читается и проверяется без догадок
- метаданные не “гуляют” по файлу
- навигация не ломается
- ничего не считается существующим, если его нет в каноническом индексе

---

## 1) DEFINITIONS (STRICT)

**CANON ARTIFACT** — файл/сущность, управляемая законами/стандартами системы и зарегистрированная в канонических индексах.

**CANON INDEX** — документ, который задаёт существование/состав/порядок в своём скоупе.  
Если артефакта нет в индексе — он не существует для системы.

**HEADER** — верхний блок метаданных файла (после заголовка), содержащий обязательные поля (см. раздел 4).  
Header — единственная точка истины о метаданных.

**RAW LINK** — ссылка на raw-содержимое файла (читаемая без открытия репозитория).

---

## 2) EXISTENCE LAW (ABSOLUTE)

### 2.1 Existence-by-index
- Если артефакта **нет** в каноническом индексе своего слоя/реестра — он **не существует** для системы.
- Файлы, существующие на диске, но не зарегистрированные индексом — **ignored / non-canon**.

### 2.2 Index order is canon
- Порядок внутри канонического индекса является законом порядка.  
- Изменение порядка = каноническое изменение.

---

## 3) NAVIGATION LAW (RAW-ONLY)

### 3.1 Raw-only requirement
- Все канонические индексы/реестры обязаны ссылаться на артефакты **только raw-ссылками**, если ссылка требуется стандартом навигации.
- Ссылки, требующие открытия GitHub UI/папок/дерева — считаются недостаточными для канона.

### 3.2 Self-contained reading
- Индекс должен быть читаем и применим **без** открытия репозитория.

---

## 4) HEADER TRUTH LAW (SINGLE SOURCE OF TRUTH)

### 4.1 Header is the only truth
- Метаданные файла признаются истинными **только** в HEADER.
- Любая попытка повторить метаданные ниже по тексту создаёт риск конфликтов и запрещена.

### 4.2 Mandatory header fields (base set)
Каждый канонический документ обязан иметь HEADER с минимумом:

- FILE:
- SCOPE:
- LAYER:
- DOC_TYPE:
- LEVEL:
- STATUS:
- LOCK:
- VERSION:
- UID:
- OWNER:
- ROLE:
- CHANGE_NOTE:

Если документ является сущностью (например ENGINE/REGISTRY/INDEX), допускаются дополнительные поля:
- ENTITY_GROUP:
- FAMILY:
- CLASS:
но они не заменяют базовый набор.

---

## 5) ANTI-DUPLICATION LAW (NO SECOND META)

### 5.1 Forbidden duplications
Запрещено:
- второй `STATUS:` в конце/середине
- второй `LOCK:` в конце/середине
- “OWNER/ROLE/VERSION/UID” повтором в тексте
- отдельные “FINAL RULE: LOCK” блоки с повтором меты

Разрешено:
- ссылаться словами (“см. статус в шапке”), но не повторять поля как метадату.

### 5.2 If conflict exists
Если в файле обнаружена дублирующая мета:
- истинной считается только HEADER
- дублирующая мета подлежит удалению как нарушение закона

---

## 6) CANON CHANGE LAW (PIPELINE ONLY)

Любое изменение, затрагивающее канон, обязано идти через Change Control:
- `03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md`

Каноническое изменение включает:
- правки LAW/STANDARDS/INDEX/REGISTRY
- любые `LOCK: FIXED`
- любые изменения состава/порядка индексов
- переименования/перемещения/удаления канонических файлов

---

## 7) MINIMUM STRUCTURE LAW (SHAPE)

Канонический документ должен иметь понятную структуру (минимум):
- PURPOSE
- DEFINITIONS (если термины неочевидны)
- RULES / PIPELINE / REQUIREMENTS (по типу документа)
- REFERENCES (если обязаны)

Структура может расширяться, но не должна ломать читабельность и детерминированность.

---

## 8) ENFORCEMENT (S0 BLOCKERS)

Нарушения уровня S0 (STOP):
- S0-1: артефакт канонический, но отсутствует в каноническом индексе
- S0-2: индекс требует ссылку, но нет raw-link
- S0-3: метаданные дублируются (второй STATUS/LOCK/UID/VERSION/OWNER/ROLE)
- S0-4: header неполный (нет обязательных полей)
- S0-5: изменён порядок в индексе без фиксации через change pipeline

При S0:
- изменение считается invalid
- требуется откат или emergency-путь

---

## 9) FINAL RULE (LOCK)

OWNER: SYSTEM  
LOCK: FIXED
