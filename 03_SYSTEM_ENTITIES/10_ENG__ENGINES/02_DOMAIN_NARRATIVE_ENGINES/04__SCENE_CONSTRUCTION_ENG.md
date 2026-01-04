# Scene Construction Engine
FILE: 04__SCENE_CONSTRUCTION_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
LEVEL: L2
STATUS: ACTIVE
VERSION: 1.0
ROLE: Builds scenes as functional units with goals, conflicts, turns, and state changes

---

## PURPOSE

Определяет сцену как **функциональный модуль**.
Сцена должна быть не “описанием”, а **операцией изменения состояния**.

---

## INPUTS

- Beat placement (из STORY_STRUCTURE_ENG)
- Characters in scene + intents
- Constraints (world rules)
- Current state snapshot

---

## OUTPUTS

- Scene Card (канонический формат сцены)
- Turn definition (перелом внутри сцены)
- State delta (что поменялось)
- Scene purpose classification

---

## CANONICAL SCENE CARD

- SCENE_ID
- LOCATION / TIME
- POV (если важно)
- GOAL: цель сцены (что герой пытается получить)
- OBSTACLE: что мешает
- CONFLICT MODE: внешний/внутренний/межличностный/системный
- TURNING POINT: что меняет направление/понимание
- OUTCOME: получилось/не получилось/частично
- COST: цена
- NEW STATE: чем закончили (info/position/relationship/risk)
- HOOK: что тянет в следующую

---

## PROCEDURE

1) Define Goal
2) Define Opposition (кто/что против)
3) Define Tactic (как пытаются)
4) Insert Turn:
   - новая инфа
   - новая угроза
   - ошибка
   - предательство
   - вмешательство
5) Outcome + Cost
6) State Delta:
   - минимум одно изменение обязано быть

---

## VALIDATION RULES

- C1: Нет цели → это не сцена, это “переход”.
- C2: Нет конфликта/напряжения → сцена должна быть объединена/удалена.
- C3: Нет изменения состояния → сцена бесполезна.
- C4: Turn обязателен почти всегда (кроме намеренных “valley scenes”, но там должна быть функция).
- C5: Сцена не должна решать главный конфликт случайностью.

---

## FAILURE MODES

- “Люди поговорили” без цены и результата
- “Экшн” без смысла (ничего не изменилось)
- Сцена повторяет предыдущую
- Слишком много экспозиции без конфликта

---

## INTEGRATION

- With TURNING_POINT_ENG (Expression): точная механика поворотных точек
- With TENSION_STAKES_ENG: сцена обязана двигать ставки
- With CONTINUITY_ENG: сцена должна быть консистентна по фактам

---
OWNER: Universe Engine
STATUS: FIXED
