# DOC CONTROL (MARKING MODULE) (CANON)
FILE: 02_STANDARDS/06_MARKING_STANDARDS/08__DOC_CONTROL.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: MODULE
MODULE_TYPE: MARKING
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.STD.MOD.MARKING.DOC_CONTROL.608
OWNER: SYSTEM
ROLE: Marking module providing practical Doc Control header patterns for common document types (INDEX/SPEC/MODULE/PROTOCOL/TEMPLATE/TERMS/REGISTRY) and legacy alias pointers. Extends Doc Control SoT.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Модуль Doc Control: готовые header-шапки для типов документов + правила alias pointers, без дублей контента"
- REASON: "Ускорить создание канона и убрать ошибки шапок"
- IMPACT: "All canon docs and migrations"

---

## XREF (UID-first)
XREF: UE.STD.SPEC.DOC_CONTROL.103 | extends | practical header patterns | 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
XREF: UE.STD.MOD.MARKING.STORAGE_MAP.602 | references | alias pointers policy | 02_STANDARDS/06_MARKING_STANDARDS/02__STORAGE_MAP.md
XREF: UE.STD.MOD.MARKING.STATUS_LOCK_VERSION.603 | references | status/lock/version clarity | 02_STANDARDS/06_MARKING_STANDARDS/03__STATUS_LOCK_VERSION.md

---

## 0) PURPOSE
Этот модуль даёт:
- готовые “копипаст” шапки Doc Control для основных типов документов
- минимальные правила “что обязательно”
- как оформить legacy alias pointer файл корректно

---

## 1) GENERAL HEADER RULES (PRACTICAL)
Обязательный минимум для канона:
- FILE
- SCOPE
- LAYER
- DOC_TYPE
- LEVEL
- STATUS
- LOCK
- VERSION
- UID
- OWNER
- ROLE
- CHANGE_NOTE (last change)

Рекомендации:
- не добавлять в header “лишние поля” если не нужны
- если документ INDEX — явно указывать `INDEX_TYPE`
- если документ SPEC — указывать `SPEC_TYPE`
- если документ MODULE — указывать `MODULE_TYPE`

---

## 2) COPY HEADERS (READY TO USE)

### 2.1 INDEX (MASTER/SUB)
FILE: <path>
SCOPE: Universe Engine
LAYER: <layer>
DOC_TYPE: INDEX
INDEX_TYPE: <MASTER|SUB|REGISTRY_INDEX|MAP|REQUIREMENTS_ROOT>
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: <UID>
OWNER: SYSTEM
ROLE: Canonical entrypoint / navigation law

CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR
- SUMMARY: "..."
- REASON: "..."
- IMPACT: "..."

---

### 2.2 SPEC (SoT)
FILE: <path>
SCOPE: Universe Engine
LAYER: <layer>
DOC_TYPE: SPEC
SPEC_TYPE: SoT
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: <UID>
OWNER: SYSTEM
ROLE: Source-of-Truth specification

CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR
- SUMMARY: "..."
- REASON: "..."
- IMPACT: "..."

---

### 2.3 MODULE
FILE: <path>
SCOPE: Universe Engine
LAYER: <layer>
DOC_TYPE: MODULE
MODULE_TYPE: <MARKING|...>
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: <UID>
OWNER: SYSTEM
ROLE: Module that extends a SoT spec

CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR
- SUMMARY: "..."
- REASON: "..."
- IMPACT: "..."

---

### 2.4 PROTOCOL
FILE: <path>
SCOPE: Universe Engine
LAYER: <layer>
DOC_TYPE: PROTOCOL
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: <UID>
OWNER: SYSTEM
ROLE: Operational protocol

CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR
- SUMMARY: "..."
- REASON: "..."
- IMPACT: "..."

---

### 2.5 TEMPLATE
FILE: <path>
SCOPE: Universe Engine
LAYER: <layer>
DOC_TYPE: TEMPLATE
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: <UID>
OWNER: SYSTEM
ROLE: Canonical copy template

CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR
- SUMMARY: "..."
- REASON: "..."
- IMPACT: "..."

---

### 2.6 TERMS
FILE: <path>
SCOPE: Universe Engine
LAYER: <layer>
DOC_TYPE: TERMS
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: <UID>
OWNER: SYSTEM
ROLE: Canonical glossary/definitions

CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR
- SUMMARY: "..."
- REASON: "..."
- IMPACT: "..."

---

### 2.7 REGISTRY
FILE: <path>
SCOPE: Universe Engine
LAYER: <layer>
DOC_TYPE: REGISTRY
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: <UID>
OWNER: SYSTEM
ROLE: Canonical registry for <scope>

CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR
- SUMMARY: "..."
- REASON: "..."
- IMPACT: "..."

---

## 3) LEGACY ALIAS POINTER (NON-CANON CONTENT) — REQUIRED FORMAT
Alias pointer файл не содержит стандарт, а только указатель.

### 3.1 Header (alias pointer)
FILE: <legacy-path>
SCOPE: Universe Engine
LAYER: <layer>
DOC_TYPE: ARTIFACT
ARTIFACT_TYPE: LEGACY_ALIAS_POINTER
LEVEL: L2
STATUS: DEPRECATED
LOCK: FIXED
VERSION: 1.0.0
UID: <UID for this pointer file>
OWNER: SYSTEM
ROLE: Legacy alias pointer to canonical document

CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR
- SUMMARY: "Created alias pointer"
- REASON: "Migration / naming collision / legacy compatibility"
- IMPACT: "Old links redirect to canon"

CANON_TARGET_UID: <UID_CANON>
CANON_TARGET: <path-to-canon>

### 3.2 Body (alias pointer)
THIS FILE IS A LEGACY ALIAS POINTER (NON-CANON CONTENT).

CANON TARGET:
- UID: <UID_CANON>
- PATH: <path-to-canon>

XREF:
- XREF: <UID_CANON> | non_canon_alias_of | legacy alias pointer | <path-to-canon>

---

## 4) COMMON FAILURES (ANTI-PATTERNS)
Запрещено:
- “второй INDEX” как альтернативный entrypoint (делай alias pointer)
- “контент стандарта” внутри alias pointer файла
- UID отсутствует или не SemVer
- смешивать doc STATUS с entity status

---

## FINAL RULE (LOCK)
Этот модуль расширяет Doc Control SoT и задаёт практику шапок/alias pointers.
Изменение обязательных header полей = MAJOR по умолчанию.
--- END.
