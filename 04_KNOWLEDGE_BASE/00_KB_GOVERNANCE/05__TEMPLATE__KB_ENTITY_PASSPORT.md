# TEMPLATE: KB ENTITY PASSPORT
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/05__TEMPLATE__KB_ENTITY_PASSPORT.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TEMPLATE
TEMPLATE_TYPE: KB_ENTITY_PASSPORT
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.GOV.TPL.PASSPORT.001
OWNER: SYSTEM
ROLE: Canonical template for KB entity passports (objects): identity, classification, tags, relations, content, and validation gates

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Шаблон паспорта KB: Doc Control, типизация, теги, REL/XREF, валидация"
- REASON: "Единый формат нужен для реестров, поиска, reuse в проектах"
- IMPACT: "Все KB entity passports"

---

# 0) COPY RULE (MANDATORY)
- Этот файл НЕ редактируется при создании сущности.
- При создании нового паспорта копируешь шаблон целиком и заполняешь поля.
- Если нужно изменить формат — это делается правкой шаблона через governance change.

---

# 1) DOC CONTROL (REQUIRED HEADER)
Заполни шапку:

TITLE: <Human name>
FILE: <Path>
SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_ENTITY
ENTITY_TYPE: <one of: KB_PRACTICE|KB_PROCESS|KB_CHECKLIST|KB_CONCEPT|KB_METHOD|KB_ARTIFACT|KB_CASE|KB_SYSTEM_REF>
LEVEL: L2
STATUS: <DRAFT|ACTIVE|DEPRECATED|ARCHIVED>
LOCK: <OPEN|FIXED>
VERSION: <X.Y.Z>
UID: <UE.KB.ENT.<TYPE>.<NNN>>
OWNER: SYSTEM
ROLE: <1 line what this entity is for>

CHANGE_NOTE:
- DATE: <YYYY-MM-DD>
- TYPE: <MAJOR|MINOR|PATCH>
- SUMMARY: "<short>"
- REASON: "<short>"
- IMPACT: "<short>"

---

# 2) IDENTITY
## 2.1 Name
- CANON_NAME: `<snake_case_name>` (unique within its type folder)
- ALIASES: [optional list]

## 2.2 Scope
- KB_REALM_PRIMARY: <NARRATIVE|CHARACTER|VISUAL|SOUND|PRODUCTION|MARKETING|GLOSSARY|RESEARCH>
- KB_REALM_SECONDARY: [optional list]

## 2.3 Tags
- TAGS: [a,b,c] (только из `04_KNOWLEDGE_BASE/90__KB_TAGS.md`)
- MAX_TAGS: 12

---

# 3) SUMMARY (ONE SCREEN)
- PROBLEM: (1–3 lines)
- SOLUTION: (1–3 lines)
- WHEN_TO_USE: (bullets)
- WHEN_NOT_TO_USE: (bullets)

---

# 4) BODY (BY ENTITY_TYPE)
> Заполни только релевантные секции; пустые секции удаляй.

## 4.A) KB_PRACTICE
- PURPOSE
- STEPS (numbered)
- DO / DONT
- COMMON_FAILURES
- EXAMPLES
- VARIATIONS

## 4.B) KB_PROCESS
- INPUTS
- OUTPUTS
- ROLES
- STEPS (numbered)
- GATES (what must be true to pass)
- FAILURE_MODES
- STORAGE_TARGET (where outputs go)

## 4.C) KB_CHECKLIST
- CHECKLIST_ITEMS (bullets)
- PASS_FAIL_RULE
- SEVERITY (S0..S3 if used)
- COMMON_MISTAKES

## 4.D) KB_CONCEPT
- DEFINITION (strict)
- BOUNDARIES (in/out)
- COMMON_CONFUSIONS
- EXAMPLES
- COUNTEREXAMPLES

## 4.E) KB_METHOD
- PURPOSE
- PROCEDURE
- TOOLS (optional)
- TRADEOFFS
- EXAMPLES

## 4.F) KB_ARTIFACT
- ARTIFACT_NAME
- STRUCTURE (required sections)
- VALIDATION_RULES
- STORAGE_TARGET
- EXAMPLES (optional)

## 4.G) KB_CASE
- CONTEXT
- CONSTRAINTS
- DECISION
- OUTCOME
- LESSONS
- WHAT_CHANGED (if iterative)

## 4.H) KB_SYSTEM_REF
- DESCRIPTION
- FORMAT (table/list)
- UPDATE_RULE (how it’s maintained)
- USED_BY (what depends on it)

---

# 5) RELATIONSHIPS (REL) (MANDATORY)
Формат записи:

`REL: <TYPE> -> <TARGET_UID> | WHY:<short>`

Где TYPE ∈:
- `depends_on`
- `related_to`
- `part_of`
- `supports`
- `replaces`
- `deprecated_by`

Пример:
`REL: depends_on -> UE.KB.ENT.KB_CONCEPT.012 | WHY:practice uses this concept`

Если нет связей:
- `REL: []`

---

# 6) CROSS-REFERENCES (XREF) (MANDATORY)
Формат:
- `XREF_DOC: <PATH> | WHY:<short>`
- `XREF_UID: <UID> | WHY:<short>`

Если нет:
- `XREF: []`

---

# 7) VALIDATION GATES (KB)
Перед переводом в `STATUS: ACTIVE` должно быть true:

- [ ] UID уникален и соответствует типу
- [ ] ENTITY_TYPE из канонического списка
- [ ] TAGS существуют в `90__KB_TAGS.md`
- [ ] Нет дубля смысла (anti-dup check)
- [ ] Есть минимум 1 XREF в realm (если сущность не purely-system)
- [ ] REL/XREF оформлены по формату
- [ ] VERSION = X.Y.Z

---

# 8) OUTPUT TARGET (OPTIONAL)
Если сущность производит reusable output, укажи:
- OUTPUT_TARGET: <path or project layer target>

---

## FINAL RULE (LOCK)
Этот шаблон обязателен для всех KB entity passports.
LOCK: FIXED
--- END.
