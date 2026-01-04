# ENG ENGINES REALM — LAYER README (REALM LAW)
FILE: 00__README__ENGINES_REALM.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
REALM_TYPE: LAYER_REALM
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0
ROLE: Definition of ENG layer + laws + boundaries + interfaces to other entity classes

LOCK: FIXED

---

## 0) WHAT IS ENG (DEFINITION)

**ENG (Engines)** — это слой “производящих механизмов” Universe Engine.

ENG-движок = **формализованная производственная функция**, которая:
- получает входные артефакты (CONSUMES),
- делает преобразование по правилам,
- выдаёт выходные артефакты (PRODUCES),
- имеет явные зависимости (DEPENDS_ON),
- и кладёт результат в понятную цель (OUTPUT_TARGET).

ENG не “обсуждает” — ENG **производит**.

---

## 1) ENG PRIME LAW (ABSOLUTE)

### 1.1 Existence law
> Если движка нет в `00__INDEX_ALL_ENGINES.md` — он **не существует** в ENG-слое.

### 1.2 One job law
> Один движок = **одна основная функция**.  
> Если движок пытается делать 2+ разные задачи — раскалываем на 2 движка.

### 1.3 No hidden dependencies
> Любая зависимость обязана быть отражена в `DEPENDS_ON`.  
> Скрытые зависимости запрещены.

### 1.4 Output or nothing
> Результат работы движка — **артефакт**, а не “текст рассуждений”.  
> Если нет PRODUCES/OUTPUT_TARGET — движок считается incomplete.

---

## 2) ENG FILE TYPES (CANON)

В ENG-слое существует 3 типа файлов:

1) **ROOT REALM**
- `00__README__ENGINES_REALM.md` (этот файл)
- определяет законы слоя

2) **GLOBAL REGISTRY**
- `00__INDEX_ALL_ENGINES.md`
- единственный реестр существования и порядка семей/движков

3) **ENGINE FAMILY REALMS + ENGINES**
- семейства: `NN_<FAMILY>_ENGINES/`
- внутри:
  - `00__README__<FAMILY>_ENGINES.md` (realm семьи)
  - `NN__<ENGINE_NAME>_ENG.md` (движки)

---

## 3) NAMING + NUMBERING (MANDATORY)

### 3.1 Family folder naming
`NN_<FAMILY_NAME>_ENGINES`

### 3.2 Engine file naming
`NN__<ENGINE_NAME>_ENG.md`

### 3.3 README inside family
`00__README__<FAMILY>_ENGINES.md`

### 3.4 Matching rule
> Номер в INDEX и номер в названии файла **обязаны совпадать**.

---

## 4) ENGINE MINI-CONTRACT (MANDATORY)

Каждый engine-файл обязан иметь mini-contract блок:

- CONSUMES: (1–5 типов входных артефактов)
- PRODUCES: (1–5 типов выходных артефактов)
- DEPENDS_ON: (движки-предпосылки или [])
- OUTPUT_TARGET: (куда идёт результат)

Если mini-contract отсутствует — движок **incomplete**.

---

## 5) ENGINE STANDARD STRUCTURE (RECOMMENDED)

Рекомендуемый каркас каждого движка:

1) Header (мета: FILE/SCOPE/STATUS/VERSION/LOCK)
2) Purpose (что производит)
3) Inputs (CONSUMES)
4) Outputs (PRODUCES)
5) Dependencies (DEPENDS_ON)
6) Pipeline (шаги выполнения)
7) Quality Gates (как проверить выход)
8) Failure Modes (типовые ошибки/как чинить)
9) Output Target (куда положить итог)
10) Examples (1–2 коротких примера)

---

## 6) STATUS + LOCK (STANDARD)

### 6.1 STATUS
В шапке — только один статус (пример):
- `STATUS: ACTIVE`

Запрещено дублировать второй статус в конце файла.

### 6.2 LOCK
- `LOCK: FIXED` — канонически зафиксировано
- `LOCK: OPEN` — в разработке

---

## 7) FAMILY REALM LAW (MANDATORY)

У каждого семейства ENG обязан быть realm-файл:

`00__README__<FAMILY>_ENGINES.md`

В нём обязательно:
- границы (что входит/что запрещено)
- типы артефактов входа/выхода
- список движков семьи (с назначением)
- xref: какие слои/семьи чаще всего стыкуются

---

## 8) BOUNDARIES (ANTI-DUPLICATION)

ENG не должен дублировать другие слои.

### 8.1 ENG vs ORC
- **ENG** производит артефакты (делает работу)
- **ORC** orchestrates: выбирает порядок, маршруты, пайплайны, переключает режимы

### 8.2 ENG vs SPC
- **SPC** — специализированный интеллект/эксперт (объясняет/оценивает/помогает решать)
- **ENG** — производственный механизм (выдаёт стандартизированный результат)

### 8.3 ENG vs CTL
- **CTL** — управление/контроль поведения системы (политики, режимы, переключатели)
- **ENG** — контент/производство/преобразование

### 8.4 ENG vs VAL / QA
- **VAL** — валидаторы (истина/согласованность/правила)
- **QA** — тесты качества/регрессии/контроль результатов
- ENG может иметь “quality gates” внутри, но **финальная проверка** — зона VAL/QA.

---

## 9) CROSS-LAYER INTERFACES (CONTRACTS)

ENG взаимодействует с другими классами через артефакты:

- ENG → ORC: отдаёт PRODUCES как вход для оркестрации пайплайна
- ORC → ENG: даёт задачу/маршрут/режим (но не заменяет движок)
- SPC → ENG: помогает улучшить правила/шаблоны/подходы (но не производит вместо движка)
- ENG → VAL/QA: отдаёт артефакт на проверку

---

## 10) GOVERNANCE (CHANGE LAW)

Любая правка ENG-слоя (новые движки/перенос/переименование/смена порядка) проходит governance pipeline:

- `00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md`
- `00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md`
- `00_GOVERNANCE_ENGINES/10__VERSIONING_MEMORY_ENG.md`
- `00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md`

---

## 11) COMMON FAILURE MODES (QUICK LIST)

- “движок без PRODUCES” → incomplete
- “движок без DEPENDS_ON, но использует чужие правила” → hidden dependency
- “движок делает два разных дела” → split
- “файл есть, но нет в INDEX” → non-canon
- “номер файла не совпадает с INDEX” → violation

---

## 12) START HERE (NAV)

1) Открой `00__INDEX_ALL_ENGINES.md` — выбери family.
2) Открой README семьи — пойми границы.
3) Открой нужный engine — выполни пайплайн и получи артефакт.

---

OWNER: Universe Engine
LOCK: FIXED
