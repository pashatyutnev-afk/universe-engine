# INDEX STRUCTURE SPEC (SoT)
FILE: 02_STANDARDS/01_SPECIFICATIONS/09__INDEX_STRUCTURE_SPEC.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: SPEC
SPEC_TYPE: INDEX_STRUCTURE
LEVEL: L2
STATUS: DRAFT
LOCK: OPEN
VERSION: 0.1.0
UID: UE.STD.SPEC.INDEX_STRUCTURE.001
OWNER: SYSTEM
ROLE: Single source of truth for index structure patterns (master-index, registry-index, realm-index), required blocks, numbering, and existence rules

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Нормализация legacy-spec: Doc Control + SemVer + UID + naming с номером"
- REASON: "Файл без номера запрещён; нужен SoT по структуре индексов"
- IMPACT: "Все индексы во всех слоях: LAW/STANDARDS/ENTITIES/KB/PROJECTS/ASSETS"

---

## 0) PURPOSE
Этот spec фиксирует **как должны выглядеть индексы** в системе:
- какие бывают типы индексов
- какие блоки обязаны присутствовать
- какие правила нумерации применяются
- как работает existence rule

---

## 1) INDEX TYPES (CANON SET)
### 1.1 MASTER INDEX
Роль: единственная точка истины о **составе и существовании** в слое.
Обязателен в каждом слое.

### 1.2 REGISTRY INDEX
Роль: учёт сущностей/документов/типов (UID/версии/статусы/связи).
Не всегда обязателен, но если есть — должен быть зарегистрирован.

### 1.3 REALM INDEX / REALM FILE
Роль: карта и правила внутри поддомена (realm/family).
Используется в KB и в SYSTEM_ENTITIES семействах.

---

## 2) REQUIRED BLOCKS (MINIMUM)
Любой индекс обязан содержать:

### 2.1 Doc Control Header (mandatory)
`SCOPE / LAYER / DOC_TYPE: INDEX / INDEX_TYPE / LEVEL / STATUS / LOCK / VERSION / UID / OWNER / ROLE`

### 2.2 PURPOSE (LAW)
- 1–5 строк: “что этот индекс фиксирует”
- existence rule

### 2.3 HOW TO USE (mandatory flow)
- пошаговая навигация (3–7 шагов)
- где entrypoint и куда идти дальше

### 2.4 ORDER OF AUTHORITY (priority)
- при конфликтах внутри scope индекса

### 2.5 CANON MAP (REGISTERED)
- список документов/сущностей, которые “существуют”
- строгий порядок (by number)

### 2.6 FINAL RULE (LOCK)
- короткое закрепление, что индекс — SoT по existence

---

## 3) NUMBERING RULES (STRICT)
### 3.1 Внутри папки
- если папка использует `NN__` — то **все файлы** должны иметь `NN__`
- README/realm-file допускается как `00__README__...` (если стандарт слоя это разрешает)

### 3.2 Внутри master-index
- порядок применяется “по номеру”
- номер в master-index и номер в имени файла должны совпадать, если используется нумерация

---

## 4) EXISTENCE RULE (SYSTEM)
Правило existence для любого слоя:

- если сущности нет в master-index слоя → сущности не существует для слоя
- если файл есть физически, но не зарегистрирован → это ошибка/мусор/вне канона

---

## 5) RAW LINKS (OPTIONAL POLICY)
Если индекс является публичной навигацией (для чтения без репо) — допускаются raw-ссылки.
Если индекс внутренний — достаточно PATH.

Рекомендация:
- master-index слоёв: PATH + RAW
- registry index: PATH (RAW опционально)

---

## 6) ANTI-DUPLICATION (INDEX LEVEL)
Запрещено:
- два master-index одного слоя
- два индекса, которые оба объявляют existence для одного и того же scope

Если нужен “быстрый доступ” — это делается как:
- ссылки в master-index
- или отдельный “map” файл, но он НЕ объявляет existence и НЕ SoT

---

## 7) OPEN ITEMS (DRAFT TODO)
- закрепить единый формат секции CANON MAP (таблица vs список)
- закрепить правила anchor/jump-секций (Quick Nav)
- связать INDEX_TEMPLATE и этот spec через UID/XREF

---

## FINAL RULE
Этот spec является SoT по структуре индексов.
Пока STATUS: DRAFT — допускает правки.
--- END.
