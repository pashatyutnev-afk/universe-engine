# 00__TEMPLATE__CTL_ENTITY

FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/00__TEMPLATES/00__TEMPLATE__CTL_ENTITY.md
SCOPE: Universe Engine / Controllers (CTL) / Template
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.CTL.TPL.ENTITY.001
OWNER: SYSTEM
ROLE: Canonical template for CTL controllers: doc control + mini-contract + checkpoint rules + blockers.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MAJOR
- SUMMARY: "Template upgraded to DOC CONTROL + RAW-only + mandatory contract fields."
- REASON: "Prevent creation of 'old style' controllers that drift from canon."
- IMPACT: "All new CTL files become consistent and audit-friendly."

---

## 0) HEADER (REQUIRED)
(Заполнить полностью)

FILE:
SCOPE:
SERIAL:
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: CTL (CONTROLLER)
LEVEL: L2 (ENTITY)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID:
OWNER: SYSTEM
ROLE: <что контролирует, 1 строка>

CHANGE_NOTE:
- DATE:
- TYPE: PATCH|MINOR|MAJOR
- SUMMARY:
- REASON:
- IMPACT:
- CHANGE_ID:

---

## 1) PURPOSE (REQUIRED)
- Что проверяет контроллер
- Где используется (какие ORC шаги или какой маршрут)
- Какие артефакты считает обязательными
- Что является STOP (S0/S1)

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- []

PRODUCES:
- []

DEPENDS_ON:
- []

OUTPUT_TARGET:
- LOG | PRJ | OUT

---

## 3) CHECKPOINTS (MANDATORY)
(минимум один)

CHECKPOINT:
- NAME:
- APPLIES_TO: <artifact type / step name>
- REQUIRES (ARTIFACTS):
  - <list>
- CHECKS:
  - <explicit testable checks>
- OUTPUT:
  - STATE: READY | BLOCKED | DONE | SKIP
  - BLOCKERS:
    - (если BLOCKED) список blocker записей по шаблону CTL_BLOCKER

---

## 4) BLOCKERS (FORMAT)
Использовать единый формат blocker:

BLOCKER:
- CODE:
- SEVERITY: S0 | S1 | S2 | S3
- MESSAGE: ""
- REQUIRED_ACTION: ""

---

## 5) RELATIONS (OPTIONAL BUT RECOMMENDED)
CALLS: []
CONSUMES: []
PRODUCES: []
DEPENDS_ON: []
VALIDATES: []
QUALITY_GATES: []
GOVERNS: []
REFERENCES: []

---

## 6) INTERFACES (RAW)
- UID RULES: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md
- DOC CONTROL: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
- CTL RULES: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__RULES__CTL.md
- CTL INDEX (SoT): https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/02__INDEX_ALL_CONTROLLERS.md
- CTL BLOCKER TEMPLATE: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/00__TEMPLATES/00__TEMPLATE__CTL_BLOCKER.md

---

## 7) KNOWLEDGE BASE (KB) SCOPE
KB Inputs:
- optional: контрольные чек-листы, примеры blockers, эталоны gate-отчётов

KB Outputs:
- none

Boundaries:
- CTL не создаёт доменные правила и не подменяет стандарты

--- END.
