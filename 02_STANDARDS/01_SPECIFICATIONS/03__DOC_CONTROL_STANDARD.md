# DOC CONTROL STANDARD (CANON)
FILE: 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: SPEC
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.STD.SPEC.DOC_CONTROL.001
OWNER: SYSTEM
ROLE: Doc header, lifecycle, versioning, and minimal cross-reference contract (UID-first)

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MINOR
- SUMMARY: "XREF/REL minimum contract changed to UID+WHY. PATH/URL are optional. Added compatibility rule: layers may enforce stricter no-link policies."
- REASON: "Совместимость с KB strict mode (no intermediate links) и устранение path-dependency."
- IMPACT: "Docs can remain stable even if file paths change."

---

## PURPOSE (LAW)
Определяет стандарт оформления документов: шапка, статусы, версии, контроль ссылок.

---

## MANDATORY HEADER (REQUIRED)
Каждый документ должен иметь шапку:

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

Optional (if needed):
CHANGE_NOTE (recommended for FIXED docs)

---

## STATUS (ENUM)
DRAFT | ACTIVE | DEPRECATED | ARCHIVED

## LOCK (ENUM)
OPEN | FIXED

---

## VERSIONING (SEMVER)
X.Y.Z
- MAJOR: изменение принципов/совместимости
- MINOR: добавление правил/полей без слома
- PATCH: правки без смены смысла

---

## UID (REQUIRED)
UID:
- уникальный
- стабильный
- не зависит от PATH
- используется для XREF/REL

---

## CROSS-REFERENCE MINIMUM CONTRACT (GLOBAL)
Чтобы все слои были совместимы, фиксируем минимум:

### XREF (UID-FIRST)
Минимальный формат (обязательный минимум):
- XREF: <UID> | WHY: <reason>

PATH/URL поля (если слой их допускает) — строго опциональны.
Слой может полностью запретить PATH/URL.

### REL (UID-FIRST)
Минимальный формат (обязательный минимум):
- REL: <REL_TYPE> | TARGET: <UID> | WHY: <reason>

---

## LINK POLICY (COMPATIBILITY)
- Базовый стандарт допускает, что некоторые слои используют PATH/URL в индексах/картах.
- Слой имеет право быть строже и запретить любые ссылки вне одного master-index (strict mode).
- Это считается совместимым, если минимум UID+WHY соблюдён.

---

## RECOMMENDED SECTIONS (CONTENT)
- PURPOSE
- DEFINITIONS (если нужно)
- RULES / CONSTRAINTS
- XREF / REL (UID-first)
- CHANGELOG (для FIXED/важных документов)

--- END.
