# CONTROLLERS (CTL) — REALM README
FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/00__README__CTL_REALM.md

SCOPE: Universe Engine / System Entities / Controllers
ENTITY_GROUP: ENT
CATEGORY: CTL
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Определяет CTL: кто такие контроллеры, как они управляют выполнением пайплайнов ORC, и как фиксируют состояние работы.

SOURCE OF TRUTH:
- UID Standard: `02_STANDARDS/01_SPECIFICATIONS/UID_AND_MARKING_SPEC.md`
- ENT Master Index: `03_SYSTEM_ENTITIES/00__INDEX__ALL_ENTITIES.md`

---

## 0) WHAT IS CTL
CTL (Controller) — сущность управления процессом выполнения:
- ставит checkpoints / gates
- проверяет наличие обязательных артефактов
- фиксирует состояние выполнения (ready / blocked / done)
- умеет “остановить” пайплайн по правилам

CTL не принимает доменных решений (SPC/ENG).
CTL не валидирует законы структуры (VAL).
CTL не оценивает художественное качество (QA).

---

## 1) EXISTENCE LAW
CTL существует только если:
- имеет UID (UE.ENT.CTL...)
- зарегистрирован в CTL Global Registry

---

## 2) WHAT CTL PRODUCES
Типовые выходы CTL:
- CHECKPOINT_STATUS
- BLOCKERS LIST
- REQUIRED ARTIFACTS CHECK
- RUN LOG ENTRY (если включён LOG слой)

---

## 3) LINKS
- Rules: `01__RULES__CTL.md`
- Registry: `02__INDEX_ALL_CONTROLLERS.md`
- Create Flow: `03__CREATE_FLOW__CTL.md`
- Templates: `00__TEMPLATES/`

---
END.
