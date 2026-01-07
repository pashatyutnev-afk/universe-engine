# SPECIALISTS (SPC) — REALM README
FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00__README__SPC_REALM.md

SCOPE: Universe Engine / System Entities / Specialists
ENTITY_GROUP: ENT
CATEGORY: SPC
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Определяет что такое SPC, как специалисты работают с ENG/ORC, и как их выводы попадают в KB/PRJ/AST/OUT.

SOURCE OF TRUTH:
- UID Standard: `02_STANDARDS/01_SPECIFICATIONS/UID_AND_MARKING_SPEC.md`
- ENT Master Index: `03_SYSTEM_ENTITIES/00__INDEX__ALL_ENTITIES.md`

---

## 0) WHAT IS SPC
SPC (Specialist) — доменный эксперт.
Он:
- принимает задачу/контекст
- выдаёт доменное решение (конкретика)
- оформляет решение в структуру, пригодную для PRJ/KB/AST/OUT

SPC не маршрутизирует пайплайн (это ORC).
SPC не устанавливает законы системы (это ENG/GOV).
SPC не является финальной проверкой (это VAL/QA).

---

## 1) EXISTENCE LAW
SPC существует только если:
- имеет UID (UE.ENT.SPC...)
- зарегистрирован в SPC Global Registry

---

## 2) WHAT SPC PRODUCES
Типовые выходы SPC:
- decisions (решения/выборы)
- constraints (ограничения/правила для сцены/контента)
- domain packs (структуры: списки, таблицы, матрицы, параметры)
- prompt payloads (для AST промптов)
- KB updates suggestions (что занести в KB)

---

## 3) LINKS
- Rules: `01__RULES__SPC.md`
- Registry: `02__INDEX_ALL_SPECIALISTS.md`
- Create Flow: `03__CREATE_FLOW__SPC.md`
- Templates: `00__TEMPLATES/`

---
END.
