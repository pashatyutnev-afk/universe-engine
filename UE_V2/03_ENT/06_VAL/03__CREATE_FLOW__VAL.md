# VALIDATORS (VAL) — CREATE FLOW

FILE: 03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/03__CREATE_FLOW__VAL.md
SCOPE: Universe Engine (Games volume) / Validators (VAL) / Create workflow
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: WORKFLOW
ENTITY_GROUP: VALIDATORS (VAL)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.GAMES.DOC.VAL.CREATE_FLOW.001
OWNER: SYSTEM
ROLE: Defines the canonical order to create a VAL entity: UID → file → registry entry → ORC gate integration.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MINOR
- SUMMARY: "DOC CONTROL alignment + clarified registry-first law + RAW-only interfaces."
- REASON: "Prevent non-registered validators from being treated as canon."
- IMPACT: "VAL creation becomes deterministic and auditable."
- CHANGE_ID: UE.CHG.2026-01-20.VAL.CREATE.001

---

## 0) CORE LAW
VAL считается существующим в каноне только после двух условий:
1) создан файл валидатора (по template)
2) добавлена запись в VAL Global Registry (SoT)

## 1) STEPS (CANON ORDER)
1) Выбери FAMILY (по назначению проверки), примерные семейства:
   - DOC / IDX / ENT / STD / GEN (если слой использует эту классификацию)
2) Назначь UID по UID rules (LAW)
3) Создай файл валидатора по шаблону `00__TEMPLATE__VAL_ENTITY.md`
4) Зарегистрируй валидатор в `02__INDEX_ALL_VALIDATORS.md` (RAW-only навигация)
5) Подключи в нужный ORC step как `GATE: VAL`
6) (Опционально) добавь примеры нарушений/отчётов в доменную библиотеку, если стандарт это требует

## 2) STOP CONDITIONS
- UID не назначен → STOP
- валидатор не зарегистрирован в global registry → STOP (NON-CANON)
- отсутствуют обязательные секции template → STOP

## 3) INTERFACES (RAW ONLY)
- VAL Global Registry (SoT):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/02__INDEX_ALL_VALIDATORS.md
- VAL Entity Template:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/00__TEMPLATES/00__TEMPLATE__VAL_ENTITY.md
- UID Rules:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md
- DOC CONTROL Standard:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
