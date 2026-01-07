# KB CREATE FLOW — BOOTSTRAP
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/06__KB_CREATE_FLOW.md

SCOPE: Universe Engine / KB Workflow
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0
OWNER: SYSTEM
ROLE: Мини-процедура создания KB-сущности без ошибок.

---

## 0) CORE LAW
- Сущность считается существующей только после:
  (1) создания паспорта + (2) регистрации в реестре.

---

## 1) CREATE STEPS (CANON)
1) Выбери CATEGORY (см. `03__INDEX__KB_ENTITY_TYPES.md`)
2) Выбери FAMILY (GEN/WORLD/…)
3) Сгенерируй UID: `UE.KB.<CATEGORY>.<FAMILY>.<NAME>`
4) Создай файл по пути из `04__KB_STORAGE_MAP.md`
5) Заполни паспорт по `05__TEMPLATE__KB_ENTITY_PASSPORT.md`
6) Добавь строку в `02__INDEX__KB_GLOBAL_REGISTRY.md`

---

## 2) REGISTRY LINE TEMPLATE
`<UID> | <CATEGORY> | <FAMILY> | <STATUS> | <CANON_PATH> | <NOTE>`

---

## 3) FAIL CONDITIONS
S0:
- нет UID
- нет записи в реестре
- файл лежит не в KB дереве

---
END.
