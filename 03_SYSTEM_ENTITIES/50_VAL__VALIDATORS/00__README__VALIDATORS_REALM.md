# VALIDATORS (VAL) — REALM README
FILE: 03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/00__README__VAL_REALM.md

SCOPE: Universe Engine / System Entities / Validators
ENTITY_GROUP: ENT
CATEGORY: VAL
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Определяет VAL: валидаторы проверяют структурную/правовую корректность артефактов по законам и стандартам системы.

SOURCE OF TRUTH:
- UID Standard: `02_STANDARDS/01_SPECIFICATIONS/UID_AND_MARKING_SPEC.md`
- ENT Master Index: `03_SYSTEM_ENTITIES/00__INDEX__ALL_ENTITIES.md`

---

## 0) WHAT IS VAL
VAL (Validator) — сущность проверки “правильно ли по системе”:
- структура документа
- наличие обязательных полей/шапок
- соответствие стандартам (ID/STATUS/LOCK/VERSION/Storage map и т.д.)
- корректность ссылок (xref)
- корректность регистраций (index existence)

VAL не принимает доменных решений (SPC/ENG).
VAL не управляет пайплайном (ORC/CTL).
VAL не оценивает художественное качество/естественность (QA).

---

## 1) EXISTENCE LAW
VAL существует только если:
- имеет UID (UE.ENT.VAL...)
- зарегистрирован в VAL Global Registry

---

## 2) WHAT VAL PRODUCES
Типовые выходы VAL:
- VALIDATION REPORT (pass/fail + причины)
- VIOLATIONS LIST (S0–S3)
- FIX ACTIONS (что исправить)
- OPTIONAL: AUTO-FIX SUGGESTIONS (только предложения, не “решение”)

---

## 3) LINKS
- Rules: `01__RULES__VAL.md`
- Registry: `02__INDEX_ALL_VALIDATORS.md`
- Create Flow: `03__CREATE_FLOW__VAL.md`
- Templates: `00__TEMPLATES/`

---
END.
