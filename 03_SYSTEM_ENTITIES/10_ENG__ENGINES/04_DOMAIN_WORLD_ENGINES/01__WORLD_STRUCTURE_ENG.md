# World Structure Engine
FILE: 01__WORLD_STRUCTURE_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 04_DOMAIN_WORLD_ENGINES
LEVEL: L2
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines structural layers, scale, maps, realms, and navigation logic of the world

---

## PURPOSE

Строит **скелет мира**:
- уровни/слои (реальности, измерения, регионы, сферы влияния)
- масштаб (микро → макро)
- карта сущностей (места, зоны, границы)
- правила перемещения и доступности

---

## INPUTS

- Premise, genre constraints
- Required locations/arenas for story
- Tech/magic baseline (если есть)

---

## OUTPUTS

- World Structure Map (layers + regions)
- Scale Ladder (уровни масштаба)
- Navigation Rules (как/куда можно попасть)
- Structural constraints list

---

## CANONICAL STRUCTURE SPEC

- LAYERS: (physical, political, social, metaphysical…)
- REGIONS: ключевые территории/узлы
- BORDERS: границы и что их держит
- HUBS: столицы/порталы/центры
- CHOKEPOINTS: узкие места (торговля, проходы, сети)
- ACCESS: кто куда может и почему
- SCALE LADDER: local/regional/global/space (если нужно)

---

## PROCEDURE

1) Define layers (минимум 1, максимум сколько надо)
2) Define regions + hubs
3) Define borders + chokepoints
4) Define access rules (ресурсы/статус/технология/магия)
5) Produce constraints:
   - что невозможно в мире по структуре

---

## VALIDATION RULES

- WS1: Каждая “важная зона” должна иметь роль в конфликте/сюжете.
- WS2: Должны существовать chokepoints (иначе мир без трения).
- WS3: Перемещение имеет стоимость (время/риск/ресурс).
- WS4: Масштаб не должен прыгать без перехода.

---

## FAILURE MODES

- мир “плоский фон”
- нет границ → нет геополитики и ставок
- телепорты без цены

---

## INTEGRATION

- With GEOPOLITICS_ENG: границы/узлы → влияние
- With ENVIRONMENT_ECOLOGY_ENG: география и климат давят на структуру
- With TIMELINE_EPOCH_ENG: структура меняется по эпохам

---
OWNER: Universe Engine
STATUS: FIXED
