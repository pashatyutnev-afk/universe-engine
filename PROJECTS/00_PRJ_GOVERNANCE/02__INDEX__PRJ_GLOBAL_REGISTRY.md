# PRJ GLOBAL REGISTRY — SINGLE SOURCE OF TRUTH
FILE: 05_PROJECTS/00_PRJ_GOVERNANCE/02__INDEX__PRJ_GLOBAL_REGISTRY.md

SCOPE: Universe Engine / Project Registry
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Реестр всех PRJ объектов (PACK/EP/SCENE/SHOT). 1 строка = 1 объект.

---

## 0) EXISTENCE RULE
> Если PRJ объекта нет в этом реестре — он не существует для проекта.

---

## 1) REGISTRY ROW FORMAT
`<UID> | <CATEGORY> | <FAMILY> | <STATUS> | <CANON_PATH> | <PARENT_UID> | <NOTE>`

Пример:
`UE.PRJ.SCENE.GEN.EP01_SCN_003 | SCENE | GEN | ACTIVE | 05_PROJECTS/01_PACKS/... | UE.PRJ.EP.GEN.EP01 | scene 3`

---

## 2) REGISTRY (EMPTY — TO BE FILLED)
(пока пусто)

---
END.
