# SPC CREATE FLOW — BOOTSTRAP
FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/03__CREATE_FLOW__SPC.md

SCOPE: Universe Engine / SPC Workflow
ENTITY_GROUP: ENT
CATEGORY: SPC
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0
OWNER: SYSTEM
ROLE: Как создавать SPC без ошибок: UID → файл → registry.

---

## 0) CORE LAW
SPC существует только после:
(1) файл SPC + (2) запись в SPC Global Registry.

---

## 1) STEPS
1) Выбери FAMILY (NAR/WORLD/VIS/SND/GEN/QLT)
2) Сгенерируй UID: `UE.ENT.SPC.<FAMILY>.<NAME>`
3) Создай файл SPC (по канону нумерации внутри выбранного семейства, если введёшь подпапки)
4) Заполни по `00__TEMPLATE__SPC_ENTITY.md`
5) Добавь запись в `02__INDEX_ALL_SPECIALISTS.md`

---

## 2) FAIL CONDITIONS
S0:
- нет mini-contract
- нет output shape
- нет registry записи

---
END.
