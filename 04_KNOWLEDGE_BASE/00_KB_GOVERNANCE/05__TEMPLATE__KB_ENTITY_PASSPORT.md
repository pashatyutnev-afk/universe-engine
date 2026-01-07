# KB ENTITY PASSPORT — TEMPLATE (UNIVERSAL)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/05__TEMPLATE__KB_ENTITY_PASSPORT.md

SCOPE: Universe Engine / Knowledge Base
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0
OWNER: SYSTEM
ROLE: Универсальный шаблон паспорта KB-сущности. Используется для CHR/LOC/OBJ/EVT/SYS/CONCEPT/REL/ARC/STYLE.

SOURCE OF TRUTH:
- UID закон: `02_STANDARDS/01_SPECIFICATIONS/UID_AND_MARKING_SPEC.md`
- KB rules: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md`
- REL/XREF: `02_STANDARDS/06_MARKING_STANDARDS/05__REL_POLICY_XREF.md`

---

## 0) HEADER (REQUIRED)
UID: <UE.KB.<CATEGORY>.<FAMILY>.<NAME>>
CATEGORY: <CHR|LOC|OBJ|EVT|SYS|CONCEPT|REL|ARC|STYLE>
FAMILY: <WORLD|GEN|NAR|VIS|SND|GOV|LOG|QLT|...>
STATUS: <DRAFT|ACTIVE|DEPRECATED|ARCHIVED>
LOCK: <OPEN|FIXED>
VERSION: <1.0>

---

## 1) SUMMARY (REQUIRED)
1–5 строк: что это и зачем существует.

---

## 2) CANON ROLE (REQUIRED)
ROLE_IN_WORLD:
- Коротко: роль/назначение в мире
- Где используется (если известно)

---

## 3) KEY FACTS (OPTIONAL)
- FACT_01:
- FACT_02:
- FACT_03:

---

## 4) RELATIONS (OPTIONAL)
XREFS: []
DEPENDS_ON: []

REL_POLICY:
  - TARGET: "UE.KB.*.*.*"
    MODE: "SOMETIMES"
    CONDITIONS: "only when needed"
    REASON: "KB cross-knowledge"

---

## 5) CONSTRAINTS (OPTIONAL)
- ограничения/запреты/что НЕ может быть истинным

---

## 6) NOTES (OPTIONAL)
- любые уточнения, ссылки на источники, версии смысла

---
END.
