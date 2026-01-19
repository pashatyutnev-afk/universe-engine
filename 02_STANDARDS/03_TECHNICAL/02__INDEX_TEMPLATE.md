# INDEX DOCUMENT — CANONICAL TEMPLATE (SoT)

FILE: 02_STANDARDS/03_TECHNICAL/02__INDEX_TEMPLATE.md
SCOPE: Universe Engine
LAYER: 02_STANDARDS/03_TECHNICAL
DOC_TYPE: TEMPLATE
TEMPLATE_TYPE: INDEX
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.TPL.INDEX.001
OWNER: SYSTEM
ROLE: Single canonical template for creating and maintaining any INDEX document in Universe Engine.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Rebuilt as true INDEX template (SoT): DOC CONTROL header, RAW/UID navigation contract, existence registry rules, anti-duplication, and explicit rules for when RAW links are mandatory vs forbidden."
- REASON: "Old patterns either caused alias loops or 'link cutting' that breaks operational navigation."
- IMPACT: "Indexes become deterministic: same structure everywhere, with controlled link policy per scope."
- CHANGE_ID: UE.CHG.2026-01-20.TPL.INDEX.002

---

## 0) PURPOSE (LAW)
Этот TEMPLATE задаёт **единственный канонический формат** для любых `DOC_TYPE: INDEX` документов Universe Engine.

INDEX документ предназначен для:
- навигации и фиксации состава (registry / existence map) внутри области;
- правил порядка и приоритета (если нужно);
- определения границ области (scope boundaries);
- выдачи **контракта чтения** (как интерпретировать записи);
- поддержки режима RAW-only (если включён законами рантайма).

INDEX **не выполняет задач**.  
Задачи выполняют `ENTRYPOINT / RUNBOOK` документы (отдельный DOC_TYPE).

---

## 1) ABSOLUTE RULES (MUST)

### 1.1 Header truth (ABSOLUTE)
- Вся мета (FILE/SCOPE/LAYER/STATUS/LOCK/VERSION/UID/OWNER/ROLE и т.д.) живёт **только в header**.
- Запрещено дублировать метаданные ниже шапки (никаких повторов LOCK/OWNER/STATUS/VERSION/UID в конце).

### 1.2 RAW-only navigation (RUNTIME LAW AWARE)
Если рантайм/слой требует RAW-only:
- любые навигационные переходы выполняются только по `RAW:` ссылкам, которые **разрешены правилами области**.
- запрещено угадывать пути/URL.

### 1.3 PATH is label, not navigation
- `PATH_LABEL` допускается только как метка (подсказка человеку).
- `PATH_LABEL` не считается механизмом навигации.

### 1.4 Scope discipline
- INDEX обязан явно описывать границы: что индексируется и что не индексируется.
- INDEX не должен превращаться в “док с задачами”.

### 1.5 Link policy is scope-dependent (NO “link cutting”)
Запрещено “урезать” систему общим правилом “ссылок не ставить”.
Вместо этого INDEX обязан объявить свой `NAV_RULE` и следовать ему:

- `NAV_RULE: Use RAW links only`  
  RAW ссылки допустимы и используются как механизм навигации.

- `NAV_RULE: UID-only`  
  RAW ссылки внутри тела не размещаются; навигация через UID/registry.

- `NAV_RULE: Snapshot RAW link base`  
  RAW ссылки **обязательны** (это оперативная база ссылок).  
  Это режим для ROOT snapshot / operational super-index.

Если `NAV_RULE` не определён — документ считается некорректным.

### 1.6 “Index-to-index” linking (CONTROLLED)
Разрешено только в двух случаях:
1) `NAV_RULE` явно допускает навигацию через индексы **и** это прописано в правилах слоя.
2) Этот INDEX является ROOT snapshot / operational base (где индексы могут быть частью базы ссылок).

По умолчанию (если нет явного разрешения) — ссылаемся на **целевые документы/сущности**, а не “на индекс ради индекса”.

---

## 2) REQUIRED HEADER (COPY AS BASE)
Ниже минимальный обязательный header-шаблон (копируй и заполни):

# <INDEX TITLE>

