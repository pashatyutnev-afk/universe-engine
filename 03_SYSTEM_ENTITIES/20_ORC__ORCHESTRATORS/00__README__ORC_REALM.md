# ORCHESTRATORS (ORC) — REALM README
FILE: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/00__README__ORC_REALM.md

SCOPE: Universe Engine / System Entities / Orchestrators
ENTITY_GROUP: ENT
CATEGORY: ORC
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Объясняет что такое ORC, какие бывают оркестраторы и как они управляют пайплайнами ENG/SPC/CTL/VAL/QA.

SOURCE OF TRUTH:
- UID Standard: `02_STANDARDS/01_SPECIFICATIONS/UID_AND_MARKING_SPEC.md`
- ENT Master Index: `03_SYSTEM_ENTITIES/00__INDEX__ALL_ENTITIES.md`

---

## 0) WHAT IS ORC
ORC (Orchestrator) — сущность маршрутизации:
- выбирает кто выполняет задачу
- в каком порядке
- какие входы нужны
- какие выходы считаются завершением

ORC не придумывает доменные решения (это SPC/ENG).
ORC не валидирует правила (это VAL/QA).
ORC не хранит контент (это KB/PRJ/AST/OUT).

---

## 1) EXISTENCE LAW
ORC существует только если:
- имеет UID (UE.ENT.ORC...)
- зарегистрирован в ORC Global Registry

---

## 2) ORC OUTPUT
Оркестратор производит:
- PIPELINE PLAN (план шагов)
- ROUTING (кто что делает)
- HANDOFFS (куда кладём результат: KB/PRJ/AST/OUT)
- CHECKPOINTS (где CTL/VAL/QA должны остановить/пропустить)

---

## 3) LINKS
- Rules: `01__RULES__ORC.md`
- Registry: `02__INDEX_ALL_ORCHESTRATORS.md`
- Templates: `00__TEMPLATES/`

---
END.
