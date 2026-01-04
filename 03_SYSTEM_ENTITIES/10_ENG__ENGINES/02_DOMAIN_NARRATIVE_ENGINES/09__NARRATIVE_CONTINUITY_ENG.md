# Narrative Continuity Engine
FILE: 09__NARRATIVE_CONTINUITY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
LEVEL: L2
STATUS: ACTIVE
VERSION: 1.0
ROLE: Maintains continuity of facts, states, timelines, and character knowledge

---

## PURPOSE

Обеспечивает непрерывность:
- фактов
- времени
- местоположений
- знаний персонажей (“кто что знает когда”)
- состояний отношений и ресурсов

---

## INPUTS

- Canon facts (entities/world rules)
- Timeline
- Scene cards
- Character states/knowledge states

---

## OUTPUTS

- Continuity Ledger:
  - facts
  - constraints
  - resource state
  - relationship state
  - knowledge state
- Error list:
  - contradictions
  - impossible timeline
  - teleportation
  - knowledge leaks

---

## CONTINUITY DIMENSIONS

- Time continuity (сколько времени прошло)
- Space continuity (где кто находится)
- Object continuity (предметы/ресурсы)
- Knowledge continuity (инфа у персонажей)
- Relationship continuity (статусы отношений)
- Rule continuity (законы мира)

---

## PROCEDURE

1) Build Canon Snapshot
2) For each scene:
   - check time delta
   - check location feasibility
   - check objects/resources
   - check who learns what
3) Maintain Knowledge Matrix:
   - персонаж → факт → момент получения
4) Flag contradictions
5) Generate minimal fixes:
   - вставка сцены-перехода
   - перенос события по таймлайну
   - изменение способа получения информации

---

## VALIDATION RULES

- K1: Персонаж не может действовать на основе знания, которого у него нет.
- K2: Нельзя переместиться быстрее законов мира.
- K3: Ресурсы не бесконечны: если потрачены — отмечаем.
- K4: Закон мира не меняется без объяснения/события.

---

## FAILURE MODES

- “он внезапно узнал”
- “они внезапно оказались там”
- “ресурс снова появился”
- “вчера ночь, сегодня снова ночь”

---

## INTEGRATION

- With WORLD Timeline & Law engines: первичная истина времени и правил
- With SCENE_CONSTRUCTION_ENG: scene cards как единицы проверки
- With GOVERNANCE/CONSISTENCY engines: системная консистентность

---
OWNER: Universe Engine
STATUS: FIXED
