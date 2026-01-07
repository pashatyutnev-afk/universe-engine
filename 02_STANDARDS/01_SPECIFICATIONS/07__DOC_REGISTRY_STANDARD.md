# DOC REGISTRY STANDARD (SoT) (CANON)
FILE: 02_STANDARDS/01_SPECIFICATIONS/07__DOC_REGISTRY_STANDARD.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: SPEC
SPEC_TYPE: SoT
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.STD.SPEC.DOC_REGISTRY.107
OWNER: SYSTEM
ROLE: Source-of-Truth specification for document registries: defines required registry fields, enums, compliance states, and how layer registries link to master-indexes.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Нормализован Doc Registry SoT: контракт реестров, поля таблицы, compliance enum, правила связки с master-index"
- REASON: "Нужен единый формат реестров по слоям и контроль канона"
- IMPACT: "All layer registries, indices, validation tooling"

---

## 0) PURPOSE (LAW)
Этот документ — SoT-спека о том:
- что такое Doc Registry (реестр документов слоя),
- какие поля реестр обязан содержать,
- какие значения допускаются (enums),
- как реестр связан с master-index слоя,
- как отмечать compliance и миграции.

---

## 1) AUTHORITY & XREF (UID-first)
Primary authority:
- `01_SYSTEM_LAW/06__CONSTRAINTS_REGISTRY.md`
- `02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md`
- `02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md`

XREF:
- XREF: UE.REG.CONSTRAINTS.MASTER.006 | governs | existence/number collision/SoT rules | 01_SYSTEM_LAW/06__CONSTRAINTS_REGISTRY.md
- XREF: UE.STD.SPEC.DOC_CONTROL.103 | depends_on | header and compliance definition | 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
- XREF: UE.STD.SPEC.REL_XREF.104 | depends_on | UID-first cross references | 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md

---

## 2) DEFINITIONS
- **Master-Index** — единственная точка входа в слой. Определяет существование документов слоя.
- **Doc Registry** — инвентаризация и контроль качества документов слоя.
- **Registry Record** — строка реестра (один документ).
- **DOC_UID** — UID документа (обязателен).
- **COMPLIANCE** — состояние соответствия законам (см. enum ниже).

---

## 3) PRIME RULES (ABSOLUTE)
### 3.1 Registry is not the existence law
Существование документа определяется master-index слоя, а не реестром.

Реестр:
- подтверждает состав
- контролирует качество/соответствие

### 3.2 UID-first
Каждая строка реестра обязана содержать `DOC_UID`.

### 3.3 No duplicates
Два документа не могут иметь один `DOC_UID`.

---

## 4) REGISTRY TABLE CONTRACT (REQUIRED COLUMNS)
Минимальный обязательный набор колонок:

1) `DOC_UID`
2) `DOC_TYPE`
3) `TITLE`
4) `STATUS`
5) `LOCK`
6) `COMPLIANCE`
7) `TARGET_VERSION`
8) `PATH`

Допустимые расширения (опционально):
- `ROLE` (коротко роль документа)
- `DEPRECATED_BY` (если STATUS=DEPRECATED)
- `NOTES` (короткие пояснения)
- `XREF` (если нужно указать ключевые связи)

---

## 5) CONTROLLED ENUMS
### 5.1 DOC_TYPE (recommended)
- INDEX
- REGISTRY
- LAW
- LAW_PROTOCOL
- SPEC
- MODULE
- PROTOCOL
- TEMPLATE
- TERMS
- REQUIREMENTS
- GUIDE
- ARTIFACT (если реестр включает не только документы-правила)

### 5.2 STATUS enum (must align with Doc Control)
- ACTIVE
- DEPRECATED
- ARCHIVED
- DRAFT (только если реестр учитывает черновики; по умолчанию в канонических реестрах DRAFT не включаем)

### 5.3 LOCK enum
- FIXED
- OPEN (по умолчанию OPEN не включается в канонический слой-реестр)

### 5.4 COMPLIANCE enum
- `OK` — документ соответствует законам (header/UID/SemVer/Naming/Constraints)
- `PENDING` — документ в каноне, но требует нормализации
- `INVALID` — документ нарушает S0 constraint (канон не может быть зафиксирован)

---

## 6) COMPLIANCE EVALUATION RULES
### 6.1 OK criteria (minimum)
COMPLIANCE = OK только если:
- Doc Control header присутствует и валиден
- UID в шапке = DOC_UID из реестра
- VERSION SemVer валиден
- Naming Rules соблюдены (или есть approved exception)
- нет коллизий номера/индекса/дублей SoT
- документ зарегистрирован в master-index слоя

### 6.2 PENDING meaning
PENDING = документ зарегистрирован и считается каноном, но ещё требует:
- добавления UID/шапки/semver
- или переименования по Naming
- или приведения XREF/REL

### 6.3 INVALID meaning
INVALID = нарушение S0 constraint:
- UID отсутствует/дубликат
- коллизия `NN*` в папке
- два entrypoint индекса
- дубли SoT смысла

INVALID блокирует Canon merge до исправления.

---

## 7) LAYER REGISTRY RULES
Каждый слой может иметь свой Doc Registry (L1), но:
- он должен быть зарегистрирован в master-index слоя
- должен соответствовать этому стандарту (колонки + enum)
- должен ссылаться на master-index слоя в Purpose/How to use

---

## 8) MIGRATION TRACKING (STANDARD)
Если документ в реестре требует исправления, фиксируется:
- `COMPLIANCE: PENDING`
- `TARGET_VERSION` (к чему приводим)
- `NOTES` (коротко что сделать)

После исправления:
- COMPLIANCE → OK
- версия документа bump по Versioning Policy

---

## 9) EXAMPLES (MINIMAL)
Пример минимальной строки:

| DOC_UID | DOC_TYPE | TITLE | STATUS | LOCK | COMPLIANCE | TARGET_VERSION | PATH |
|---|---|---|---|---|---|---|---|
| UE.STD.SPEC.DOC_CONTROL.103 | SPEC | Doc Control Standard (SoT) | ACTIVE | FIXED | OK | 1.1.0 | 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md |

---

## FINAL RULE (LOCK)
Doc Registry Standard — SoT для всех реестров документов.
Любое изменение обязательных колонок/enum = MAJOR по умолчанию.
--- END.
