# Timeline & Epoch Engine
FILE: 03__TIMELINE_EPOCH_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 04_DOMAIN_WORLD_ENGINES
LEVEL: L2
STATUS: ACTIVE
VERSION: 1.0
ROLE: Creates causal timeline, epochs, turning points, and history constraints

---

## PURPOSE

Строит историю мира как **цепочку причинности**:
- эпохи
- переломные события
- последствия
- что “возможно/невозможно” в текущий момент из-за истории

---

## INPUTS

- World structure
- World laws
- Key civilizations/factions
- Narrative needs (эпоха действия)

---

## OUTPUTS

- Timeline (ordered events)
- Epoch Map (названия + признаки)
- Turning points list
- Historical constraints for present

---

## CANONICAL EPOCH ENTRY

- EPOCH_ID / NAME
- TIME_RANGE
- DOMINANT POWERS
- KEY TECHNOLOGY/MAGIC LEVEL
- CULTURAL NORM
- MAJOR CONFLICTS
- ENDING TURN (что сломало эпоху)
- LEGACIES (что осталось)

---

## PROCEDURE

1) Define 3–7 epochs (если мир большой)
2) Place 5–15 turning events
3) For each event:
   - cause → event → consequence
4) Compute constraints:
   - какие ресурсы/идеи/раны пришли в “сейчас”
5) Lock canon:
   - что нельзя ретконить без change control

---

## VALIDATION RULES

- T1: У события должна быть причина и последствие.
- T2: Переломы меняют структуру власти/ресурсы/веру/тех.
- T3: “Сейчас” должно быть объяснимо историей.
- T4: Эпохи должны отличаться операционно (не только эстетикой).

---

## FAILURE MODES

- история как список дат без причинности
- эпохи одинаковые по сути
- события “появились из воздуха”

---

## INTEGRATION

- With CIVILIZATION_ENG: цивилизации эволюционируют по эпохам
- With CONFLICT_POWER_ENG: войны и баланс сил
- With CONTINUITY_ENG: согласование таймлайна и событий сюжета

---
OWNER: Universe Engine
STATUS: FIXED
