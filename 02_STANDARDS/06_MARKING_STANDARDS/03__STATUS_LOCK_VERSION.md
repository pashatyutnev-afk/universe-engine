# STATUS / LOCK / VERSION — STANDARD
FILE: 02_STANDARDS/06_MARKING_STANDARDS/03__STATUS_LOCK_VERSION.md

SCOPE: Universe Engine / Documentation
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Единые правила статуса, замка и версий для всех документов.

SOURCE OF TRUTH:
- STATUS/LOCK/VERSION описаны здесь.

---

## 0) CORE LAW
- В документе допускается один набор полей STATUS/LOCK/VERSION в шапке.
- Дубли в конце файла запрещены.

---

## 1) STATUS (single)
Допустимые значения:
- ACTIVE
- DRAFT
- DEPRECATED
- ARCHIVED

Правило:
- ACTIVE = используется системой
- DRAFT = в разработке
- DEPRECATED = не использовать, есть замена
- ARCHIVED = историческое, не менять

---

## 2) LOCK (single)
- LOCK: OPEN — можно править
- LOCK: FIXED — канон зафиксирован (правится только через Change Management)

---

## 3) VERSION (semver-lite)
Формат:
- VERSION: 1.0 / 1.1 / 2.0

Правило:
- 0.1..0.9 — ранняя разработка (если хотите)
- MINOR — уточнения без смены структуры
- MAJOR — смена структуры/контракта/формата

---

## 4) REQUIRED HEADER (minimum)
Каждый документ обязан иметь:
- FILE
- SCOPE
- LEVEL
- STATUS
- LOCK
- VERSION
- OWNER
- ROLE

Контроль — DOC_CONTROL (см. 08__DOC_CONTROL.md)

---
END.
