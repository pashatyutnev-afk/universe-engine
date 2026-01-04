# Environment & Ecology Engine
FILE: 10__ENVIRONMENT_ECOLOGY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 04_DOMAIN_WORLD_ENGINES
LEVEL: L2
STATUS: ACTIVE
VERSION: 1.0
ROLE: Models environment, climate, ecology, hazards, and how nature pressures civilizations and stories

---

## PURPOSE

Среда — это давление.
Движок задаёт:
- климат/сезоны/катастрофы
- биомы и ресурсы
- угрозы (болезни, голод, штормы, радиация, существа)
- экологические последствия технологий/магии
- адаптации цивилизаций

---

## INPUTS

- World structure regions
- Resource model
- Tech/magic system
- Timeline epochs (катастрофы/изменения)

---

## OUTPUTS

- Biome map (описательно + функционально)
- Hazard catalog
- Seasonal pressure model
- Adaptation rules by civilization
- Ecology consequences ledger

---

## HAZARD ENTRY (CANON)

- HZ_ID / NAME
- TYPE: climate / bio / geo / anomalous
- FREQUENCY: rare/seasonal/common
- EFFECT: what it does to people/supply/war
- COUNTERS: how to mitigate
- COST: mitigation price
- STORY HOOK: what scenes it creates

---

## PROCEDURE

1) Define key biomes/regions ecology
2) Define 8–20 hazards
3) Define seasonal cycles and their pressures
4) Define adaptation strategies per civilization
5) Define consequences of tech/magic:
   - pollution, depletion, anomalies
6) Produce “pressure hooks”:
   - scarcity, migration, disasters

---

## VALIDATION RULES

- EE1: Среда должна влиять на ресурсы/геополитику/культуру.
- EE2: Угрозы должны иметь counters и цену.
- EE3: Экология меняется от действий цивилизаций (следы).
- EE4: Природа создаёт конфликты, а не только фон.

---

## FAILURE MODES

- климат есть, но ни на что не влияет
- ресурсы не связаны с биомом
- катастрофы без последствий

---

## INTEGRATION

- With ECONOMY_RESOURCE_ENG: дефициты и потоки
- With GEOPOLITICS_ENG: миграции, буферы, границы
- With TIMELINE_EPOCH_ENG: катастрофы как переломы эпох

---
OWNER: Universe Engine
STATUS: FIXED
