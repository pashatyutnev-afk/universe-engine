# World Structure Engine
FILE: 01__WORLD_STRUCTURE_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 04_DOMAIN_WORLD_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines the structural anatomy of the world (layers, regions, scales, spatial rules, location graph); produces a World Structure Spec and Map Index enabling consistent geography, traversal, constraints, and continuity across narratives and production

---

## PURPOSE

Структура мира — это “скелет”, на котором держится всё:
- где что находится
- как далеко одно от другого
- какие уровни/слои мира существуют (поверхность/орбита/подземка/реальности)
- какие границы и узлы
- где что возможно и невозможно

Движок нужен, чтобы:
- мир не был набором случайных локаций
- путешествия, логистика, войны, экономика, сцены — сходились
- любые новые локации вставлялись без ломания карты

---

## NON-GOALS

- не пишет историю мира (Timeline engine)
- не определяет законы физики/магии (World Law / Tech&Magic)
- не создаёт культуру/цивилизации (Civilization)
Он задаёт **пространственный каркас** и правила масштаба.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- World premise (high-level idea) (optional)
- Story requirements (key places needed by narrative)
- Tech/Travel constraints (from Technology & Magic / World Law when available)

### PRODUCES
- WORLD STRUCTURE SPEC (WSS) — canonical artifact
- WORLD MAP INDEX (WMI) — location registry + graph
- REGION TAXONOMY
- TRAVEL & DISTANCE RULES (structure-level)
- “ADD LOCATION” insertion protocol

### DEPENDS_ON
- 01_CORE_ENGINES (identity/state lifecycle)
- 00_GOVERNANCE_ENGINES (consistency + registry)

### OUTPUT_TARGET
- Feeds:
  - 04_DOMAIN_WORLD_ENGINES/06__GEOPOLITICS_ENG.md (borders + hubs)
  - 04_DOMAIN_WORLD_ENGINES/07__ECONOMY_RESOURCE_ENG.md (routes)
  - 02_DOMAIN_NARRATIVE_ENGINES/04__SCENE_CONSTRUCTION_ENG.md (where scenes happen)
  - 02_DOMAIN_NARRATIVE_ENGINES/09__NARRATIVE_CONTINUITY_ENG.md (location continuity)
  - Production engines (shot planning, travel montage consistency)

---

## CANON TERMS

### WORLD LAYERS
Слои мира (пример):
- surface / orbital / subterranean / oceanic / pocket-realm

### REGION
Крупная область, объединённая:
- климатом
- культурой
- властью
- ландшафтом
- логистикой

### LOCATION NODE
Локация как узел графа:
- город
- база
- руины
- портал
- точка маршрута

### LOCATION GRAPH
Граф переходов:
- пути, порталы, коридоры, морские маршруты, перевалы

### SCALE LOCK
Фиксация масштаба, чтобы “далеко” всегда было далеко.

---

## STRUCTURE AXES (STANDARD)

Мир описывается по осям:

1) SCALE
- micro: room/building
- local: town/zone
- regional: region/country
- global: planet
- supra: system/galaxy (если применимо)

2) LAYERS
- physical layers + special layers

3) CONNECTIVITY
- hub/spoke
- mesh
- gate-based (порталы)
- corridor-based (туннели/перевалы)

4) FRICTION
- travel difficulty:
  - low/medium/high
- what slows movement:
  - terrain/weather/politics/energy

---

## REQUIRED ARTIFACT A: WORLD STRUCTURE SPEC (WSS)

### WSS SCHEMA (CANON)

Header:
- WSS_ID:
- WORLD_ID:
- SCOPE:
- VERSION:
- STATUS:

World Scale Lock:
- PRIMARY SCALE:
  - planet | archipelago | mega-city | system | etc
- DISTANCE BASELINES:
  - typical distances between hubs
- TRAVEL TIME BASELINES:
  - on foot / vehicle / special travel (if any)
- SCALE PROHIBITIONS:
  - what cannot appear (e.g., “no interstellar travel”)

World Layers:
- LAYER LIST (repeat):
  - LAYER_ID:
  - NAME:
  - TYPE:
    - physical | artificial | metaphysical
  - ACCESS RULE:
    - who can enter / how
  - CONSTRAINTS:
    - hazards, limits

