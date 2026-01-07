# PRJ ENTITY TYPES — INDEX
FILE: 05_PROJECTS/00_PRJ_GOVERNANCE/03__INDEX__PRJ_ENTITY_TYPES.md

SCOPE: Universe Engine / PRJ Types
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Типы PRJ объектов и их минимальные поля.

---

## PACK
Минимум:
- UID
- SUMMARY
- GOALS (optional)
- STYLE_TARGET (optional)
- OUTPUT_TARGETS (куда будет выход)

## EP
Минимум:
- UID
- SUMMARY
- PACK_REF

## SCENE
Минимум:
- UID
- SUMMARY
- EP_REF
- STACK_REF (обязателен после создания STACK)

## SHOT (optional)
Минимум:
- UID
- SUMMARY
- SCENE_REF

---
END.
