# QA CREATE FLOW — BOOTSTRAP
FILE: 03_SYSTEM_ENTITIES/60_QA__QUALITY/03__CREATE_FLOW__QA.md

SCOPE: Universe Engine / QA Workflow
ENTITY_GROUP: ENT
CATEGORY: QA
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0
OWNER: SYSTEM
ROLE: Как создавать QA без ошибок: UID → файл → registry → подключение в ORC gates.

---

## 0) CORE LAW
QA существует только после:
(1) файл QA + (2) запись в QA Global Registry.

---

## 1) STEPS
1) Выбери FAMILY (NAT/STY/TXT/AUD/VIS/GEN)
2) Сгенерируй UID: `UE.ENT.QA.<FAMILY>.<NAME>`
3) Создай файл QA (по шаблону)
4) Зарегистрируй в `02__INDEX_ALL_QA.md`
5) Подключи как gate в нужные ORC STEP (GATE: QA)

---
END.
