# RULES — ENG ENGINES (CANON STANDARD)
FILE: 01__RULES__ENGINES.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: RULESET
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0
ROLE: Canon law that defines how every ENG engine file must be written, validated, linked, and connected to projects

---

## 0) PURPOSE (LAW)

Этот документ — **закон формата** для всех файлов класса **ENG (Engines)**.

Он фиксирует:
- обязательную структуру каждого engine-файла
- правила STATUS/LOCK
- mini-contract (обязательный контракт движка)
- правила зависимостей (DEPENDS_ON)
- правила OUTPUT_TARGET (куда складываются результаты в проектах)
- границы ответственности (anti-duplication)
- правила версионирования и правок

Если движок нарушает этот документ — он считается **incomplete / non-canon** до исправления.

---

## 1) CANON PATH + NAMING (MANDATORY)

### 1.1 Canon path rule
Все ENG движки живут только в:
`03_SYSTEM_ENTITIES/10_ENG__ENGINES/<FAMILY_PATH>/<FILE>`

### 1.2 Family folder naming
Формат папки семейства:
`NN_<FAMILY_NAME>_ENGINES`

- `NN` — глобальный порядок семейств (00, 01, 02…)
- README семейства всегда начинается с `00__`

### 1.3 Engine file naming
Формат файла движка:
`NN__<ENGINE_NAME>_ENG.md`

- `NN` начинается с `01` **внутри** семейства
- номер в названии файла и номер в INDEX обязаны совпадать

### 1.4 README rule
README не является движком и всегда:
`00__README__<FAMILY>_ENGINES.md`

---

## 2) HEADER STANDARD (MANDATORY)

Каждый engine-файл обязан начинаться с заголовка и шапки:

- H1 title
- FILE:
- SCOPE:
- ENTITY_GROUP: ENGINES (ENG)
- FAMILY:
- LEVEL:
- STATUS:
- VERSION:
- ROLE:

### 2.1 STATUS rule
`STATUS` указывается **только** в шапке.

Допустимые значения:
- `ACTIVE` — используется сейчас
- `DRAFT` — в разработке
- `OPTIONAL` — необязательный движок (можно отключать в “минимальном режиме”)
- `DEPRECATED` — устарел, но ещё хранится ради истории/совместимости
- `ARCHIVED` — заморожен, больше не используется

---

## 3) LOCK STANDARD (MANDATORY)

В конце каждого engine-файла допускается только LOCK, без второго STATUS.

Допустимые значения:
- `LOCK: OPEN` — файл можно менять, он в разработке
- `LOCK: FIXED` — канонически зафиксирован (правки только через governance)

### 3.1 Footer rule
Футер движка:

- OWNER: Universe Engine
- LOCK: OPEN/FIXED

Запрещено внизу:
- второй `STATUS`
- повтор `VERSION`
- повтор шапки

---

## 4) ENGINE FILE SKELETON (MANDATORY ORDER)

Каждый ENG engine-файл обязан иметь следующие секции и порядок:

1) PURPOSE
2) BOUNDARIES (WHAT IT IS NOT)
3) INPUTS
4) OUTPUTS
5) MINI-CONTRACT (MANDATORY)
6) PROCEDURE (PIPELINE)
7) VALIDATION RULES (GATES)
8) FAILURE MODES (COMMON FAILS)
9) CHANGE RULES (HOW TO UPDATE)
10) FOOTER (OWNER + LOCK)

Если секции нет — движок считается incomplete.

---

## 5) MINI-CONTRACT LAW (MANDATORY)

Каждый движок обязан иметь mini-contract блок **в точном формате**:

### 5.1 Mini-contract (canon format)

CONSUMES:
- (1–5 items)

PRODUCES:
- (1–5 items)

DEPENDS_ON:
- (list of engine file paths) OR []

OUTPUT_TARGET:
- (canonical path(s) where produced artifacts must be placed)

### 5.2 Rules
- CONSUMES/PRODUCES: максимум 5 пунктов (сжимай)
- DEPENDS_ON: либо список путей, либо `[]` (пусто)
- OUTPUT_TARGET обязателен всегда
- Нельзя писать “куда-то в проект” — только канонический путь по структуре

---

## 6) OUTPUT_TARGET → PROJECT STRUCTURE MAP (MANDATORY)

ENG движки должны быть привязаны к реальной структуре проектов.

Канонические уровни проекта:

### L0 — Intake (сырьё / вход)
`05_PROJECTS/<PROJECT>/02_INTAKE__L0/`

