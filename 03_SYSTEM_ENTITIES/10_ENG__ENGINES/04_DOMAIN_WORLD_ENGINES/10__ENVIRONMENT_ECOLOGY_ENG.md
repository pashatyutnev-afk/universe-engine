# Environment & Ecology Engine
FILE: 10__ENVIRONMENT_ECOLOGY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 04_DOMAIN_WORLD_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines environmental reality (climate, biomes, cycles, hazards, ecology, carrying capacity, disease vectors, natural disasters) and how it constrains settlements, logistics, conflict, and resource flows; produces Biome Maps and Hazard Registers ensuring world stability and realistic second-order consequences

---

## PURPOSE

Окружение — это главный “невидимый правитель” мира.
Движок нужен, чтобы:
- биомы и климат были стабильными и объяснимыми
- ресурсы и цивилизации имели экологические пределы (carrying capacity)
- катастрофы/болезни не были “рандомом автора”
- война, логистика и миграции учитывали среду
- изменения среды фиксировались в таймлайне и последствия были реальными

---

## NON-GOALS

- не заменяет World Structure (геометрия мира)
- не заменяет Economy (детальные потоки)
- не заменяет Mythology (смыслы/ритуалы)
Он формализует **экологические и климатические ограничения**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- World Structure + Map Index (WSS/WMI)
- World Law Spec (WLS) (physics, anomalies, seasons)
- Timeline/Epochs (TM/ER)
- Economy/Resource artifacts (RL/FM) (resource coupling)
- Civilization Profiles (settlement patterns)
- Tech/Magic capabilities (CT/TMC) (terraforming, disease control, etc.)

### PRODUCES
- BIOME & CLIMATE MAP (BCM) — canonical artifact
- HAZARD REGISTER (HR) — disasters/diseases/risks
- CARRYING CAPACITY MODEL (CCM) — sustainability limits
- SEASONAL/ENV CYCLE SPEC (SCS)
- “ENV CHANGE” protocol (when ecology shifts)

### DEPENDS_ON
- 04_DOMAIN_WORLD_ENGINES/01__WORLD_STRUCTURE_ENG.md
- 04_DOMAIN_WORLD_ENGINES/02__WORLD_LAW_ENG.md
- 04_DOMAIN_WORLD_ENGINES/07__ECONOMY_RESOURCE_ENG.md

### OUTPUT_TARGET
- Feeds:
  - settlement plausibility
  - war/logistics constraints
  - resource stability and scarcity shocks
  - narrative stakes (storms, famine, plague)
  - continuity (post-disaster world state)

---

## CANON TERMS

### BIOME
Тип среды (лес, степь, пустыня, тундра, океан, подземье, техно-биом).

### CLIMATE REGIME
Устойчивый режим климата: температура/осадки/ветра/сезоны.

### CARRYING CAPACITY
Сколько людей/животных/производства среда выдерживает без коллапса.

### HAZARD
Опасность:
- природная (шторма, землетрясения)
- биологическая (эпидемии)
- хим/радиация (если в мире есть)
- системная (пыльные бури из-за вырубки, опустынивание)

### SECOND-ORDER EFFECTS
Вторичные эффекты:
- миграция, бунты, войны, крах торговли, появление культов

---

## REQUIRED ARTIFACT A: BIOME & CLIMATE MAP (BCM)

### BCM SCHEMA (CANON)

Header:
- BCM_ID:
- WORLD_ID:
- EPOCH:
- VERSION:
- STATUS:

Regions (repeat):
- REGION_ID / LAYER_ID:
- BIOME TYPE:
- CLIMATE REGIME:
  - temp band, precipitation band, wind pattern
- SEASONALITY:
  - none | weak | strong | extreme
- WATER MODEL:
  - rivers, aquifers, ocean currents, rainfall sources
- SOIL/FERTILITY:
  - low/med/high + notes
- KEY SPECIES / ECOSYSTEM NOTES:
- HUMAN VIABILITY:
  - easy | medium | hard | hostile
- INFRASTRUCTURE COST:
  - low/med/high (roads, maintenance)
- KEY CONSTRAINTS:
  - storms, cold, heat, disease, terrain

Rule:
- Every major settlement region must have an entry explaining “why people can live there”.

---

## REQUIRED ARTIFACT B: SEASONAL / ENV CYCLE SPEC (SCS)

### SCS SCHEMA (CANON)

- CYCLE NAME:
  - seasons, monsoon, ash-year, night-cycle, etc.
- PERIOD:
- PHASES:
  - phase 1..n
