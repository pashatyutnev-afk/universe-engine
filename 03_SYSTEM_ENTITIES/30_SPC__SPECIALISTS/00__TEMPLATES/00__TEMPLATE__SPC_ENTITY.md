# SPC ENTITY — TEMPLATE
FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00__TEMPLATES/00__TEMPLATE__SPC_ENTITY.md

SCOPE: Universe Engine / SPC Template
ENTITY_GROUP: ENT
CATEGORY: SPC
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0
OWNER: SYSTEM
ROLE: Универсальный шаблон SPC: контракт + формат выдачи решения.

SOURCE OF TRUTH:
- UID Standard: `02_STANDARDS/01_SPECIFICATIONS/UID_AND_MARKING_SPEC.md`
- SPC Rules: `03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/01__RULES__SPC.md`

---

## 0) HEADER (REQUIRED)
UID: <UE.ENT.SPC.<FAMILY>.<NAME>>
FAMILY: <NAR|WORLD|VIS|SND|GEN|QLT>
STATUS: <DRAFT|ACTIVE|DEPRECATED|ARCHIVED>
LOCK: <OPEN|FIXED>
VERSION: <1.0>
OWNER: <SYSTEM|YOU>
ROLE: <кто он и зачем, 1 строка>

---

## 1) PURPOSE (REQUIRED)
- какую доменную область закрывает
- какой тип задач решает
- какие выходы производит

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- []
PRODUCES:
- []
DEPENDS_ON:
- []
OUTPUT_TARGET:
- <KB|PRJ|AST|OUT>

---

## 3) OUTPUT SHAPE (MANDATORY)
### DECISIONS
- <decision_01>
- <decision_02>

### CONSTRAINTS
- <constraint_01>
- <constraint_02>

### DELIVERABLES
- KB: <what to add or change>
- PRJ: <what to set in scene/episode>
- AST: <prompt payloads / asset requirements>
- OUT: <stack/script guidance>

### OPEN_QUESTIONS (optional)
- <question_01>

---

## 4) NOTES (OPTIONAL)

---
END.
