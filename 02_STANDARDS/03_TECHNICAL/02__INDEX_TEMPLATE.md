FILE: 02_STANDARDS/03_TECHNICAL/02__INDEX_TEMPLATE.md
SCOPE: Universe Engine
LAYER: 02_STANDARDS/03_TECHNICAL
DOC_TYPE: TEMPLATE
TEMPLATE_TYPE: INDEX
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.INDEX.001
OWNER: SYSTEM
ROLE: Single canonical template for creating and maintaining any INDEX document in Universe Engine.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Converted from alias-pointer loop into real canonical INDEX template (SoT). Header aligned to DOC CONTROL. Added strict anti-duplication, RAW-only, and index content rules."
- REASON: "Self-referencing alias invalidates template existence and breaks auditable indexing."
- IMPACT: "All indexes can be generated deterministically from one stable template."
- CHANGE_ID: UE.CHG.2026-01-20.TPL.INDEX.001

---

## 0) PURPOSE (LAW)
Этот TEMPLATE задаёт единственный канонический формат для любых INDEX документов системы.

INDEX документ предназначен для:
- навигации и фиксации состава (existence registry) внутри области;
- правил порядка и приоритета;
- ссылки на допустимые ресурсы (если разрешено правилами слоя);
- служит “точкой входа” для чтения, но **не выполняет задач** (кроме ENTRYPOINT/RUNBOOK документов, которые имеют отдельный DOC_TYPE).

---

## 1) ABSOLUTE RULES (MUST)

### 1.1 Header truth (ABSOLUTE)
- Вся документная мета (STATUS/LOCK/VERSION/UID/OWNER/ROLE/FILE и т.д.) живёт **только в header**.
- Запрещено повторять метаданные ниже шапки (никаких “FINAL RULE (LOCK) LOCK: …” и аналогов).

### 1.2 RAW-only navigation
- Если в системе активен режим RAW-only, любые ссылочные переходы выполняются только по RAW.
- Запрещено угадывать пути.

### 1.3 Index scope discipline
- INDEX должен явно описывать **границы области**: что индексирует, что не индексирует.
- INDEX не должен содержать “выполнение задач” (это зона ENTRYPOINT/RUNBOOK).

### 1.4 No “index-to-index” link spam (STRICT)
- Внутри INDEX по умолчанию **не размещать ссылки на другие INDEX документы**.
- Если нужно сослаться на другой INDEX: использовать **UID-only reference** (без ссылки), либо ссылаться на конечный документ/сущность (не на индекс).
- Исключение возможно только если отдельный LAW слоя явно разрешает index-to-index navigation.

---

## 2) REQUIRED HEADER (COPY AS BASE)
Ниже минимальный обязательный header-шаблон. Заполни значения под документ:

# <INDEX TITLE>

FILE: <path/to/file.md>
SCOPE: <scope text>
SERIAL: <optional volume serial if used>
LAYER: <layer name>
DOC_TYPE: INDEX
INDEX_TYPE: <ROOT | MASTER | LAYER | REALM | PROJECT | REGISTRY | OTHER>
LEVEL: <L0-L3 or L1 etc>
STATUS: <ACTIVE | DRAFT | DEPRECATED>
LOCK: <FIXED | OPEN>
VERSION: <semver>
UID: <canonical UID>
OWNER: <SYSTEM | team>
ROLE: <one-line role>
NAV_RULE: <Use RAW links only | UID-only | other rule if law defines>

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
    
- какой это уровень/роль.
    

### 3.2 EXISTENCE RULE (ABSOLUTE)

Обязательный блок, если INDEX отвечает за “существование”:

- Если сущность/документ не зарегистрирован в этом INDEX — он не существует для этой области.
    
- Если файл существует физически, но не зарегистрирован — он NON-CANON/ignored.
    
- Любые исключения должны быть записаны явно.
    

### 3.3 SCOPE BOUNDARIES

- IN SCOPE: что входит
    
- OUT OF SCOPE: что не входит
    
- OPTIONAL: зависимости (какие документы/слои считаются внешними)
    

### 3.4 NAVIGATION CONTRACT

- Как читать индекс (порядок)
    
- Как интерпретировать записи
    
- Что считается каноном
    

### 3.5 CANON MAP (REGISTRY)

Главная часть индекса.

Формат записи (рекомендуемый, читаемый машиной и человеком):

```
- ITEM: <human name>
  TYPE: <DOC | ENTITY | FOLDER | TEMPLATE | REGISTRY | OTHER>
  UID: <uid if exists, otherwise TBD>
  PATH_LABEL: <optional label, not a navigation mechanism>
  RAW: <raw link if allowed by scope rules>
  STATUS: <optional, if different from doc header rules>
  NOTES: <short reason or usage hint>
```

Правила:

- Каждая запись — атомарная.
    
- Никаких длинных описаний в индексе. Если надо — ссылка на целевой документ.
    
- Если RAW запрещён правилами области — использовать `UID` без ссылки.
    

### 3.6 CHANGE CONTROL (REMINDER)

- Как обновляется индекс
    
- Через какой протокол
    
- Что считается “manual refresh” если индекс snapshot
    

---

## 4) OPTIONAL SECTIONS (ONLY IF NEEDED)

### 4.1 ORDER / PRIORITY

Если индекс задаёт порядок применения:

- пронумеровать
    
- кратко объяснить приоритет
    

### 4.2 DEPRECATION POINTERS

Если есть DEPRECATED элементы:

- указывать `REPLACED_BY_UID`
    
- давать краткую причину
    

### 4.3 VALIDATION CHECKLIST

Мини-чек перед коммитом:

- header заполнен
    
- UID корректен
    
- нет дублей меты в теле
    
- scope boundaries указаны
    
- нет ссылок “на индексы ради индексов” (по умолчанию)
    

---

## 5) INDEX MINI EXAMPLE (REFERENCE)

Пример одной записи:

- ITEM: "DOC CONTROL STANDARD"  
    TYPE: DOC  
    UID: UE.STD.DOC_CONTROL.001  
    PATH_LABEL: 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md  
    RAW:  
    NOTES: "Authority for doc headers and meta rules."
    

---

## 6) END