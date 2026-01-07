# KB GLOBAL REGISTRY — INDEX (CANON)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/02__INDEX__KB_GLOBAL_REGISTRY.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: REGISTRY
REGISTRY_TYPE: KB_GLOBAL_ENTITY_REGISTRY
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.KB.GOV.REGISTRY.012
OWNER: SYSTEM
ROLE: Canonical global registry of KB entities. Defines entity existence at the KB-world level: an entity exists only if registered here with a valid passport reference.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Нормализован KB Global Registry: контракт реестра, поля, правила обновления, entity-status vs doc-status"
- REASON: "Единая точка истины о сущностях KB"
- IMPACT: "All KB entity creation and references"

---

## XREF (UID-first)
XREF: UE.KB.GOV.RULES.011 | governs | registry-first entity existence | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md
XREF: UE.KB.TPL.ENTITY_PASSPORT.015 | depends_on | passport required fields | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/05__TEMPLATE__KB_ENTITY_PASSPORT.md
XREF: UE.KB.GOV.ENTITY_TYPES.013 | depends_on | controlled entity typing | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/03__INDEX__KB_ENTITY_TYPES.md
XREF: UE.STD.SPEC.REL_XREF.104 | depends_on | UID-first references | 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md

---

## 0) PURPOSE (LAW)
Этот реестр — единая точка истины о **существующих KB-сущностях**.

### ENTITY EXISTENCE RULE (ABSOLUTE)
> Сущность считается существующей в KB только если:
> 1) у неё есть `ENTITY_UID`
> 2) у неё есть паспорт (PASSPORT_PATH)
> 3) она зарегистрирована в этом реестре (эта таблица)

---

## 1) ENTITY STATUS (NOT DOC STATUS)
`ENTITY_STATUS` — состояние сущности (не путать с header STATUS документа).

Recommended controlled values:
- `active`
- `draft`
- `deprecated`
- `retired`
- `unknown`

Правило:
- `deprecated` сущность обязана иметь ссылку/переезд на каноническую замену.

---

## 2) REGISTRY RECORD FORMAT (STANDARD)
Каждая запись (строка) должна содержать:

- ENTITY_UID (required, unique)
- ENTITY_NAME (required)
- ENTITY_TYPE (required, must exist in Entity Types)
- ENTITY_STATUS (required)
- PASSPORT_PATH (required)
- PRIMARY_REALM (optional)
- TAGS (optional)
- NOTE (optional)
- XREF (optional, UID-first)

---

## 3) REGISTRY TABLE (CANON)
> Формат таблицы Markdown.  
> Сортировка: по ENTITY_TYPE, затем по ENTITY_NAME (рекомендуется).  
> ENTITY_UID всегда уникален.

| ENTITY_UID | ENTITY_NAME | ENTITY_TYPE | ENTITY_STATUS | PASSPORT_PATH | PRIMARY_REALM | TAGS | NOTE |
|---|---|---|---|---|---|---|---|
| (empty) | (add entities here) |  |  |  |  |  |  |

---

## 4) UPDATE RULES (MANDATORY)
### 4.1 Add new entity
Чтобы добавить сущность:
1) создать паспорт по шаблону
2) присвоить ENTITY_UID
3) добавить строку в таблицу
4) при необходимости добавить XREF связи в паспорте

### 4.2 Update existing entity
Разрешено менять:
- ENTITY_NAME (rename)
- ENTITY_STATUS
- TAGS/NOTE
- PASSPORT_PATH (если паспорт перемещён — must migrate)

Запрещено:
- менять ENTITY_UID (UID immutable)

### 4.3 Deprecation / merge
Если сущность deprecated:
- ENTITY_STATUS = deprecated
- NOTE должен содержать `DEPRECATED_BY: <ENTITY_UID_CANON>`
- паспорт дубля должен содержать:
  - `DEPRECATED_BY_ENTITY_UID: <ENTITY_UID_CANON>`
  - XREF deprecated_by → ENTITY_UID_CANON

---

## 5) VALIDATION CHECKLIST
- нет дублей ENTITY_UID
- у каждой строки существует PASSPORT_PATH
- ENTITY_TYPE валиден
- deprecated сущности имеют DEPRECATED_BY

---

## 6) OPTIONAL: XREF BLOCK (UID-FIRST)
Если нужен список связей на уровне реестра:

XREF:
- XREF: <UID_TARGET> | references | "<why>" | <path(optional)>

---

## FINAL RULE (LOCK)
Этот реестр определяет существование KB-сущностей (world-canon level).
Любая правка контракта колонок/правил = изменение канона.
--- END.
