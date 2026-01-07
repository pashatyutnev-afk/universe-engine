# VAL CREATE FLOW — BOOTSTRAP
FILE: 03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/03__CREATE_FLOW__VAL.md

SCOPE: Universe Engine / VAL Workflow
ENTITY_GROUP: ENT
CATEGORY: VAL
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0
OWNER: SYSTEM
ROLE: Как создавать VAL без ошибок: UID → файл → registry → подключение в ORC gates.

---

## 0) CORE LAW
VAL существует только после:
(1) файл VAL + (2) запись в VAL Global Registry.

---

## 1) STEPS
1) Выбери FAMILY (DOC/IDX/ENT/STD/GEN)
2) Сгенерируй UID: `UE.ENT.VAL.<FAMILY>.<NAME>`
3) Создай файл VAL (по шаблону)
4) Зарегистрируй в `02__INDEX_ALL_VALIDATORS.md`
5) Подключи как gate в нужные ORC STEP (GATE: VAL)

---
END.
