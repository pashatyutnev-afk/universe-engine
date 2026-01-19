# CHANGE MANAGEMENT PROTOCOL (STANDARDS)
FILE: 02_STANDARDS/02_PROTOCOLS/01__CHANGE_MANAGEMENT_PROTOCOL.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: PROTOCOL
INDEX_TYPE: OPERATIONAL
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.1
UID: UE.PROTO.STD.CHANGE_MANAGEMENT.001
OWNER: SYSTEM
ROLE: Operational protocol for proposing, reviewing, approving, implementing, and logging changes across the repo

CHANGE_NOTE:
- DATE: 2026-01-19
- TYPE: PATCH
- SUMMARY: "Boot-aligned formatting + explicit STOP rules + explicit required artifacts + clarified rename/alias pointer contract."
- REASON: "Убрать двусмысленность и сделать протокол исполнимым как часть BOOT SEQUENCE."
- IMPACT: "Любая правка канона проходит единый минимальный пайплайн и оставляет следы в логах/реестрах."
- CHANGE_ID: UE.CHG.2026-01-19.PROTO.CHANGE_MGMT.001

---

## 0) PURPOSE (LAW)
Этот протокол описывает, **как вносить изменения** в Universe Engine так, чтобы:
- не ломать канон и навигацию,
- сохранять единый источник истины (SoT),
- оставлять прозрачный след изменений (registry + logs),
- не создавать “битых ссылок” и дублей смысла.

---

## 1) SCOPE (WHEN IT APPLIES)
Протокол обязателен для:
- новых файлов и новых сущностей (SPC/ORC/ENG/CTL/VAL/QA/XREF);
- правок законов, стандартов, протоколов, шаблонов;
- правок индексов и реестров (existence / doc registry / entity registry);
- переименований / переносов / деприкаций;
- массовых миграций структуры.

---

## 2) ABSOLUTE LAWS (STOP-FIRST)
### 2.1 No destructive edits without trace
Запрещено менять канон без:
- CHANGE_NOTE в затронутых файлах,
- обновления реестров (если применимо),
- записи в логах (если применимо).

### 2.2 No guessing + link discipline
Если изменение требует ссылок — использовать только корректные RAW-ссылки, которые реально существуют, без угадывания.

### 2.3 ROOT LINK BASE snapshot awareness
ROOT-INDEX — это **снимок ссылок** и не обновляется автоматически.
Если изменение затрагивает навигацию/пути/файлы, которые должны быть доступны через ROOT-INDEX, это фиксируется как отдельный шаг “REFRESH REQUIRED” (см. раздел 6.6).

---

## 3) DEFINITIONS (MINIMAL)
- **CANON** — документ/сущность, признанные истиной и соответствующие Doc Control.
- **SoT (Single source of truth)** — главный документ смысла по теме.
- **DRAFT** — подготовка, не канон.
- **ACTIVE** — канон (активный).
- **DEPRECATED** — канон прошлого, заменён.
- **ALIAS POINTER** — legacy-файл без содержания, который указывает на новый канон-путь (см. раздел 5).
- **FIXED** — заморожен: правки только по протоколам и с CHANGE_NOTE.

---

## 4) CHANGE CLASSES (STANDARD)
- **PATCH** — правка текста без изменения смысла/структуры/путей.
- **MINOR** — совместимое расширение (новый раздел/новый файл без ломки навигации).
- **MAJOR** — ломающее изменение (переименование/перенос/смена правил/структуры/совместимости).

---

## 5) REQUIRED ARTIFACTS (ALWAYS)
Любое изменение обязано иметь минимум:

1) **CHANGE_NOTE**  
   - добавляется в шапку каждого затронутого файла.

2) **Registry update (when applicable)**  
   - master-index слоя (existence rule),
   - doc-registry слоя (UID / version / status),
   - entity registry (если добавлялась/менялась сущность).

3) **Audit / changes log (when applicable)**  
   - `99_LOGS/LOG__CHANGES.md` — для системных миграций/массовых изменений,
   - `99_LOGS/LOG__AUDIT.md` — для изменений законов/индексов/протоколов/шаблонов.

---

## 6) CANON CHANGE PIPELINE (MANDATORY FLOW)
### 6.1 Classify
Определи класс изменения: PATCH / MINOR / MAJOR.

### 6.2 Impact scan
Составь список затрагиваемого:
- слои, индексы, реестры,
- UID/версии,
- ссылки/пути,
- зависимые документы.

### 6.3 Plan
Составь план действий списком файлов:
- create / edit / rename / alias / deprecate
- какие реестры обновляются
- какие логи пополняются

### 6.4 Implement
Выполни правки по плану:
- обнови содержимое,
- обнови Doc Control поля (STATUS/LOCK/VERSION/UID/CHANGE_NOTE).

### 6.5 Register (if applicable)
- обнови master-index слоя (existence),
- обнови doc-registry слоя,
- обнови entity registry (если трогали сущности).

### 6.6 Log (if applicable)
- добавь запись в `LOG__AUDIT` / `LOG__CHANGES` по типу изменения.
- если изменение требует обновления ROOT-INDEX snapshot — зафиксируй:
  - `REFRESH REQUIRED: YES`
  - `WHY: ...`
  - `WHAT TO REFRESH: ...` (какие ссылки/разделы)

### 6.7 Freeze (if canon)
Если результат — канон:
- `STATUS: ACTIVE`
- `LOCK: FIXED`
- версия повышена согласно классу (PATCH/MINOR/MAJOR)

---

## 7) RENAMES & MOVES (HARD RULE)
Переименование/перенос **всегда** делается так:

1) Создаётся новый файл в канон-пути (новое имя/папка).
2) Старый файл превращается в `DOC_TYPE: ALIAS_POINTER`, `STATUS: DEPRECATED`, `LOCK: FIXED`.
3) ALIAS POINTER содержит только:
   - CANON PATH (текстом),
   - RAW link на новый файл,
   - краткое пояснение “moved/renamed”,
   - CHANGE_NOTE.

Запрещено:
- удалять старый файл сразу, если он был доступен по RAW,
- оставлять “полу-копию” (часть текста в alias).

---

## 8) CHANGE BLOCKERS (STOP RULES)
Изменение запрещено (STOP), если оно:
- ломает existence rule (файл исчез без регистрации),
- создаёт дубли смысла (2 SoT на одну тему),
- создаёт коллизии нумерации (NN конфликт внутри папки),
- меняет канон без CHANGE_NOTE,
- требует ссылок/путей, но они не подтверждены (нет RAW/нет файла),
- нарушает правила Doc Control (STATUS/LOCK/VERSION/UID несогласованы).

---

## 9) OUTPUT DISCIPLINE (CROSS-PROTOCOL)
Любой результат изменения, который предназначен “наружу” как итог работы (правило/шаблон/пайплайн/контент), должен существовать как документ-артефакт и быть совместимым с Doc Control и соответствующими стандартами.

---

## FINAL RULE (LOCK)
Этот протокол обязателен для всех изменений канона.
--- END.
