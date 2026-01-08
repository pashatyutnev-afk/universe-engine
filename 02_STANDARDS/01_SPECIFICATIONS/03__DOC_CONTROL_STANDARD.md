# DOC CONTROL STANDARD (CANON)
FILE: 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: SPEC
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.2.1
UID: UE.STD.SPEC.DOC_CONTROL.001
OWNER: SYSTEM
ROLE: Doc header + lifecycle + minimal XREF/REL contract (UID-first) + anti-dup rules

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: PATCH
- SUMMARY: "Made FILE field explicitly allowed. Removed footer meta duplication pattern. Added strict single-index compatibility clause."
- REASON: "Убрать конфликт: документы используют FILE, а стандарт его не признавал. Запретить дубли LOCK/STATUS/VERSION внизу."
- IMPACT: "Единый Doc Control без самопротиворечий."

---

## 0) PURPOSE (LAW)
Этот стандарт определяет:
- обязательную шапку документа (Doc Control header)
- правила статусов/локов/версий
- минимальный формат XREF/REL (UID-first)
- запрет на дубли метаданных вне шапки
- совместимость со строгими режимами (single-index)

---

## 1) MANDATORY HEADER (REQUIRED)
Каждый документ обязан иметь шапку (ровно один раз, в начале файла):

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

Optional (recommended):
CHANGE_NOTE

---

## 2) STRICT NO-DUP RULE (ABSOLUTE)
Запрещено дублировать метаданные шапки где-либо ниже в тексте, включая:
STATUS / LOCK / VERSION / UID / OWNER / FILE / LAYER / DOC_TYPE / LEVEL / SCOPE

Одна истина метаданных — в шапке.

Запрещённый паттерн (пример):
"FINAL RULE (LOCK) LOCK: FIXED"  ← это дубль LOCK и нарушает стандарт.

---

## 3) STATUS (ENUM)
DRAFT | ACTIVE | DEPRECATED | ARCHIVED

## 4) LOCK (ENUM)
OPEN | FIXED

## 5) VERSIONING
SemVer: X.Y.Z

---

## 6) MINIMUM CROSS-REFERENCE CONTRACT (GLOBAL)

### XREF (UID-FIRST)
Формат:
- XREF: <UID> | WHY: <reason>

### REL (UID-FIRST)
Формат:
- REL: <REL_TYPE> | TARGET: <UID> | WHY: <reason>

PATH/URL допускаются только если слой это разрешает.
Слой имеет право быть строже и полностью запретить ссылки вне одного master-index.

---

## 7) STRICT SINGLE-INDEX MODE (COMPATIBLE)
Слой может объявить режим:
- один master-index = единственный SoT по NAV/EXISTENCE
- sub-indexes запрещены
- PATH/RAW/URL разрешены только в master-index

Это совместимо с данным стандартом при соблюдении UID-first.

--- END.
