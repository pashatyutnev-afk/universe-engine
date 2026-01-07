# CTL CREATE FLOW — BOOTSTRAP
FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/03__CREATE_FLOW__CTL.md

SCOPE: Universe Engine / CTL Workflow
ENTITY_GROUP: ENT
CATEGORY: CTL
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0
OWNER: SYSTEM
ROLE: Как создавать CTL без ошибок: UID → файл → registry.

---

## 0) CORE LAW
CTL существует только после:
(1) файл CTL + (2) запись в CTL Global Registry.

---

## 1) STEPS
1) Выбери FAMILY (GOV/PROD/GEN)
2) Сгенерируй UID: `UE.ENT.CTL.<FAMILY>.<NAME>`
3) Создай файл CTL (по канону нумерации внутри выбранного семейства, если будут подпапки)
4) Заполни по `00__TEMPLATE__CTL_ENTITY.md`
5) Добавь запись в `02__INDEX_ALL_CONTROLLERS.md`

---
END.
