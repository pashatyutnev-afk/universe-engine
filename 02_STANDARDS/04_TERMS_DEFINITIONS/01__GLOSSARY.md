# GLOSSARY (TERMS & DEFINITIONS)
FILE: 02_STANDARDS/04_TERMS_DEFINITIONS/01__GLOSSARY.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: TERMS
INDEX_TYPE: GLOSSARY
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.STD.TERMS.GLOSSARY.001
OWNER: SYSTEM
ROLE: Canonical glossary (single source of truth for term meanings used across the system)

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Глоссарий нормализован: Doc Control + нумерация (NN__) + каноническая структура"
- REASON: "Все термины должны иметь единую точку истины, иначе канон расползается"
- IMPACT: "Унифицирует язык всей документации"

---

## 0) PURPOSE (LAW)
Этот файл фиксирует значения терминов Universe Engine.
Если термин определён здесь — это его каноническое значение.

Правило:
- Один термин → одно определение.
- Любая система/стандарт/движок обязаны использовать эти термины или давать XREF/REL.

---

## 1) TERM FORMAT (STANDARD)
Каждый термин оформляется так:

- **TERM:** <название>
  - **DEFINITION:** <строгое определение>
  - **SCOPE:** <где применяется>
  - **NOT:** <что этим не является>
  - **XREF:** [<UID/PATH>, ...]

---

## 2) CORE TERMS (FOUNDATION)

- **TERM:** CANON
  - **DEFINITION:** Набор документов/правил/артефактов, зарегистрированных в master-index слоя и соответствующих Doc Control.
  - **SCOPE:** Все слои.
  - **NOT:** “лежит в репо значит канон”.
  - **XREF:** []

- **TERM:** NON-CANON
  - **DEFINITION:** Любой файл/смысл, который существует физически, но не зарегистрирован в master-index слоя или нарушает Doc Control.
  - **SCOPE:** Все слои.
  - **NOT:** “плохой контент” — это просто вне канона.
  - **XREF:** []

- **TERM:** SoT (Single Source of Truth)
  - **DEFINITION:** Единственный документ, которому принадлежит смысл/правило. Всё остальное только ссылается, не копирует.
  - **SCOPE:** Законы/стандарты/реестры.
  - **NOT:** “копия SoT”.
  - **XREF:** []

- **TERM:** INDEX (Master / Registry)
  - **DEFINITION:** Каноническая навигационная точка: фиксирует состав/порядок/существование.
  - **SCOPE:** Слои и подсистемы.
  - **NOT:** “просто список ссылок”.
  - **XREF:** []

- **TERM:** REGISTRY
  - **DEFINITION:** Учётная ведомость сущностей/документов: UID/версии/статусы/связи.
  - **SCOPE:** Слои и подсистемы.
  - **NOT:** existence law (это роль master-index).
  - **XREF:** []

- **TERM:** UID
  - **DEFINITION:** Уникальный идентификатор сущности/документа в системе. Не меняется при переименованиях (если не MAJOR-замена).
  - **SCOPE:** Все слои.
  - **NOT:** путь файла.
  - **XREF:** []

- **TERM:** SemVer
  - **DEFINITION:** Версионирование X.Y.Z (MAJOR.MINOR.PATCH).
  - **SCOPE:** Все канонические документы.
  - **NOT:** “1.0”.
  - **XREF:** []

- **TERM:** STATUS
  - **DEFINITION:** Состояние документа: DRAFT / ACTIVE / DEPRECATED / ARCHIVED.
  - **SCOPE:** Все канонические документы.
  - **NOT:** “внизу файла повторить статус”.
  - **XREF:** []

- **TERM:** LOCK
  - **DEFINITION:** Режим изменения: OPEN (можно править) / FIXED (канон, только через протоколы).
  - **SCOPE:** Все канонические документы.
  - **NOT:** “несколько LOCK в файле”.
  - **XREF:** []

- **TERM:** ALIAS_POINTER
  - **DEFINITION:** Legacy-файл-указатель после переименования/переноса: содержит только ссылку на новый канон-путь.
  - **SCOPE:** Миграции.
  - **NOT:** “второй источник истины”.
  - **XREF:** []

---

## 3) TERMS TO EXTEND (QUEUE)
Добавлять по мере появления:
- ENTITY / ENTITY_TYPE / ENTITY_GROUP
- LAYER / REALM / FAMILY
- ENGINE / ORCHESTRATOR / SPECIALIST / VALIDATOR / QA
- REL / XREF
- PIPELINE / STEP / ARTIFACT
- S0–S3 PRIORITY

---

## FINAL RULE (LOCK)
LOCK: FIXED
--- END.
