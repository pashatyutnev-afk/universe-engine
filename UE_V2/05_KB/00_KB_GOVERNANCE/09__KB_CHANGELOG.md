# KB CHANGELOG — CENTRAL CHANGE LOG (KB)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/09__KB_CHANGELOG.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: LOG
INDEX_TYPE: CHANGELOG (KB)
LEVEL: L1
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.LOG.CHANGELOG.001
OWNER: SYSTEM
ROLE: Central auditable log of all changes in Knowledge Base; required for governance, memory safety, and one-index existence discipline

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Initialized KB central changelog with strict entry format and impact requirements."
- REASON: "KB is quality control plane; changes must be traceable and audit-friendly."
- IMPACT: "All KB edits become reviewable; VERIFIED modules remain memory-safe."
- CHANGE_ID: UE.CHG.2026-01-14.KB.LOG.001

---

## 0) PURPOSE (LAW)
Этот CHANGELOG — единый журнал изменений для `04_KNOWLEDGE_BASE`.

Зачем:
- контроль качества и дрейфа,
- audit trail (проверяемость),
- memory safety (VERIFIED модули),
- синхронизация с one-index existence rule (master-index).

Этот файл не является NAV/EXISTENCE индексом.

---

## 1) MANDATORY RULES
### 1.1 Every meaningful change is logged
Любое изменение KB, которое:
- меняет смысл,
- добавляет/удаляет файл,
- меняет версию/статус/lock,
- меняет шаблон/гейт/политику,
- меняет карту scope/validation/pipeline,
обязано иметь запись в этом журнале.

### 1.2 No silent edits
Запрещены изменения без записи.

### 1.3 One entry = one file change (recommended)
Рекомендуется: одна запись на один изменённый файл.
Если изменения пакетные — допускается “batch entry” с явным списком файлов.

---

## 2) ENTRY FORMAT (STRICT)
Каждая запись обязана содержать:

- DATE: YYYY-MM-DD
- FILE: PATH (один файл) или FILES: PATH list (если batch)
- CHANGE_TYPE: MAJOR | MINOR | PATCH | CREATE | DELETE | MOVE | RENAME | DEPRECATE
- VERSION: old -> new (если применимо)
- STATUS: old -> new (если применимо)
- LOCK: old -> new (если применимо)
- SUMMARY: кратко, конкретно
- REASON: почему это сделано
- IMPACT: кого затронуло (entities/pipelines/maps)
- REQUIRED_ACTIONS: что нужно обновить после изменения
- CHANGE_ID: уникальный идентификатор изменения

---

## 3) IMPACT RULES (MANDATORY)
### 3.1 Impact must mention affected systems
IMPACT обязан указать минимум одно:
- какие сущности должны обновить KB_SOURCES/KB_GATES
- какие пайплайны/карты scope должны быть пересмотрены
- какие тест-кейсы/примеры должны быть обновлены

### 3.2 VERIFIED module protection
Если изменён VERIFIED модуль:
- IMPACT обязан требовать пере-проверку
- module state должен быть пересмотрен (обычно VERIFIED → READ_ONCE до подтверждения)

---

## 4) REQUIRED_ACTIONS (MANDATORY)
Каждая запись должна содержать “что сделать дальше”.
Примеры:
- "Update KB master-index canon map RAW list"
- "Update TASK_TO_SCOPE_MAP"
- "Update entity KB connector: KB_SOURCES/KB_GATES"
- "Re-run validation test cases"
- "Mark module as DEPRECATED and add replacement path"

---

## 5) LOG ENTRIES
### 2026-01-14
- DATE: 2026-01-14
  FILE: 04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md
  CHANGE_TYPE: CREATE
  VERSION: N/A -> 1.0.0
  STATUS: N/A -> DRAFT
  LOCK: N/A -> OPEN
  SUMMARY: "Created KB master-index as single SoT for NAV/EXISTENCE + one-index operational mode."
  REASON: "Enable deterministic KB usage and prevent drift."
  IMPACT: "All KB files must be registered here to exist operationally."
  REQUIRED_ACTIONS: "Register all KB governance/pillars/topics/libraries/entities_kb/rel_xref entrypoints."
  CHANGE_ID: UE.CHG.2026-01-14.KB.IDX.001

- DATE: 2026-01-14
  FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/09__KB_CHANGELOG.md
  CHANGE_TYPE: CREATE
  VERSION: N/A -> 1.0.0
  STATUS: N/A -> DRAFT
  LOCK: N/A -> OPEN
  SUMMARY: "Initialized KB central changelog with strict entry format."
  REASON: "KB changes must be auditable."
  IMPACT: "All future KB edits must be logged here."
  REQUIRED_ACTIONS: "Use this entry format for every non-trivial KB change."
  CHANGE_ID: UE.CHG.2026-01-14.KB.LOG.001

---

## 6) TEMPLATE — COPY FOR NEW ENTRY
- DATE: YYYY-MM-DD
  FILE: <PATH>  # or FILES: <PATH1>; <PATH2>; ...
  CHANGE_TYPE: <MAJOR|MINOR|PATCH|CREATE|DELETE|MOVE|RENAME|DEPRECATE>
  VERSION: <old> -> <new>  # if applicable
  STATUS: <old> -> <new>   # if applicable
  LOCK: <old> -> <new>     # if applicable
  SUMMARY: "<what changed>"
  REASON: "<why>"
  IMPACT: "<who/what is affected>"
  REQUIRED_ACTIONS: "<what must be updated next>"
  CHANGE_ID: <unique id>

--- END.
