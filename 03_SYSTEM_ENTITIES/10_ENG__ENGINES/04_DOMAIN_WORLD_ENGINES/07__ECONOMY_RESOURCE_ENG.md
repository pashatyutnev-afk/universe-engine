# Economy & Resource Engine
FILE: 07__ECONOMY_RESOURCE_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 04_DOMAIN_WORLD_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines economic reality of the world (resources, production, allocation/exchange modes, logistics, scarcity handling, strategic dependencies); produces Resource Ledgers and Flow Maps that keep society, conflict, geopolitics, and daily life plausible and consistent

---

## PURPOSE

Экономика мира — это не “деньги”, а:
- что производится
- кем
- из чего
- как доставляется
- что дефицитно
- кто контролирует узлы и потоки

Движок нужен, чтобы:
- цивилизации были жизнеспособны
- войны имели ресурсные причины и пределы
- торговля/распределение были логичны
- дефицит приводил к последствиям
- “великие цивилизации без валюты” работали системно, а не на словах

---

## NON-GOALS

- не заменяет Civilization (институты/нормы)
- не заменяет Geopolitics (договоры/границы)
- не заменяет Conflict & Power (балансы/эскалация)
Он формализует **ресурсы и потоки**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- World Structure Spec + Map Index (WSS/WMI) (routes/chokepoints)
- Civilization Profiles + Network Maps (CP/CNM)
- Geopolitics Control Map + Treaty Ledger (CM/TAL)
- Conflict & Power artifacts (PM/CL) (war demand)
- Timeline/Epochs (TM/ER)

### PRODUCES
- RESOURCE LEDGER (RL) — canonical artifact
- FLOW MAP (FM) — production -> transit -> consumption graph
- SCARCITY & SHOCK PROTOCOL (SSP)
- ALLOCATION/EXCHANGE MODEL (AEM) per civ/epoch
- STRATEGIC DEPENDENCY LIST (SDL)
- “ECON UPDATE” protocol after big events

### DEPENDS_ON
- 04_DOMAIN_WORLD_ENGINES/04__CIVILIZATION_ENG.md
- 04_DOMAIN_WORLD_ENGINES/06__GEOPOLITICS_ENG.md
- 04_DOMAIN_WORLD_ENGINES/01__WORLD_STRUCTURE_ENG.md

### OUTPUT_TARGET
- Feeds:
  - conflict escalation realism
  - geopolitical leverage (sanctions, blockades)
  - narrative stakes (food/energy shortage, black markets)
  - continuity (supply changes after events)

---

## CANON TERMS

### RESOURCE
Любой ограниченный вход:
- food, water, energy, metals, tech parts, medicine, labor, data, access

### FLOW
Поток ресурса:
- extraction -> processing -> storage -> transport -> distribution -> consumption

### BOTTLENECK
Узел, через который проходит критический поток:
- порт, перевал, ворота, завод, электростанция, маг-узел

### ALLOCATION
Распределение без валюты:
- квоты
- доступы/права
- расписание/бронь
- репутация/заслуги
- обязанность/служба

### BLACK MARKET
Если официальная система распределения есть, подполье почти всегда возникает:
- дефицит
- коррупция
- границы доступа

---

## RESOURCE TAXONOMY (STANDARD)

Core:
- FOOD
- WATER
- ENERGY
- SHELTER/HOUSING
- MEDICINE/HEALTH

Industrial:
- METALS/MINERALS
- FUEL
- PARTS/TOOLS
- CHEMICALS
- MANUFACTURING CAPACITY

Strategic:
- INFORMATION/DATA
- SKILLED LABOR
- TRANSPORT CAPACITY
- SECURITY CAPACITY
- RARE “POWER RESOURCE” (if any)

---

## CANON CONSTRAINT: GREAT CIVS (NO CURRENCY)

Rule:
- Great civilizations do not use currency internally.
They must define:
- allocation authority (who assigns)
- enforcement mechanism
- scarcity handling
- black market posture (tolerate/crackdown/ignore)
- external interface layer (if they trade with currency civs)

---

## REQUIRED ARTIFACT A: RESOURCE LEDGER (RL)

### RL SCHEMA (CANON)

Header:
- RL_ID:
- WORLD_ID:
- EPOCH:
- VERSION:
- STATUS:

Resources (repeat):
- RES_ID:
- NAME:
- CATEGORY:
- SOURCE NODES:
  - WMI/CNM nodes where it comes from
- PROCESSING NODES:
- STORAGE NODES:
- CONSUMPTION NODES:
- RARITY:
  - abundant | constrained | scarce | critical
- SUBSTITUTES:
  - what can replace it
- FAILURE IMPACT:
  - what breaks if missing
- CONTROL:
  - who controls source/bottleneck
- NOTES:
  - seasonality, hazards, spoilage

