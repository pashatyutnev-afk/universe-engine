# Pacing & Rhythm Engine
FILE: 05__PACING_RHYTHM_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
LEVEL: L2
STATUS: ACTIVE
VERSION: 1.0
ROLE: Controls narrative tempo, density, and rhythm of escalation/release

---

## PURPOSE

Управляет темпом истории как **распределением плотности**:
- сколько “событийной массы” на отрезок
- где ускорение, где торможение
- как чередуются напряжение и дыхание
- как поддерживается интерес (микро-хуки)

---

## INPUTS

- Scene list + scene cards
- Dramatic arc graph
- Format constraints (эпизод/глава/серия)

---

## OUTPUTS

- Pacing Plan:
  - density map
  - scene length targets
  - valley/peak alternation
- Flags:
  - drag zones (провисания)
  - overload zones (перегруз)

---

## METRICS (SIMPLE BUT CANON)

- Event density: событий/изменений на сцену/главу
- Turn frequency: как часто происходит “перелом”
- Rest ratio: доля сцен разрядки
- Hook continuity: есть ли “крючок” на переходах

---

## PROCEDURE

1) Segment into Units (acts/episodes)
2) Compute Density per Unit
3) Place Valleys intentionally:
   - “дыхание” должно давать:
     - новую инфу / план / эмоциональный смысл
4) Ensure Hook chain:
   - каждая сцена должна оставлять вопрос/напряжение/ожидание
5) Fix Drag Zones:
   - объединить сцены
   - поднять стоимость
   - вставить turn
6) Fix Overload:
   - добавить паузу с функцией
   - выкинуть повтор

---

## VALIDATION RULES

- P1: Если 2+ сцены подряд без turn и без state delta — провисание.
- P2: Если 3+ сцены подряд “пик” без разрядки — усталость.
- P3: Разрядка без функции запрещена.
- P4: Темп должен соответствовать формату (серия ≠ книга).

---

## FAILURE MODES

- “болото” в середине
- равномерная монотонность
- перегруз событиями (ничего не успевает значить)
- отсутствие крючков

---

## INTEGRATION

- With DRAMATIC_ARC_ENG: пики/спады
- With SCENE_CONSTRUCTION_ENG: turn и state delta
- With PRODUCTION_FORMAT engines: длины и правила формата

---
OWNER: Universe Engine
STATUS: FIXED
