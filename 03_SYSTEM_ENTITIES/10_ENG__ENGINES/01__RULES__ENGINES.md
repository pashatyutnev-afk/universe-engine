# ENG LAYER RULES — ENGINES RULESET (CANON LAW)
FILE: 01__RULES__ENGINES.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: RULESET
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0
ROLE: Non-negotiable rules for ENG engines: naming, structure, registry, contracts, locks

LOCK: FIXED
OWNER: Universe Engine

---

## 0) RULE LANGUAGE (NORMATIVE)

- MUST / ОБЯЗАН = нарушение ломает канон.
- MUST NOT / ЗАПРЕЩЕНО = нарушение ломает канон.
- SHOULD / СЛЕДУЕТ = сильная рекомендация.
- MAY / МОЖЕТ = допускается.

---

## 1) SINGLE SOURCE OF TRUTH (REGISTRY LAW)

### 1.1 Global Registry
ENG-слой имеет единственный глобальный реестр состава и порядка движков:

`02__INDEX_ALL_ENGINES.md`

### 1.2 Existence
Если движка нет в реестре — он не существует для ENG.

### 1.3 No hidden engines
ЗАПРЕЩЕНО создавать “временные” движки без регистрации.
ЗАПРЕЩЕНО “держать где-то” отдельный список движков, конкурирующий с реестром.

---

## 2) DIRECTORY LAW (CANON ROOT)

Канонический корень ENG:

`03_SYSTEM_ENTITIES/10_ENG__ENGINES/`

Все ENG-движки MUST находиться внутри этого корня.

---

## 3) NAMING + NUMBERING LAW

### 3.1 Family folder
Формат папки семейства:
`NN_<FAMILY_NAME>_ENGINES`

### 3.2 Family realm file (README)
README семейства:
`00__README__<FAMILY>_ENGINES.md`

README — не движок.

### 3.3 Engine file
Формат движка:
`NN__<ENGINE_NAME>_ENG.md`

- NN начинается с 01 внутри каждого семейства.
- Номер в реестре MUST совпадать с номером в имени файла.
- Движок MUST принадлежать ровно одному семейству.

---

## 4) HEADER + STATUS + LOCK LAW

### 4.1 Header required
В каждом README и каждом движке MUST быть шапка с метаданными.

### 4.2 Single status
В документе MUST быть только один `STATUS: ...` (в шапке).
ЗАПРЕЩЕНО повторять `STATUS` в конце файла.

### 4.3 Lock required
Каждый файл MUST иметь `LOCK:` в шапке:
- `LOCK: FIXED` — канонически зафиксирован.
- `LOCK: OPEN` — в разработке.

---

## 5) MINI-CONTRACT LAW (ENGINE CONTRACT)

Каждый движок MUST содержать mini-contract:

CONSUMES:
- 1–5 типов входных артефактов

PRODUCES:
- 1–5 типов выходных артефактов

DEPENDS_ON:
- список движков-предпосылок или []

OUTPUT_TARGET:
- куда кладётся результат (папка/тип артефакта/реестр)

Если mini-contract отсутствует — движок считается incomplete и не может считаться готовым.

---

## 6) LINK LAW (RAW LINKS)

### 6.1 Family links
Каждое семейство MUST иметь realm-link (README) в реестре.

### 6.2 Engine links
Каждый движок MUST иметь прямой raw-link в реестре.

### 6.3 No placeholders
ЗАПРЕЩЕНЫ заглушки вида “список без изменений” или “будет позже”.

---

## 7) DEPENDENCY LAW (NO HIDDEN DEPENDS)

- Любые зависимости MUST быть в `DEPENDS_ON`.
- “Скрытые зависимости” ЗАПРЕЩЕНЫ.
- Циклы допускаются только если:
  - они явно перечислены,
  - и описана причина/контроль.

Зависимости должны отражаться в governance registry (см. governance engines).

---

## 8) ANTI-DUPLICATION LAW

- Два движка НЕ ДОЛЖНЫ выполнять одну и ту же функцию.
- При пересечении зон MUST быть boundary rule: кто главный, кто вторичен, что считается конфликтом.

---

## 9) CHANGE LAW (GOVERNANCE PIPELINE)

Любая правка состава/порядка/версий движков MUST проходить governance pipeline.

Минимальный обязательный порядок:
1) правка в `02__INDEX_ALL_ENGINES.md`
2) создание/правка engine file
3) обновление зависимостей (DEPENDS_ON + governance registry)
4) аудит/лог (если включено governance)

---

## 10) READY TEMPLATE (ENGINE HEADER)

Рекомендуемый минимальный шаблон шапки для движка:

FILE: NN__NAME_ENG.md
SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: <FAMILY_NAME>
LEVEL: L?
STATUS: ACTIVE
VERSION: 1.0
ROLE: ...
LOCK: OPEN|FIXED
OWNER: Universe Engine

---

## FINAL (LOCK)

ENG Ruleset — закон для ENG-слоя.
LOCK: FIXED
