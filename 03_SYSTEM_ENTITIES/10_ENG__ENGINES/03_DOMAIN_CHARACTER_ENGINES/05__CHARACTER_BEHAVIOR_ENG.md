# Character Behavior Engine
FILE: 05__CHARACTER_BEHAVIOR_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 03_DOMAIN_CHARACTER_ENGINES
LEVEL: L2
STATUS: ACTIVE
VERSION: 1.0
ROLE: Translates motive/value/psyche into observable behavior and decision policy

---

## PURPOSE

Переводит внутреннее (мотивация/ценности/психика) в **поведение**:
- политика решений (decision policy)
- привычки и паттерны
- реакции на давление
- типичные ошибки
- “почерк” действий

---

## INPUTS

- Motivation map
- Value stack
- Psychology profile
- Scene context (stakes, constraints)

---

## OUTPUTS

- Behavior Policy
- Default tactics (3–6)
- Under-pressure variants
- Mistake patterns
- Observable tells (манеры/микро-поведение)

---

## CANONICAL BEHAVIOR POLICY

- DEFAULT STRATEGY: (avoid / confront / negotiate / manipulate / sacrifice / control)
- TOP TACTICS: (конкретные способы)
- RISK STYLE: (risk-seeking / risk-averse / calculated)
- CONFLICT STYLE: (direct / indirect / passive / aggressive)
- TRUST STYLE: (fast/slow; tests)
- LIE STYLE: (if lies: how)
- FAILURE PATTERN: (как ломается)
- RECOVERY PATTERN: (как возвращается)

---

## PROCEDURE

1) Determine default strategy from motive+values
2) Define tactics list
3) Define pressure shift:
   - under fear → what changes
4) Define failure pattern
5) Define recovery pattern
6) Produce “tells” (наблюдаемые маркеры)

---

## VALIDATION RULES

- B1: Поведение должно быть распознаваемым (повторяемость).
- B2: Под давлением меняется форма поведения, но не ядро (или нужен триггер ломки).
- B3: Ошибка должна быть системной (из раны/ценности), а не случайной.
- B4: Тактики ограничены ресурсами и миром.

---

## FAILURE MODES

- персонаж “делает что угодно”
- поведение меняется без причины
- герой всегда принимает лучшее решение

---

## INTEGRATION

- With SCENE_CONSTRUCTION_ENG: цель/тактика/turn
- With CONTINUITY_ENG: поведение не должно нарушать знания/факты
- With RELATIONSHIP_ENG: поведение в связях

---
OWNER: Universe Engine
STATUS: FIXED
