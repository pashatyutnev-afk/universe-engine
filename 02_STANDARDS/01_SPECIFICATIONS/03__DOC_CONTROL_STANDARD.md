# DOC CONTROL STANDARD (CANON)
FILE: 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: SPEC
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.2.0
UID: UE.STD.SPEC.DOC_CONTROL.001
OWNER: SYSTEM
ROLE: Doc header + lifecycle + minimal cross-reference contract (UID-first)

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MINOR
- SUMMARY: "Enforced UID-first XREF/REL contract. Clarified: PATH/URL optional; strict layers may ban links outside a single master-index. Banned metadata duplication."
- REASON: "Совместимость с KB strict mode и стабильность при изменении путей."
- IMPACT: "Docs stay valid even if paths change."

---

## MANDATORY HEADER (REQUIRED)
Каждый документ обязан иметь шапку:

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

Optional (recommended for FIXED docs):
CHANGE_NOTE

---

## STRICT NO-DUP RULE
Запрещено дублировать метаданные из шапки внизу файла:
- STATUS / LOCK / VERSION / UID / OWNER / FILE

Одна истина метаданных — в шапке.

---

## STATUS (ENUM)
DRAFT | ACTIVE | DEPRECATED | ARCHIVED

## LOCK (ENUM)
OPEN | FIXED

## VERSIONING
SemVer: X.Y.Z

---

## MINIMUM CROSS-REFERENCE CONTRACT (GLOBAL)

### XREF (UID-FIRST)
Минимальный формат:
- XREF: <UID> | WHY: <reason>

### REL (UID-FIRST)
Минимальный формат:
- REL: <REL_TYPE> | TARGET: <UID> | WHY: <reason>

PATH/URL допускаются только если слой это разрешает.
Слой имеет право быть строже и полностью запретить ссылки вне одного master-index.

--- END.
