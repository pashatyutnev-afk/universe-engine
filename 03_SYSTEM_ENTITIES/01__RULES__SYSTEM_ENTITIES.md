# SYSTEM ENTITIES REALM — RULES (CANON)

FILE: 03_SYSTEM_ENTITIES/01__RULES__SYSTEM_ENTITIES.md
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: RULE
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.1
UID: UE.ENT.RULE.SYS_ENTITIES.001
OWNER: SYSTEM
ROLE: Operational rules for entity realm (SPC/ORC/ENG/CTL/VAL/QA/XREF + REG/TPL): what is an entity, how it becomes operationally real, and how this layer must be navigated in RAW-only mode.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Rebuilt RULES into a strict operational law: no type-mixing, explicit operational existence rule via INDEX, RAW-only navigation contract, and creation/update discipline."
- REASON: "Navigation loops + confusion came from mixing README/RULE/INDEX semantics and missing operational definition of 'real' entities."
- IMPACT: "Entity layer becomes deterministic: operational reality is defined, changes are controlled, and routing is stable."
- CHANGE_ID: UE.CHG.2026-01-20.SYS_ENTITIES.RULES.001

---

## 0) PURPOSE (LAW)
Этот документ фиксирует **правила слоя `03_SYSTEM_ENTITIES`**:
- что считается “сущностью” (entity) и какие бывают классы;
- как сущность становится **операционно реальной** (operationally real);
- как навигироваться по слою при RAW-only;
- как создавать/обновлять сущности без смешивания типов документов.

---

## 1) DEFINITIONS
### 1.1 Entity classes (CANON)
Entity classes в Universe Engine:
- **SPC** — specialists (владельцы намерения/решений/упаковки результата)
- **ORC** — orchestrators (пайплайны, порядок шагов, handoffs)
- **ENG** — engines (детерминированная микрологика/методы)
- **CTL** — controllers (политики, лимиты, блокировки, гейты)
- **VAL** — validators (проверки соответствия + фиксация нарушений)
- **QA** — quality (гейты приёмки, эталоны, регресс)
- **XREF** — crossref (карты соответствий, матрицы, схемы пайплайнов)

Дополнительно (служебные подсистемы слоя):
- **REG** — registries (реестры существования/изменений/дефолтов)
- **TPL** — templates (шаблоны для создания сущностей/документов внутри слоя)

### 1.2 Document types inside this realm (STRICT)
В `03_SYSTEM_ENTITIES` допустимы разные типы документов, но **каждый тип делает только своё**:
- **README** — короткая записка “что это за слой и как читать” (не RULE, не INDEX)
- **RULE** — правила поведения/ограничения (не INDEX)
- **INDEX** — навигация/registry состава (не RULE)
- **TEMPLATE** — шаблоны (не правила)
- **REGISTRY** — реестры (учёт/журналирование/списки)

Запрещено подменять:
- RULE документом INDEX,
- INDEX документом RULE,
- README документом INDEX/RULE.

---

## 2) OPERATIONAL EXISTENCE RULE (ABSOLUTE)
### 2.1 What is “operationally real”
Сущность считается **операционно реальной** только если:
- она зарегистрирована в **каноническом индексе слоя** `03_SYSTEM_ENTITIES/02__INDEX__SYSTEM_ENTITIES.md`.

Если файл физически существует в репозитории, но **не зарегистрирован** в индексе слоя:
- он считается **NON-OPERATIONAL / ignored** для выполнения задач,
- его нельзя использовать как “доказанное существование сущности”.

### 2.2 Why this rule exists
Причина — режим просмотра/навигации:
- в практике пользователю и системе нужен **один стабильный список**, который определяет “что существует”,
- иначе появляются петли и “фантомные” сущности.

---

## 3) RAW-ONLY NAVIGATION CONTRACT (ABSOLUTE)
Если активирован RAW-only режим:
- переходы делаются **только по RAW ссылкам**;
- запрещено угадывать пути/URL;
- индексы/реестры должны содержать ссылки так, чтобы ими можно было пользоваться напрямую.

