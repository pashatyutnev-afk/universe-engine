# KB RULES — GOVERNANCE (CANON)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: RULES
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.LAW.RULES.001
OWNER: SYSTEM
ROLE: Governance ruleset for Knowledge Base layer: naming, structure, existence, canon boundaries

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Введены жёсткие правила структуры KB: realms как порталы, контент в topics, алиасы вынесены в 98/99, системные справочники в 90+"
- REASON: "Устранение коллизий, 404, дублей и распухания realms"
- IMPACT: "Вся навигация, существование и рост KB"

---

## 0) PURPOSE (LAW)
Эти правила фиксируют **как устроен слой KB**, какие файлы считаются каноном, и как он расширяется без бардака.

---

## 1) ORDER OF AUTHORITY (KB)
При конфликте внутри KB слой подчиняется строго:

1) `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/*`
2) `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`
3) `04_KNOWLEDGE_BASE/*` + `04_KNOWLEDGE_BASE/10_TOPICS/*`

---

## 2) EXISTENCE RULE (ABSOLUTE)
- **Существует только то, что зарегистрировано** в `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`.
- Файл в репо без регистрации в master-index = **NON-CANON / ignored**.
- Любой новый KB-документ сначала регистрируется в master-index, потом создаётся файл.

---

## 3) KB STRUCTURE MODEL (CANON)
Слой KB обязан иметь следующие зоны:

### 3.1 Governance (управление)
Папка: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/`
- Здесь живут правила, карты, реестры, шаблоны, системные справочники KB.

### 3.2 Realms (порталы знаний)
Файлы: `04_KNOWLEDGE_BASE/01__*.md ... 08__*.md`
- Realm-файлы — это **порталы/оглавления/навигаторы**, а не склад всего контента.
- Realm обязан ссылаться на темы/доки, но **не обязан** содержать весь текст внутри себя.

### 3.3 Topics (контент)
Папка: `04_KNOWLEDGE_BASE/10_TOPICS/`
- Здесь живут конкретные KB-статьи/темы.
- Реалмы должны указывать на topics и формировать карту знаний.

### 3.4 System KB dictionaries (справочники)
Только в governance и только `90__*`:
- Пример: `00_KB_GOVERNANCE/90__KB_TAGS.md`
- Любые “системные справочники” (типы тегов/REL/XREF/классы) запрещено хранить рядом с realms.

### 3.5 Aliases / Legacy pointers
Только `98__*` / `99__*` в корне KB:
- Это НЕ канон.
- Их содержимое = **только pointer** на `00__INDEX__KNOWLEDGE_BASE.md` (без правил/контента).

---

## 4) NAMING + NUMBERING (MANDATORY)
### 4.1 File naming (strict)
Любой канонический файл KB:
- `NN__NAME.md` (двойное подчёркивание обязательно)
- `NN` = двухзначный порядок внутри своей зоны.

### 4.2 Allowed numbering ranges (hard)
- `00_*` — только governance зона
- `01..08__*` — только realms
- `10_*` — только topics зона
- `90..97__*` — системные справочники (только governance)
- `98..99__*` — алиасы (non-canon)

Если файл не попадает в диапазон — это ошибка структуры.

---

## 5) DOC CONTROL (MANDATORY)
Каждый канонический KB-файл обязан иметь шапку:
- SCOPE / LAYER / DOC_TYPE / LEVEL / STATUS / LOCK / VERSION / UID / OWNER / ROLE

Правила:
- SemVer строго `X.Y.Z`
- `UID` обязателен и уникален
- `STATUS` допускается только из множества: `DRAFT | ACTIVE | DEPRECATED | ARCHIVED`
- `LOCK` допускается только: `OPEN | FIXED`
- Запрещено дублировать `OWNER/LOCK/VERSION/STATUS` внизу файла отдельными строками

Файл без Doc Control шапки = **NON-CANON**.

---

## 6) CONTENT RULES (ANTI-DUPLICATION)
- Один смысл → один KB-артефакт.
- Если тема нужна в нескольких realms — делается **один** topic-док + XREF/REL ссылки из realms.
- Дубли текстов между realms запрещены без явного XREF/REL.

---

## 7) CREATE / CHANGE FLOW (MANDATORY)
### 7.1 Create new KB doc
1) Добавить запись в `00__INDEX__KNOWLEDGE_BASE.md`
2) Создать файл в правильной зоне (governance / realms / topics)
3) Присвоить UID + SemVer + шапку Doc Control
4) Добавить XREF/REL ссылки из realms (если это topic)
5) Зафиксировать change-note внутри файла

### 7.2 Rename / Move
- Переименование/перенос = изменение канона.
- Старый путь должен:
  - либо быть удалён,
  - либо превращён в `98/99` alias-pointer (если нужно сохранить входную точку).

---

## 8) ENFORCEMENT (HARD)
Если нарушено любое правило этого файла:
- документ считается **NON-CANON / ignored**
- ссылки на него из realms/индексов должны быть удалены или переведены в non-canon секцию

---

## FINAL RULE (LOCK)
Этот RULESET фиксирует базовую архитектуру KB и обязателен для соблюдения.
--- END.
