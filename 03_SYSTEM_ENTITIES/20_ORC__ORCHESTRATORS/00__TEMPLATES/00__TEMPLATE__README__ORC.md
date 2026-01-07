# ORC FAMILY — README TEMPLATE
FILE: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/00__TEMPLATES/00__TEMPLATE__README__ORC.md

SCOPE: Universe Engine / System Entities / ORC
ENTITY_GROUP: ENT
CATEGORY: ORC
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0
OWNER: SYSTEM
ROLE: Шаблон README для семейства ORC (если вводятся семейства/подпапки внутри ORC).

SOURCE OF TRUTH:
- UID Standard: `02_STANDARDS/01_SPECIFICATIONS/UID_AND_MARKING_SPEC.md`
- ORC Realm: `03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/00__README__ORC_REALM.md`
- ORC Rules: `03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/01__RULES__ORC.md`
- ORC Registry: `03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/02__INDEX_ALL_ORCHESTRATORS.md`

---

## 0) FAMILY PURPOSE (REQUIRED)
Коротко:
- зачем это семейство оркестраторов существует
- какие задачи маршрутизирует
- какие типы выходов обслуживает (PRJ/AST/OUT)

---

## 1) INCLUDED ORCHESTRATORS (REQUIRED)
Строго по номеру:

01 — <ORC NAME> — 🔗 <RAW LINK>  
02 — <ORC NAME> — 🔗 <RAW LINK>  

---

## 2) BOUNDARIES (MANDATORY)
### ORC DOES
- маршрутизация
- порядок шагов
- handoff targets (KB/PRJ/AST/OUT)
- checkpoints (CTL/VAL/QA gates)

### ORC DOES NOT
- доменные решения (SPC/ENG)
- валидация законов (VAL/QA)
- хранение контента (KB/PRJ/AST/OUT)

---

## 3) DEFAULT PIPELINE SHAPE (OPTIONAL)
Если в семействе есть “типовой пайплайн”, опиши:

- входы (CONSUMES)
- выходы (PRODUCES)
- контрольные точки (GATES)

---

## 4) NOTES (OPTIONAL)

---
END.
