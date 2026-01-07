# STORAGE MAP — HOME / WORK / OUTPUT_TARGET
FILE: 02_STANDARDS/06_MARKING_STANDARDS/02__STORAGE_MAP.md

SCOPE: Universe Engine / Storage
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Единый стандарт “куда что класть” + запреты на хаотичное хранение.

SOURCE OF TRUTH:
- HOME/WORK/OUTPUT_TARGET правила описаны здесь.

---

## 0) CORE LAW
- Любой объект (ENT/ART/ASSET/DB/LOG) обязан иметь понятный STORAGE TARGET.
- Канон не хранится в WORK.
- Если объект лежит не там — он считается NON-CANON / MISPLACED.

---

## 1) DEFINITIONS
- HOME — каноническое место хранения
- WORK — рабочая зона (FAST / черновики / промежуточные)
- OUTPUT_TARGET — место финального результата (выпуск/канон проекта/ассеты)

---

## 2) ROOT MAP (верхний уровень)
- 01_SYSTEM_LAW — законы
- 02_STANDARDS — стандарты/спеки/шаблоны
- 03_SYSTEM_ENTITIES — системные сущности (ENG/ORC/SPC/CTL/VAL/QA)
- 04_KNOWLEDGE_BASE — знания/контент базы
- 05_PROJECTS — производство/проекты
- 06_ASSETS — ассеты/медиа
- 07_MODELS — модели/описания моделей
- 08_DATABASES — реестры/табличные базы
- 99_LOGS — логирование/аудит

---

## 3) STORAGE RULES BY CLASS
### 3.1 System docs (LAW / STANDARDS)
- HOME: `01_SYSTEM_LAW/` и `02_STANDARDS/`
- WORK: запрещено выносить в проекты
- OUTPUT_TARGET: HOME (после фиксации)

### 3.2 System entities (ENG/ORC/SPC/CTL/VAL/QA)
- HOME: `03_SYSTEM_ENTITIES/<CLASS>/...`
- WORK: допускается только в dev-подветках внутри того же класса (если введёте)
- OUTPUT_TARGET: HOME

### 3.3 Knowledge base entities (world content)
- HOME: `04_KNOWLEDGE_BASE/`
- WORK: `05_PROJECTS/.../02_INTAKE_L0` и `03_PROJECT_L1`
- OUTPUT_TARGET: `05_PROJECTS/.../04_PROJECT_L2/CANON` (если это “канон проекта”)

### 3.4 Production artifacts
- WORK: `05_PROJECTS/.../02_INTAKE_L0` и `03_PROJECT_L1`
- OUTPUT_TARGET: `05_PROJECTS/.../05_PROJECT_L3/<FORMAT>/`

### 3.5 Assets (media)
- HOME: `06_ASSETS/`
- WORK: допускается временно внутри проектов
- OUTPUT_TARGET: `06_ASSETS/` (канон ассетов)

---

## 4) STORAGE VIOLATIONS (S0)
S0 нарушение:
- канонический документ лежит в WORK
- системные стандарты/законы лежат в проектах
- финальный артефакт отсутствует в OUTPUT_TARGET

См. 04__PRIORITY_S0_S3.md

---
END.
