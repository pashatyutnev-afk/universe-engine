# Event Engine
FILE: 01__EVENT_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 05_EXPRESSION_ENGINES
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Produces structured events as operations that change world/character state

---

## PURPOSE

Собирает событие в **исполняемую спецификацию**:
- что должно быть истинно до (preconditions)
- что запускает (trigger)
- что происходит (action)
- какая цена (cost)
- что изменится (consequences)
- какие следы останутся (trace)

---

## INPUTS

- Current state snapshot (world + characters)
- Active conflicts / tensions
- Constraints (world law, continuity)

---

## OUTPUTS

- Event Spec (canonical format)
- Event-to-state delta (what exactly changes)
- Observables list (как событие узнаётся)

---

## EVENT TYPES (REFERENCE)

- SOCIAL (интрига, скандал, договор)
- POLITICAL (закон, переворот, санкция)
- MILITARY (атака, осада, диверсия)
- ENVIRONMENTAL (буря, эпидемия)
- DISCOVERY (находка, инсайт)
- INTERNAL (решение персонажа)
- SYSTEMIC (коллапс, кризис сети)

---

## PROCEDURE

1) Pick event type + scope (local/regional/global)
2) Write preconditions (3–8 пунктов)
3) Define trigger (конкретный сигнал)
4) Define actors (инициатор / цели / свидетели)
5) Describe action as steps (3–12)
6) Add cost ledger (что тратится/ломается)
7) Define consequences as state deltas (таблично)
8) Define trace (документы, раны, новые правила)
9) Define counters (что могло остановить)

---

## VALIDATION RULES

- EV1: Consequences must be measurable state changes.
- EV2: Trigger must be concrete, not “потому что сюжет”.
- EV3: Cost must be non-zero.
- EV4: Trace must exist (иначе событие не оставило след).

---

## INTEGRATION

- With CAUSE_EFFECT_ENG: цепочки
- With EVENT_SCHEDULING_ENG: порядок
- With CONTINUITY: фиксация следов

---
OWNER: Universe Engine
STATUS: FIXED
