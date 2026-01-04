# Tension & Stakes Engine
FILE: 06__TENSION_STAKES_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
LEVEL: L2
STATUS: ACTIVE
VERSION: 1.0
ROLE: Builds stakes model and tension escalator; validates risk and consequence clarity

---

## PURPOSE

Ставки и напряжение — это “двигатель внимания”.
Этот engine гарантирует:
- понятность угроз
- рост/изменение ставки
- цену решений
- ощущение “можно проиграть”

---

## INPUTS

- Main conflict
- Character goals + vulnerabilities
- World constraints
- Scene list draft

---

## OUTPUTS

- Stakes Map:
  - personal stakes
  - relational stakes
  - systemic stakes
  - existential stakes (если нужно)
- Tension Ladder:
  - уровни угрозы по времени
- Consequence Ledger:
  - что будет если проиграют
  - что будет если выиграют

---

## STAKES TYPES

- Personal: жизнь, свобода, здоровье, смысл
- Relational: любовь, доверие, семья, команда
- Status/Power: репутация, власть, позиция
- Systemic: судьба города/мира/цивилизации
- Moral: цена совести, компромисс

---

## TENSION SOURCES

- Uncertainty (неизвестно что будет)
- Time pressure (время)
- Exposure (раскрытие тайны)
- Resource scarcity (ресурсы)
- Opposition competence (умный враг)
- Irreversibility (необратимость)

---

## PROCEDURE

1) Define Stakes Baseline
2) Define “Lose Condition”
3) Place escalation points:
   - stakes increase OR stakes transform (из личного → системное, например)
4) Assign stakes to scenes:
   - каждая сцена должна иметь tension driver
5) Consequence check:
   - последствия должны проявляться, иначе ставки фейковые

---

## VALIDATION RULES

- T1: Ставки должны быть ясны зрителю (или ясность намеренно отсрочена).
- T2: Если проигрыш ничего не меняет — сцена/конфликт фальшивый.
- T3: Эскалация должна быть либо в размере угрозы, либо в цене решения.
- T4: Враг/система должна быть компетентной, иначе нет напряжения.

---

## FAILURE MODES

- “ставки на словах”
- герой не может проиграть
- враг тупой
- угрозы без проявленных последствий

---

## INTEGRATION

- With DRAMATIC_ARC_ENG: напряжение как граф
- With SCENE_CONSTRUCTION_ENG: tension driver в каждой сцене
- With CONFLICT_ENG (Expression): механика конфликта

---
OWNER: Universe Engine
STATUS: FIXED