For each phase:
- ENV CONDITIONS:
- TRAVEL EFFECT:
- AGRICULTURE/FLOW EFFECT:
- DISEASE/HARAZD SHIFT:
- CULTURE/RELIGION HOOK:
  - festivals, taboos, rituals

Rule:
- If the world uses a special cycle (e.g., long winter), it must be here and referenced by economy/conflict.

---

## REQUIRED ARTIFACT C: HAZARD REGISTER (HR)

### HR SCHEMA (CANON)

Header:
- HR_ID:
- WORLD_ID:
- EPOCH:
- VERSION:
- STATUS:

Hazards (repeat):
- HAZARD_ID:
- TYPE:
  - storm | quake | flood | drought | wildfire | plague | infestation | toxic zone | anomaly
- REGION(S):
- FREQUENCY:
  - rare | periodic | seasonal | constant
- EARLY SIGNS:
- IMPACTS:
  - travel, food, water, health, infrastructure
- SEVERITY:
  - low/med/high/catastrophic
- MITIGATION:
  - shelters, medicine, tech/magic counters
- SECOND-ORDER EFFECTS:
  - migration, conflict, black market, coups
- CANON LOCKS:
  - what must be true if it happens

Rule:
- If a hazard is used in plot, it must be registered (or explicitly “unknown anomaly” and then later resolved).

---

## REQUIRED ARTIFACT D: CARRYING CAPACITY MODEL (CCM)

### CCM SCHEMA (CANON)

For each region/biome:
- REGION_ID:
- WATER LIMIT:
- FOOD PRODUCTION LIMIT:
- ENERGY LIMIT (if relevant):
- POPULATION SUSTAINABLE BAND:
- OVERUSE SIGNALS:
  - soil loss, fish collapse, disease, riots
- COLLAPSE THRESHOLD:
- RECOVERY TIME:
- HUMAN/INDUSTRY IMPACT:
  - pollution, deforestation, overhunting
- POLICY/TECH LEVERS:
  - rationing, relocation, terraforming, crop change

Rule:
- “Big city exists” requires a sustainability story: imports, river, tech, or exploitation with consequences.

---

## ECOLOGY RULES (CANON)

### EE1 — Settlements obey environment
Где живут люди = где можно добыть воду/еду/энергию или импортировать.
Если нет объяснения — поселение неканон.

### EE2 — Environment shapes geopolitics
Климат/биомы создают:
- границы
- choke points
- сезонные окна войны
Это должно совпадать с Geopolitics Control Map.

### EE3 — Shocks have second-order effects
Катастрофа/засуха/эпидемия обязана запускать:
- миграции
- дефициты
- конфликты/перевороты
Иначе это “декорация”.

### EE4 — Disease vectors are real
Если есть плотные города/армии/торговля — есть риск эпидемий.
Нужно:
- частота
- условия
- реакция институтов

### EE5 — Tech/Magic can override ecology only with cost
Терраформинг/очистка/контроль погоды:
- только если зарегистрировано в Tech/Magic
- и имеет цену/лимиты/контры

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- desert empire with huge population and no water logistics
- winter world but travel/war happens same as summer
- plague appears/disappears with no vectors or mitigation
- repeated disasters with no permanent changes
- ecology doesn’t affect economy flows (RL/FM)
- terraforming exists but not in CT/TMC or has no cost

Fix options:
- add water model + import routes (FM)
- define seasonal windows and travel costs (SCS)
- register hazard vectors and mitigation capacity (HR)
- enforce state change deltas after disasters (Event engine)
- sync region limits with resource ledger (RL)
- register tech/magic overrides with costs/counters

---

## PROCEDURE (HOW TO RUN)

1) Build biome/climate map per epoch
2) Define seasonal/environment cycles
3) Register hazards with frequency and impacts
4) Define carrying capacity and overuse signals
5) Sync with economy flows, geopolitics control, conflict timing
6) Define “environment change” events in timeline
7) Lock canon constraints and update continuity after shocks

---

## QC CHECKLIST (MANDATORY)

- BCM covers all major regions/settlements?
- SCS defines seasons/cycles used by story?
- HR includes hazards used in canon + mitigation?
- CCM explains big cities and resource sustainability?
- synced with RL/FM and CM/CL?
- tech/magic overrides registered with cost?

---

## VALIDATION RULES

- EEV1: Environment constraints make world physically plausible.
- EEV2: Hazards are systemic and produce lasting consequences.
- EEV3: Carrying capacity prevents “infinite population” nonsense.
- EEV4: Ecology links to economy, geopolitics, and conflict consistently.

---

OWNER: Universe Engine
LOCK: FIXED