### L1 — Project (каркас / рабочая структура)
`05_PROJECTS/<PROJECT>/03_PROJECT__L1/`

### L2 — Canon (канонизация / утверждённые факты)
`05_PROJECTS/<PROJECT>/04_PROJECT__L2/`

### L3 — Output (выпуск: арт/книга/фильм/игра/музыка/серии)
`05_PROJECTS/<PROJECT>/05_PROJECT__L3/`

### 6.1 Output rule
Каждый движок обязан:
- указать OUTPUT_TARGET минимум в один уровень (L0/L1/L2/L3)
- если движок системный (governance/meta), OUTPUT_TARGET может быть системной папкой:
  `99_LOGS/` или `02_STANDARDS/` или `03_SYSTEM_ENTITIES/90_XREF__CROSSREF/` (если у вас так заведено)

---

## 7) DEPENDENCY RULES (NO HIDDEN DEPENDENCIES)

### 7.1 Explicit dependency rule
Любая зависимость должна быть указана:
- в `DEPENDS_ON` mini-contract

Если зависимость не указана — она запрещена.

### 7.2 Registry sync rule
Если система использует dependency registry (governance), то зависимости движка должны быть совместимы с:
`00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG.md`

---

## 8) ANTI-DUPLICATION / BOUNDARY LAW (MANDATORY)

Каждый движок обязан явно описать границы (Boundaries), чтобы не было дублей.

### 8.1 Canon boundaries (global)
- Narrative rhythm (story-time) → `02_DOMAIN_NARRATIVE_ENGINES/05__PACING_RHYTHM_ENG.md`
- Editing rhythm (screen-time) → `08_KNOWLEDGE_PRODUCTION_ENGINES/07__EDITING_MONTAGE_ENG.md`

- Production audio (sync/design/placement/clarity) → `08_KNOWLEDGE_PRODUCTION_ENGINES/08__SOUND_MUSIC_ENG.md`
- Deep music (composition/harmony/arrangement/vocal/mix) → `09_SOUND_MUSIC_ENGINES/*`

### 8.2 Boundary rule
В секции BOUNDARIES движок обязан:
- перечислить 2–5 вещей, которые он НЕ делает
- при необходимости дать ссылку “это делает другой движок” (путь)

---

## 9) VALIDATION RULES (GATES)

Каждый движок обязан иметь 3–7 правил валидации.

Формат:
- XX1: ...
- XX2: ...
- XX3: ...

Правило:
- Валидация должна быть проверяема человеком (и по возможности QA-слоем).

---

## 10) FAILURE MODES (COMMON FAILS)

Каждый движок обязан перечислить 3–7 типичных провалов:
- что ломается
- почему ломается
- какой быстрый фикс

Это делает движки “боевыми”, а не теорией.

---

## 11) CHANGE RULES (HOW TO UPDATE)

Любая правка движка должна:
- повышать VERSION (semver или простая 1.0 → 1.1)
- проходить governance pipeline (если LOCK: FIXED)

Рекомендуемый governance пайплайн:
- `00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md`
- `00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md`
- `00_GOVERNANCE_ENGINES/10__VERSIONING_MEMORY_ENG.md`
- `00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md`

---

## 12) REFERENCE — ENGINE FILE TEMPLATE (CANON)

Ниже эталонный шаблон движка (копируй и заполняй):

# <ENGINE TITLE>
FILE: NN__<ENGINE_NAME>_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: <NN_FAMILY_ENGINES>
LEVEL: Lx
STATUS: ACTIVE
VERSION: 1.0
ROLE: <one line role>

---

## PURPOSE
(что делает движок и зачем)

---

## BOUNDARIES (WHAT IT IS NOT)
- (что движок НЕ делает)
- (куда относится вместо этого — путь)

---

## INPUTS
- (inputs)

---

## OUTPUTS
- (outputs)

---

## MINI-CONTRACT (MANDATORY)

CONSUMES:
- ...

PRODUCES:
- ...

DEPENDS_ON:
- (path) OR []

OUTPUT_TARGET:
- (canonical path)

---

## PROCEDURE (PIPELINE)
1) ...
2) ...
3) ...

---

## VALIDATION RULES (GATES)
- XX1: ...
- XX2: ...
- XX3: ...

---

## FAILURE MODES (COMMON FAILS)
- ...
- ...
- ...

---

## CHANGE RULES
- ...

---

OWNER: Universe Engine
LOCK: OPEN

---

OWNER: Universe Engine
LOCK: FIXED

(NOTE: выбираешь только один LOCK в конце)
---

OWNER: Universe Engine
LOCK: FIXED
