# KB DOC CONTROL — VERSIONING / STATUS / CHANGE DISCIPLINE (KB)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/08__KB_DOC_CONTROL.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: SPEC
INDEX_TYPE: DOC_CONTROL_STANDARD (KB)
LEVEL: L1
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPEC.DOC_CONTROL.001
OWNER: SYSTEM
ROLE: Define KB-specific doc control: status/lock/version rules, change notes, review gates, and impact logging compatible with one-index existence and source-lock

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created KB Doc Control standard: SemVer, statuses, lock policy, mandatory change notes, KB changelog entries, and impact notes."
- REASON: "KB is quality control plane; uncontrolled changes break determinism and memory safety."
- IMPACT: "KB changes become auditable; VERIFIED modules become reliable for Memory-OK; drift prevented."
- CHANGE_ID: UE.CHG.2026-01-14.KB.DOCCTL.001

---

## 0) PURPOSE (LAW)
KB управляет качеством контента. Поэтому любые изменения KB должны быть:
- контролируемыми,
- аудируемыми,
- совместимыми с запретом фантазии (source-lock),
- совместимыми с one-index existence rule.

Этот документ задаёт правила версий/статусов/заморозки/изменений для всех KB файлов.

---

## 1) ABSOLUTE PRINCIPLES
### 1.1 One-index existence reminder
Существование KB файла определяется только master-index.
Любое добавление/переименование требует синхронизации master-index.

### 1.2 No silent drift
Запрещены “тихие правки” без change note и без записи в KB_CHANGELOG.

### 1.3 Memory safety
Модули, которые используются “по памяти”, должны быть VERIFIED.
Изменение VERIFIED модуля требует пересмотра его статуса (см. module states).

---

## 2) STATUS POLICY (KB DOC STATUS)
### 2.1 Allowed statuses
Используются статусы (минимальный набор):
- DRAFT — документ в разработке, не считается стабильным
- ACTIVE — документ рабочий и применяется
- DEPRECATED — документ устарел, использовать нельзя (только как историческую справку)

Правила:
- DRAFT может часто меняться, но всё равно должен иметь change note.
- ACTIVE требует управляемых изменений (semver + changelog + impact).
- DEPRECATED должен указывать replacement (что использовать вместо).

---

## 3) LOCK POLICY (FREEZE CONTROL)
### 3.1 Allowed locks
- OPEN — правки разрешены в рамках change control
- FIXED — документ заморожен (изменения только через канон-процедуру)

Рекомендация:
- Governance документы, задающие законы, после стабилизации переводятся в FIXED.
- Master-index после стабилизации переводится в FIXED.

---

## 4) VERSION POLICY (SEMVER REQUIRED)
### 4.1 SemVer format (mandatory)
VERSION: `MAJOR.MINOR.PATCH`

### 4.2 When to bump versions
- PATCH: исправление формулировок без изменения смысла/контрактов
- MINOR: добавление новых секций/модулей/правил без ломания обратной совместимости
- MAJOR: изменение контракта, структуры, правил или поведения гейтов

### 4.3 Version stability
VERSION фиксируется в шапке документа. Любое изменение версии требует записи в CHANGE_NOTE.

---

## 5) CHANGE NOTE (MANDATORY HEADER BLOCK)
Каждый KB документ должен иметь в шапке блок CHANGE_NOTE.

Минимальные поля для записи:
- DATE
- TYPE (MAJOR/MINOR/PATCH)
- SUMMARY
- REASON
- IMPACT
- CHANGE_ID

Правило:
- CHANGE_NOTE обновляется при каждом изменении документа (добавляется новая запись или обновляется “последняя запись” по вашей практике).
- Любая запись должна быть конкретной и проверяемой.

---

## 6) KB CHANGELOG (CENTRAL LOG)
Все изменения KB должны отражаться в:
- `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/09__KB_CHANGELOG.md`

Минимальный формат записи:
- DATE
- FILE (PATH)
- CHANGE TYPE
- VERSION (old → new)
- SUMMARY
- IMPACT (кто затронут: сущности/пайплайны/карты)
- CHANGE_ID

---

## 7) IMPACT NOTE (MANDATORY FOR NON-TRIVIAL CHANGES)
Impact note обязателен, если:
- изменён смысл правила,
- изменён gate/рубрика,
- изменён scope map / validation matrix,
- изменён template (output contract),
- изменён VERIFIED модуль.

Impact note должен указать:
- какие сущности должны обновить KB_SOURCES/KB_GATES,
- какие пайплайны должны быть пересмотрены,
- какие тест-кейсы/примеры должны быть обновлены.

---

## 8) MODULE STATE SYSTEM (OPERATIONAL)
KB модули имеют operational state:
- UNREAD
- READ_ONCE
- VERIFIED
- DEPRECATED

Правило:
- VERIFIED можно использовать по памяти (Memory-OK) без искажений.
- Любое существенное изменение VERIFIED → временно переводит его в READ_ONCE до повторной валидации применением.

---

## 9) REVIEW GATES (QUALITY CONTROL)
### 9.1 Minimal review for ACTIVE
Перед переводом в ACTIVE модуль должен иметь:
- применимость (procedure/checklist/rubric)
- примеры PASS/FAIL (и EDGE если нужно)
- корректные PATH links (REL/XREF)
- отсутствие фантазии (source-lock)

### 9.2 Promotion to VERIFIED
Модуль может стать VERIFIED, если:
- использовался в реальной работе минимум N раз (N задаётся в KB policy или в практике команды),
- не привёл к противоречиям,
- имеет тест-кейсы/примеры и они согласованы с usage gate.

---

## 10) DEPRECATION RULES
Если модуль устарел:
- STATUS: DEPRECATED
- module state: DEPRECATED
- обязательно указать replacement:
  - PATH: <new module>
- обновить master-index и карты, чтобы не было “битых маршрутов”.

---

## 11) COMPLIANCE CHECK (FAST)
KB Doc Control соблюдён, если:
- SemVer корректен
- статус из allowed set
- lock определён
- есть change note
- изменения отражены в KB_CHANGELOG
- impact note добавлен (если нужно)
- VERIFIED модули защищены от тихих правок

--- END.
