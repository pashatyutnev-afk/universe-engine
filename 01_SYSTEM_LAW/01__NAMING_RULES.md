# UNIVERSE ENGINE — NAMING RULES (LAW)
FILE: 01_SYSTEM_LAW/01__NAMING_RULES.md

SCOPE: Universe Engine
LAYER: SYSTEM LAW
LEVEL: L0
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Закон именования. Фиксирует обязательные форматы имен файлов/папок/индексов/шаблонов во всей системе.

---

## 0) PURPOSE
Naming Rules нужны чтобы:
- исключить хаос и дубли
- обеспечить строгую сортировку и навигацию
- обеспечить совместимость индексов и процессов

---

## 1) UNIVERSAL LAWS (ABSOLUTE)
### 1.1 ASCII ONLY
Имена файлов/папок: только латиница, цифры, `_` и `-`.

### 1.2 NO SPACES
Пробелы запрещены.

### 1.3 STABLE ORDER
Порядок задаётся номером в начале имени.

---

## 2) FOLDER NAMING (CANON)
Формат папки:

NN_<NAME>

Где:
- NN — двухзначный порядок: 00..99
- NAME — UPPER_SNAKE_CASE или MIXED_CASE (но стабильно внутри слоя)

Примеры:
- `01_SYSTEM_LAW`
- `02_STANDARDS`
- `03_SYSTEM_ENTITIES`
- `10_ENG__ENGINES`

Запрещено:
- папки без номера, если это уровень с сортировкой по порядку
- “misc”, “temp”, “new”, если это канон-слой

---

## 3) FILE NAMING (CANON)
### 3.1 Standard file
Формат:

NN__NAME.md

Примеры:
- `00__SYSTEM_LAW.md`
- `04__CANON_PROTOCOL.md`
- `01__SCENE_PIPELINE_ORC.md`

### 3.2 README file (special)
README всегда имеет номер `00` и формат:

00__README__<SCOPE>.md

Примеры:
- `00__README__ENGINES_REALM.md`
- `00__README__CORE_ENGINES.md`

---

## 4) INDEX NAMING (CANON)
### 4.1 Master index
Формат:

00__INDEX__<SCOPE>.md

Примеры:
- `01_SYSTEM_LAW/00__INDEX__SYSTEM_LAW.md`

### 4.2 Registry index (all items)
Формат:

02__INDEX_ALL_<SCOPE>.md

Примеры:
- `10_ENG__ENGINES/02__INDEX_ALL_ENGINES.md`
- `20_ORC__ORCHESTRATORS/02__INDEX_ALL_ORCHESTRATORS.md`

---

## 5) TEMPLATE NAMING (CANON)
Шаблон всегда помечается как TEMPLATE:

NN__TEMPLATE__<TYPE>__<SCOPE>.md

Примеры:
- `00__TEMPLATE__ENGINE__CORE_ENGINES.md`
- `00__TEMPLATE__README__CORE_ENGINES.md`

Малые шаблоны (вспомогательные) допускают формат:
NNX__TEMPLATE__<NAME>.md  
(например 06A, если это мини-шаблон рядом со стандартом)

---

## 6) ENTITY FILE NAMING (ENT)
ENT файлы обязаны содержать суффикс группы:

- `_ENG.md` для engines
- `_ORC.md` для orchestrators
- `_SPC.md` для specialists
- `_CTL.md` для controllers
- `_VAL.md` для validators
- `_QA.md`  для quality

Пример:
- `01__SCENE_PIPELINE_ORC.md`
- `01__READINESS_CHECK_CTL.md`

---

## 7) NUMBERING RULE (MANDATORY)
- Нумерация начинается с `01` внутри реестра сущностей (если `00` занят под README/шаблоны).
- Номер в индексе и номер в имени файла должны совпадать.
- При вставке нового элемента в середину:
  - запрещено “ломать” всю нумерацию без причины
  - допускается только через Canon Protocol (если реально надо)

---

## 8) FINAL LAW
> Имя = навигация.  
> Нарушение naming rules считается дефектом системы и исправляется в первую очередь.

OWNER: Universe Engine  
LOCK: FIXED

---
END.