Strategic Dependencies (mandatory section):
- DEP_ID:
- ACTOR/CIV:
- DEPENDS_ON:
  - resource + node/link
- WHY IT MATTERS:
- VULNERABILITY:
- MITIGATION OPTIONS:
  - stockpile, diversify, conquest, treaty, tech

---

## REQUIRED ARTIFACT B: FLOW MAP (FM)

### FM SCHEMA (CANON)

Header:
- FM_ID:
- WORLD_ID:
- EPOCH:
- VERSION:
- STATUS:

Flows (repeat):
- FLOW_ID:
- RESOURCE:
- FROM (source node):
- VIA (links/bottlenecks):
- TO (sink/consumer node):
- VOLUME BAND:
  - low/med/high (or 0–5)
- TIME LAG:
- RISK:
  - piracy, weather, war, bureaucracy
- CONTROL POINTS:
  - who can disrupt it
- COST MODEL:
  - currency | allocation | barter | access-rights
- FAILURE MODE:
  - what happens if broken

Rule:
- Every “critical” resource must have at least one flow registered.

---

## REQUIRED ARTIFACT C: SCARCITY & SHOCK PROTOCOL (SSP)

### SSP SCHEMA (CANON)

Shock Types:
- blockade
- drought/famine
- sabotage
- war mobilization
- epidemic
- infrastructure collapse
- policy shift (rationing)

For each shock:
- TRIGGER CONDITIONS:
- FIRST-WEEK EFFECTS:
- MONTH EFFECTS:
- SECONDARY EFFECTS:
  - riots, migration, black market, coups
- WHO PROFITS:
- WHO SUFFERS:
- STABILITY THRESHOLD:
  - when system tips into collapse
- RESPONSE PLAYBOOK:
  - rationing, substitution, imports, force

Rule:
- If story uses a shortage as stakes, SSP must predict it.

---

## ALLOCATION/EXCHANGE MODEL (AEM) (PER CIV)

### AEM SCHEMA (CANON)

- CIV_ID:
- MODE:
  - currency | allocation | barter | mixed
- PRIMARY ALLOCATION AUTHORITY:
- ACCESS RIGHTS:
  - how people get access (merit/service/roles)
- ENFORCEMENT:
  - audits, identity, social pressure, police
- PRICING ANALOG (if no currency):
  - quotas, wait-time, reputation points, duty hours
- BLACK MARKET POLICY:
- EXTERNAL TRADE INTERFACE:
  - how they trade with currency systems

---

## ECONOMY RULES (CANON)

### ER1 — Flows define reality
Если нет потоков, нет цивилизации.
Любое “у них есть город” обязано иметь:
- food/water/energy flows
- maintenance model (from civ profile)

### ER2 — Control of bottlenecks is power
Кто контролирует узлы, тот контролирует политику и войну.
Любой bottleneck должен быть отражён:
- в geopolitics control map
- в power map

### ER3 — Scarcity creates behavior
Дефицит порождает:
- заменители
- коррупцию
- подполье
- миграцию
Если это не проявляется — дефицит фальшивый.

### ER4 — No-currency needs enforcement
Если “нет валюты”, то обязателен механизм:
- распределение
- аудит
- санкции
Иначе система превращается в магию.

### ER5 — War demand has limits
Война увеличивает спрос:
- food, fuel, metal, medicine, transport
Если война длится — покажи, что ломается или как они компенсируют.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- empire/army exists with no food/fuel logistics
- “no currency” but people buy/sell normally
- shortages don’t cause black markets or rationing
- resources appear without sources/processing
- flows ignore choke points and control maps
- war continues with no depletion or substitution

Fix options:
- add nodes/links into WMI/CNM
- define allocation authority + enforcement
- register critical flows + bottlenecks
- add substitutes + rationing policy
- sync bottlenecks with geopolitics + power
- apply SSP to predict second-order effects

---

## PROCEDURE (HOW TO RUN)

1) List resources by category and rarity
2) Map sources/processing/storage/consumption nodes
3) Register critical flows with bottlenecks
4) Define AEM per civ (currency vs allocation, etc.)
5) Define strategic dependencies and vulnerabilities
6) Write SSP for major shocks
7) Sync with geopolitics/power/continuity
8) Update after major events (blockades, collapses, new tech)

---

## QC CHECKLIST (MANDATORY)

- RL exists with critical resources + dependencies?
- FM exists with bottlenecks + control points?
- AEM specified for each major civ (esp. no currency)?
- SSP exists for key shock types used in story?
- bottlenecks synced with geopolitics/power?
- war demand limits accounted for?

---

## VALIDATION RULES

- ERV1: RL/FM make settlements and conflict materially plausible.
- ERV2: AEM prevents “handwavy economy” (esp. no-currency civs).
- ERV3: SSP predicts believable second-order effects of scarcity.
- ERV4: Control of flows links to power and geopolitics consistently.

---

OWNER: Universe Engine
LOCK: FIXED