FILE: <path/to/file.md>
SCOPE: <scope text>
SERIAL: <optional volume serial if used>
LAYER: <layer name>
DOC_TYPE: INDEX
INDEX_TYPE: <ROOT | MASTER | LAYER | REALM | PROJECT | REGISTRY | OTHER>
LEVEL: <L0 | L1 | L2 | L3>
STATUS: <ACTIVE | DRAFT | DEPRECATED>
LOCK: <FIXED | OPEN>
VERSION: <semver>
UID: <canonical UID>
OWNER: <SYSTEM | team>
ROLE: <one-line role>
NAV_RULE: <Use RAW links only | UID-only | Snapshot RAW link base | other law-defined rule>

CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: <PATCH | MINOR | MAJOR>
- SUMMARY: "<short summary>"
- REASON: "<why>"
- IMPACT: "<impact>"
- CHANGE_ID: <id>

---

## 3) INDEX BODY TEMPLATE (REQUIRED SECTIONS)

### 3.1 PURPOSE (LAW)
Коротко:
- что индексирует;
- зачем нужен;
- что является “точкой входа” для чтения;
- какой NAV_RULE действует.

### 3.2 EXISTENCE RULE (ABSOLUTE | IF APPLICABLE)
Если этот INDEX является реестром существования для области, вставь этот блок:

- Если сущность/документ не зарегистрирован в этом INDEX — он не существует для этой области.
- Если файл есть физически, но не зарегистрирован — он NON-CANON / ignored.
- Исключения должны быть записаны явно.

Если INDEX не является existence registry — явно напиши: “EXISTENCE RULE: NOT APPLICABLE”.

### 3.3 SCOPE BOUNDARIES
- IN SCOPE: что входит
- OUT OF SCOPE: что не входит
- DEPENDENCIES (optional): внешние документы/слои, которые считаются источниками правил

### 3.4 NAVIGATION CONTRACT
- Как читать индекс (порядок)
- Как интерпретировать записи
- Что считается каноном (existence rule / lock rule)
- Какая политика ссылок (RAW/UID-only/snapshot)

### 3.5 CANON MAP (REGISTRY)
Главная часть индекса.

Рекомендуемый формат записи (читаемо человеком и машиной):

- ITEM: <human name>
  TYPE: <DOC | ENTITY | FOLDER | TEMPLATE | REGISTRY | OTHER>
  UID: <uid if exists, otherwise TBD>
  PATH_LABEL: <optional label, not navigation>
  RAW: <raw link if NAV_RULE allows or requires; otherwise omit>
  STATUS: <optional, if different from header>
  NOTES: <short usage hint>

Правила:
- Каждая запись — атомарная (одна сущность = одна запись).
- Длинные объяснения запрещены (для этого целевой документ).
- Если `NAV_RULE: UID-only` — поле `RAW` не использовать.

### 3.6 CHANGE CONTROL (REMINDER)
- Как обновляется индекс (через какой протокол)
- Что считается manual refresh (если индекс snapshot)
- Кто владелец изменения (OWNER / governance)

---

## 4) OPTIONAL SECTIONS (ONLY IF NEEDED)

### 4.1 ORDER / PRIORITY
Если индекс задаёт порядок:
- пронумеровать элементы
- кратко объяснить логику приоритета

### 4.2 DEPRECATION POINTERS
Если есть DEPRECATED элементы:
- REPLACED_BY_UID: <uid>
- REASON: <short>

### 4.3 VALIDATION CHECKLIST (PRE-COMMIT)
- [ ] header заполнен и единственный источник меты
- [ ] UID корректен
- [ ] NAV_RULE указан и соблюдён
- [ ] scope boundaries указаны
- [ ] existence rule указан (applicable / not applicable)
- [ ] PATH используется только как метка
- [ ] RAW ссылки есть только там, где разрешены/обязательны
- [ ] нет “index-to-index” ссылок без явного разрешения

---

## 5) MINI EXAMPLE (REFERENCE)
- ITEM: "DOC CONTROL STANDARD"
  TYPE: DOC
  UID: UE.STD.DOC_CONTROL.001
  PATH_LABEL: 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
  RAW: <insert RAW if NAV_RULE allows>
  NOTES: "Authority for doc headers and meta rules."

---

## 6) END
