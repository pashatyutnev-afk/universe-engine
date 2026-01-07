# DOC CONTROL STANDARD (SoT) — CANON HEADER + METADATA LAW
FILE: 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: STANDARD
STANDARD_TYPE: DOC_CONTROL
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.2.0
UID: UE.STD.DOC_CONTROL.SOT.001
OWNER: SYSTEM
ROLE: Single source of truth for canonical document header format, required metadata, allowed values, and anti-duplication rules across all layers

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MINOR
- SUMMARY: "Зафиксирован единый машиночитаемый формат шапки, список обязательных/разрешённых полей, SemVer enforcement, запрет дублей метаданных вне шапки"
- REASON: "Усилить фундамент: единый формат канона для индексов/реестров/шаблонов/сущностей"
- IMPACT: "Все канонические документы обязаны соответствовать"

---

## 0) PURPOSE (SoT)
Этот стандарт определяет **единую каноническую форму документа** Universe Engine.

Он фиксирует:
- единый формат шапки (header)
- обязательные и разрешённые поля
- допустимые множества значений (STATUS/LOCK)
- строгий формат версии (SemVer)
- запрет дублей метаданных вне шапки
- минимальные правила “каноничности” (валидность формы)

Если документ не соответствует этому стандарту — он считается **NON-CANON** до исправления.

---

## 1) CANON HEADER FORMAT (HARD LAW)

### 1.1 Header block (mandatory)
Шапка документа — это набор строк формата:

`KEY: VALUE`

Правила:
- один пробел после двоеточия `:`
- KEY — только `A-Z`, `0-9`, `_`
- VALUE — любая строка без управляющих символов

### 1.2 Placement (mandatory)
- Шапка обязана идти **сразу после первой строки заголовка `# ...`**
- После шапки — пустая строка и дальше контент

### 1.3 Single source of truth (hard)
Поля `STATUS`, `LOCK`, `VERSION`, `UID`, `OWNER` **должны существовать только в шапке**.

Запрещено:
- повторять эти поля внизу файла отдельными строками
- включать вторые “STATUS/LOCK/VERSION” в блоках `FINAL RULE`, `FOOTER`, `META`, и т.п.

Если дубли обнаружены → документ **NON-CANON**.

---

## 2) REQUIRED FIELDS (STRICT SET)
Каждый канонический документ обязан иметь следующие поля шапки:

- `SCOPE:`
- `LAYER:`
- `STATUS:`
- `LOCK:`
- `VERSION:`
- `UID:`
- `OWNER:`
- `ROLE:`

Отсутствие любого из REQUIRED полей → документ **NON-CANON**.

---

## 3) OPTIONAL FIELDS (WHITELIST)
Допускаются только следующие optional-поля (по необходимости):

- `DOC_TYPE:` (см. §5)
- `INDEX_TYPE:` (если документ — индекс/реестр)
- `STANDARD_TYPE:` (если документ — стандарт/спека)
- `ENTITY_GROUP:` (если документ описывает класс сущностей)
- `ENTITY_CLASS:` (ENG/ORC/SPC/CTL/VAL/QA/KB/PRJ/AST/DB/LOG)
- `LEVEL:` (L0..L5 — если используется уровневость)
- `TAGS:` (comma-separated)
- `RELATES_TO:` (список UID через запятую)
- `CANON_PATH:` (канонический путь в репозитории)
- `RAW:` (raw-ссылка для чтения без репозитория)
- `CHANGE_NOTE:` (блок изменений; обязателен для L1 master-index и system laws)

Любые другие поля запрещены, пока не добавлены в этот whitelist через Canon Protocol.

---

## 4) STATUS / LOCK (STRICT VALUES)

### 4.1 STATUS allowed (global)
Допускаются только:
- `STATUS: DRAFT`
- `STATUS: ACTIVE`
- `STATUS: DEPRECATED`
- `STATUS: ARCHIVED`

### 4.2 LOCK allowed (global)
Допускаются только:
- `LOCK: OPEN`
- `LOCK: FIXED`

---

## 5) DOC TYPE TAXONOMY (STRICT)
Поле `DOC_TYPE:` (если используется) допускается только из множества:

- `DOC_TYPE: LAW`
- `DOC_TYPE: STANDARD`
- `DOC_TYPE: INDEX`
- `DOC_TYPE: TEMPLATE`
- `DOC_TYPE: ENTITY`
- `DOC_TYPE: REGISTRY`
- `DOC_TYPE: PROTOCOL`
- `DOC_TYPE: GUIDE`
- `DOC_TYPE: LOG`

Если нужен новый тип — сначала добавляется сюда через Canon Protocol.

---

## 6) VERSION FORMAT (SemVer HARD)
`VERSION:` должен быть строго в формате SemVer:

`X.Y.Z`

Где:
- `X` — MAJOR
- `Y` — MINOR
- `Z` — PATCH

Запрещено:
- `1.0`
- `4.1`
- `v1.2.3`

---

## 7) MINIMUM CANON VALIDATION (GATES)
Документ считается каноничным по форме, если:
1) соблюдён формат шапки (§1)
2) присутствуют все REQUIRED поля (§2)
3) значения STATUS/LOCK валидны (§4)
4) VERSION валиден SemVer (§6)
5) отсутствуют дубли метаданных вне шапки (§1.3)

---

## 8) MIGRATION RULE
Любой документ без шапки, без SemVer, без UID или с дублями метаданных — **NON-CANON** до нормализации.
Нормализация проходит через:
- Canon Protocol
- Versioning & Change Policy
- Audit Log (если требуется governance)

---

## FINAL RULE (LOCK)
LOCK: FIXED
--- END.
