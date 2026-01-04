# Geopolitics Engine
FILE: 06__GEOPOLITICS_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 04_DOMAIN_WORLD_ENGINES
LEVEL: L2
STATUS: ACTIVE
VERSION: 1.0
ROLE: Converts world structure + power into geopolitical map, blocs, borders, and strategic behavior

---

## PURPOSE

Строит геополитику:
- границы и их причины
- блоки/альянсы
- стратегические цели государств/сил
- зоны влияния и буферы
- торговые/военные chokepoints

---

## INPUTS

- World Structure Map
- Civilization profiles
- Power matrix + conflicts
- Resource distribution

---

## OUTPUTS

- Influence map (zones)
- Border logic table
- Alliance map
- Strategic objectives list
- Flashpoints list (точки войны)

---

## CANONICAL GEO UNIT

- ACTOR (state/faction)
- CORE INTERESTS (security, resources, prestige, ideology)
- STRATEGY (contain, expand, trade, destabilize)
- ALLIES / RIVALS
- DEPENDENCIES (trade routes, tech, food)
- RED LINES (что нельзя терпеть)
- FLASHPOINTS (где рванёт)

---

## PROCEDURE

1) Identify actors (5–20)
2) For each actor:
   - interests, dependencies, red lines
3) Map alliances and rivalries
4) Place chokepoints and flashpoints
5) Predict likely moves under pressure

---

## VALIDATION RULES

- G1: Границы должны иметь причины (география/культура/сила).
- G2: Альянсы держатся на выгоде или страхе (или и то, и то).
- G3: Зависимости создают драму (энергия/еда/технологии).
- G4: Flashpoints должны быть связаны с ресурсом/идеей/безопасностью.

---

## FAILURE MODES

- геополитика “карта ради карты”
- союзы без интереса
- войны без flashpoints

---

## INTEGRATION

- With WORLD_STRUCTURE_ENG: chokepoints/borders
- With CONFLICT_POWER_ENG: эскалации по flashpoints
- With ECONOMY_RESOURCE_ENG: маршруты и зависимости

---
OWNER: Universe Engine
STATUS: FIXED
