# Game Narrative Engine
FILE: 08__GAME_NARRATIVE_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 07_PRODUCTION_FORMAT_ENGINES
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines interactive narrative structure (quests, missions, branching, agency, fail states)

---

## PURPOSE

Игра — это интерактив:
- игрок выбирает
- история должна выдерживать ветвления
- нужен “agency” (ощущение влияния)
- нужны состояния мира (state) и последствия

---

## INPUTS

- World law + systems
- Character arcs (if relevant)
- Game loop type (exploration/combat/story)
- Budget for branching

---

## OUTPUTS

- Narrative gameplay spec
- Quest/mission templates
- Branching model
- State & consequence rules

---

## CORE MODELS (CANON)

1) LINEAR WITH CHOICE FLAVOR  
   выбор влияет на детали, но не ломает магистраль.
2) BRANCHING ARC  
   2–4 крупных ветки с точками схождения.
3) HUB-AND-SPOKE  
   хаб + миссии, возвращение в хаб.
4) EMERGENT SYSTEM STORY  
   история рождается из систем и последствий.

---

## QUEST TEMPLATE (CANON)

- PLAYER GOAL
- OBSTACLE
- CHOICE POINT (optional)
- CONSEQUENCE (state change)
- REWARD (meaningful)
- NEXT HOOK

---

## VALIDATION RULES

- GN1: Любой выбор должен иметь различимый результат.
- GN2: Состояния мира фиксируются (State Engine linkage).
- GN3: Fail states должны быть осмысленны (не “game over ради game over”).

---
OWNER: Universe Engine
STATUS: FIXED
