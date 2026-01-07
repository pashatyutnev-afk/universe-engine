# ORC CREATE FLOW — BOOTSTRAP
FILE: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/03__ORC_CREATE_FLOW.md

SCOPE: Universe Engine / ORC Workflow
ENTITY_GROUP: ENT
CATEGORY: ORC
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0
OWNER: SYSTEM
ROLE: Как создавать ORC без ошибок: UID → файл → registry.

---

## 0) CORE LAW
ORC существует только после:
(1) файл ORC + (2) запись в ORC Global Registry.

---

## 1) STEPS
1) Выбери FAMILY (PROD/GOV/QLT/GEN)
2) Сгенерируй UID: `UE.ENT.ORC.<FAMILY>.<NAME>`
3) Создай файл:
   `03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/<NN__ORC_NAME>.md` (или в подпапку — как решишь, главное канон)
4) Заполни по шаблону `00__TEMPLATE__ORC_ENTITY.md`
5) Добавь в реестр строку

---

## 2) FAIL CONDITIONS
S0:
- нет mini-contract
- нет pipeline steps
- нет registry записи

---
END.