Region Taxonomy:
- REGION TIERS:
  - Tier 1: macro-regions
  - Tier 2: sub-regions
- REGION DEFINITIONS (repeat):
  - REGION_ID:
  - LAYER_ID:
  - NAME:
  - BIOME/STRUCTURE:
  - CORE HUBS:
  - BORDER TYPE:
    - natural | political | hostile zone | undefined
  - KEY RESOURCES (optional):
  - KEY CONFLICTS (optional):

Connectivity Model:
- CONNECTIVITY TYPE:
  - mesh | hubs | gates | corridors | mixed
- GLOBAL HUBS:
  - list of hubs
- BOTTLENECKS:
  - choke points
- HARD BLOCKS:
  - closed borders / impassable zones
- TRAVEL FRICTION RULES:
  - what adds cost

Location Graph Rules:
- NODE TYPES:
  - hub | outpost | ruin | gate | capital | wild
- LINK TYPES:
  - road | rail | sea | air | portal | tunnel
- LINK ATTRIBUTES:
  - distance | time | risk | toll | control owner

Add-Location Protocol (mandatory):
- NEW LOCATION must declare:
  - region + layer
  - nearest hub
  - link type(s)
  - travel time baseline match
  - continuity tags

---

## REQUIRED ARTIFACT B: WORLD MAP INDEX (WMI)

### WMI SCHEMA (CANON)

Header:
- WMI_ID:
- WORLD_ID:
- VERSION:
- STATUS:

Node Registry (repeat):
- NODE_ID:
- NAME:
- TYPE:
- LAYER_ID:
- REGION_ID:
- SHORT FUNCTION:
  - why it exists in narrative/world
- OWNER/CONTROL (optional):
- KEY FEATURES:
- HAZARDS:
- “CANON TAGS”:
  - e.g., sacred, restricted, trade hub, ruin

Link Registry (repeat):
- LINK_ID:
- FROM_NODE:
- TO_NODE:
- LINK_TYPE:
- DISTANCE/TIME:
- RISK:
- CONTROL/TOLL (optional):
- NOTES:

Rule:
- Any location used in canon scenes must be registered as NODE (or declared “ephemeral”).

---

## STRUCTURE RULES (CANON)

### WS1 — Scale lock is law
Если расстояния/времена прыгают, мир рушится.
Любое исключение должно быть:
- declared special travel
- or retcon with governance

### WS2 — Every location has function
Локация без функции = мусорная локация.
Функция: конфликт, ресурс, загадка, дом, база, узел пути.

### WS3 — Connectivity must be explicit
Нельзя “они поехали куда-то”.
Должно быть:
- откуда -> куда -> как -> сколько стоит -> риск

### WS4 — Bottlenecks create power
Если есть choke points, они должны:
- влиять на геополитику/экономику
- быть источником конфликтов

### WS5 — Insertions must preserve baselines
Новая локация вставляется только через Add-Location Protocol.
Иначе карта “надувается” хаотично.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- travel time changes scene-to-scene without reason
- regions overlap with no boundaries
- teleport/fast travel appears unannounced
- location appears with no links/hubs
- map has no bottlenecks despite gate/corridor model

Fix options:
- lock baselines in WSS
- add links with distance/time
- declare special travel mechanism (handoff to World Law/Tech)
- define border types and choke points
- register nodes used in scenes into WMI

---

## PROCEDURE (HOW TO RUN)

1) Choose primary scale + baselines (distance/time)
2) Define layers (if any) and access constraints
3) Define region taxonomy (tiers)
4) Choose connectivity model (mesh/hubs/gates/corridors)
5) Define hubs + bottlenecks + hard blocks
6) Build WMI registry:
   - nodes + links with time/risk
7) Enforce Add-Location Protocol for any new location
8) Sync location usage with continuity

---

## QC CHECKLIST (MANDATORY)

- scale lock defined?
- travel baselines defined?
- layers list exists (or declared none)?
- regions have borders + hubs?
- connectivity model explicit?
- WMI has nodes + links for canon places?
- add-location protocol present?

---

## VALIDATION RULES

- WSV1: WSS exists with scale/layers/regions/connectivity.
- WSV2: WMI registers all canon locations and links.
- WSV3: Travel times and scale remain consistent across scenes.
- WSV4: New locations can be inserted without breaking the map.

---

OWNER: Universe Engine
LOCK: FIXED