Минимальные точки входа слоя:
- README: `03_SYSTEM_ENTITIES/00__README__SYSTEM_ENTITIES.md`
- RULES: `03_SYSTEM_ENTITIES/01__RULES__SYSTEM_ENTITIES.md`
- INDEX: `03_SYSTEM_ENTITIES/02__INDEX__SYSTEM_ENTITIES.md`

(Глобальные “супер-индексы” допускаются, но они **не отменяют** канонический INDEX слоя. Если такой супер-индекс существует — он должен быть зарегистрирован в INDEX слоя как отдельный item.)

---

## 4) REALM STRUCTURE (CANON)
Структура слоя (верхний уровень) задаёт классы сущностей:

- `00_REG__REGISTRIES/` — реестры слоя (индексы реестров, журналы, deprecation, changelog)
- `01_TPL__TEMPLATES/` — шаблоны сущностей/документов слоя
- `10_ENG__ENGINES/` — ENG сущности
- `20_ORC__ORCHESTRATORS/` — ORC сущности
- `30_SPC__SPECIALISTS/` — SPC сущности
- `40_CTL__CONTROLLERS/` — CTL сущности
- `50_VAL__VALIDATORS/` — VAL сущности
- `60_QA__QUALITY/` — QA сущности
- `90_XREF__CROSSREF/` — XREF сущности

Каждый realm-подкаталог может иметь собственные README/INDEX/RULES (если они зарегистрированы и не нарушают типовую дисциплину).

---

## 5) CREATION & UPDATE DISCIPLINE (MUST)
### 5.1 Creating a new entity (standard flow)
Любая новая сущность (SPC/ORC/ENG/CTL/VAL/QA/XREF) создаётся так:
1) берётся соответствующий TEMPLATE из `01_TPL__TEMPLATES/` (или из под-templates внутри класса, если так принято);
2) заполняется header (FILE/SCOPE/LAYER/DOC_TYPE/LEVEL/STATUS/LOCK/VERSION/UID/OWNER/ROLE/CHANGE_NOTE);
3) файл кладётся в правильный класс-подкаталог;
4) добавляется запись в `02__INDEX__SYSTEM_ENTITIES.md` (это делает сущность operationally real);
5) при наличии реестров/журналов изменений — обновляются соответствующие REG документы.

### 5.2 Updating an existing entity
Любое изменение сущности:
- version bump по правилам versioning;
- CHANGE_NOTE обязателен (что/почему/impact/change_id);
- LOCK: FIXED означает: изменения допускаются, но только дисциплинированно (не “тихие правки”).

---

## 6) NO-DUPLICATION OF META (STRICT)
Вся мета документа живёт **только в header**:
- нельзя повторять `LOCK/OWNER/VERSION/UID/STATUS` внизу как “FINAL RULE”.
- в теле — только смысловые правила/контракты.

---

## 7) BOUNDARIES WITH OTHER LAYERS (SCOPE)
- Законы системы (LAW) живут в `01_SYSTEM_LAW` и имеют приоритет.
- Стандарты и протоколы живут в `02_STANDARDS`.
- Knowledge Base живёт в `04_KNOWLEDGE_BASE`.
Этот документ **не дублирует** их содержимое — он только фиксирует правила слоя сущностей.

---

## 8) MINIMUM COMPLIANCE CHECKLIST (CTL-LIKE)
Перед коммитом/обновлением:
- [ ] header заполнен полностью (и не дублируется в теле)
- [ ] DOC_TYPE соответствует реальной роли документа
- [ ] UID и VERSION присутствуют
- [ ] сущность/документ добавлен в `02__INDEX__SYSTEM_ENTITIES.md` (иначе он non-operational)
- [ ] RAW-only навигация не ломается (нет ссылок “угадай путь”)

--- END.
