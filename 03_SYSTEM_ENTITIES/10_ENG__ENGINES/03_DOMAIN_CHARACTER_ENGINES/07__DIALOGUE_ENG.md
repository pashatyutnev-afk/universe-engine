# Dialogue Engine
FILE: 07__DIALOGUE_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 03_DOMAIN_CHARACTER_ENGINES
LEVEL: L2
STATUS: ACTIVE
VERSION: 1.0
ROLE: Generates dialogue goals, subtext, conflict, and ensures dialogue changes state

---

## PURPOSE

Диалог — это действие, а не “разговор”.
Engine делает диалоги:
- целевыми (goal-driven)
- конфликтными (внешний/внутренний/межличностный)
- с подтекстом
- меняющими состояние (инфо/отношения/план/ставки)

---

## INPUTS

- Scene card (goal, obstacle, turn)
- Relationship edge profile
- Character voice notes
- Hidden info / secrets

---

## OUTPUTS

- Dialogue Plan:
  - speaker goals
  - tactics
  - subtext
  - turn lines (where it breaks)
- Anti-exposition flags
- Stakes lines (what’s at risk)

---

## DIALOGUE UNIT (CANON)

- GOAL (что хочет говорящий)
- OBSTACLE (почему не получается)
- TACTIC (уговор, давление, стёб, угроза, просьба)
- SUBTEXT (что реально хочет/боится)
- REVEAL/CONCEAL (что выдаёт/прячет)
- TURN LINE (фраза или факт, который меняет сцену)
- COST (что теряет)

---

## PROCEDURE

1) Assign goals for each speaker
2) Choose tactics from behavior policy
3) Encode subtext (value/fear)
4) Place turn line (new info / boundary / insult / confession)
5) Remove exposition:
   - если инфу можно показать действием — не говорить
6) Ensure state delta:
   - диалог должен изменить отношения/план/инфо

---

## VALIDATION RULES

- DLG1: Диалог без цели = пустота.
- DLG2: Каждый обмен должен нести давление (даже мягкое).
- DLG3: Подтекст обязателен в важных сценах.
- DLG4: Экспозиция допустима только если она конфликтна и имеет цену.

---

## FAILURE MODES

- “инфодамп”
- одинаковые голоса у всех
- разговоры без результата
- персонажи говорят то, что не сказали бы

---

## INTEGRATION

- With SPEECH_NATURALIZATION_ENG: звучание естественно
- With RELATIONSHIP_ENG: тактики и доверие
- With SCENE_CONSTRUCTION_ENG: turn и outcome

---
OWNER: Universe Engine
STATUS: FIXED
