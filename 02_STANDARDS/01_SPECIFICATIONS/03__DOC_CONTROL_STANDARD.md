# DOC CONTROL STANDARD (CANON)
FILE: 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: SPEC
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.3.0
UID: UE.STD.SPEC.DOC_CONTROL.001
OWNER: SYSTEM
ROLE: Doc header + lifecycle + anti-dup rules + strict single-index compatibility

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: PATCH
- SUMMARY: "FILE field explicitly allowed. Absolute ban on footer meta duplication. Added strict single-index mode clause."
- REASON: "Убрать конфликт: FILE используется в шапках, а стандарт его не признавал; запретить 'LOCK внизу'."
- IMPACT: "Doc Control больше не может противоречить сам себе."

---

## 0) PURPOSE (LAW)
Этот стандарт определяет:
- обязательную шапку документа (Doc Control header)
- правила статусов/локов/версий
- запрет на дубли метаданных вне шапки
- совместимость со строгим режимом single-index

---

## 1) MANDATORY HEADER (REQUIRED)
Каждый документ обязан иметь ровно одну шапку в начале файла.

REQUIRED FIELDS (строго):
FILE
SCOPE
LAYER
DOC_TYPE
LEVEL
STATUS
LOCK
VERSION
UID
OWNER
ROLE

OPTIONAL (recommended):
CHANGE_NOTE

---

## 2) STRICT NO-DUP RULE (ABSOLUTE)
Запрещено дублировать метаданные шапки где-либо ниже в тексте, включая:
FILE / SCOPE / LAYER / DOC_TYPE / LEVEL / STATUS / LOCK / VERSION / UID / OWNER / ROLE

Запрещённые паттерны (примеры):
- "FINAL RULE (LOCK) LOCK: FIXED"
- "LOCK: FIXED" в конце
- "STATUS: ACTIVE" повтором внизу

Одна истина метаданных — только в шапке.

---

## 3) STATUS (ENUM)
DRAFT | ACTIVE | DEPRECATED | ARCHIVED

## 4) LOCK (ENUM)
OPEN | FIXED

## 5) VERSIONING
SemVer: X.Y.Z

---

## 6) STRICT SINGLE-INDEX MODE (COMPATIBLE)
Слой может объявить режим:
- один master-index = единственный SoT по NAV/EXISTENCE
- sub-indexes запрещены
- ссылки PATH/RAW допускаются только в master-index
Это совместимо с данным стандартом.

## 7) RAW-ONLY NAV RULE (RECOMMENDED FOR INDEXES)
Для INDEX документов навигация должна быть оформлена как RAW ссылки.
PATH допускается только как человеческая подпись и не считается навигацией.


--- END.
