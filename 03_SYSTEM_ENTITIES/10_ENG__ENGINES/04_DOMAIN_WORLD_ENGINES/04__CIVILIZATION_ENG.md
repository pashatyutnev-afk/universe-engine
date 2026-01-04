# Civilization Engine
FILE: 04__CIVILIZATION_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 04_DOMAIN_WORLD_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines civilizations as functional systems (institutions, governance, norms, infrastructure, population, settlement networks, resource flows); produces Civilization Profiles and Network Maps enabling consistent worldbuilding, geopolitics, economy/logistics, and narrative plausibility

---

## PURPOSE

Цивилизация — это “как они живут на самом деле”.
Движок нужен, чтобы:
- общество имело институты и механизмы (не декорации)
- города/поселения образовывали сеть
- власть и нормы объясняли поведение масс
- ресурсы/труд/безопасность работали логично
- цивилизации были различимы и устойчивы в каноне

---

## NON-GOALS

- не описывает географию (World Structure)
- не описывает законы магии/физики (World Law)
- не заменяет Geopolitics (межгосударственные игры)
- не заменяет Economy & Resource (формальный учет потоков)
Он делает **системный профиль цивилизации**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- World Structure Spec (WSS)
- World Law Spec (WLS)
- Timeline & Epoch Registry (TM/ER)
- Tech level notes (from Technology & Magic when available)

### PRODUCES
- CIVILIZATION PROFILE (CP) — canonical artifact
- CIVILIZATION NETWORK MAP (CNM) — settlements + links + dependencies
- INSTITUTION SET (IS)
- SOCIAL CONTRACT MODEL (SCM)
- “CIV INSERTION PROTOCOL” (how to add a new civ)

### DEPENDS_ON
- 04_DOMAIN_WORLD_ENGINES/01__WORLD_STRUCTURE_ENG.md
- 04_DOMAIN_WORLD_ENGINES/03__TIMELINE_EPOCH_ENG.md

### OUTPUT_TARGET
- Feeds:
  - 04_DOMAIN_WORLD_ENGINES/05__CONFLICT_POWER_ENG.md
  - 04_DOMAIN_WORLD_ENGINES/06__GEOPOLITICS_ENG.md
  - 04_DOMAIN_WORLD_ENGINES/07__ECONOMY_RESOURCE_ENG.md
  - Narrative engines (stakes, factions, cities, life)

---

## CANON TERMS

### INSTITUTION
Устойчивая система:
- армия, суд, церковь/культ, гильдия, школа, архив, корпорация, совет

### SOCIAL CONTRACT
Невидимая сделка:
- что люди получают
- что обязаны
- что считается нормой/грехом/предательством

### SETTLEMENT NETWORK
Сеть поселений:
- столица/хабы/приграничные узлы/производственные узлы

### LEGITIMACY
Почему власть считается “правильной”:
- закон, сила, традиция, эффективность, святость

---

## CIVILIZATION TYPES (STANDARD)

- tribal/confederation
- city-state network
- empire
- federation
- corporate-state
- theocracy
- post-collapse enclaves
- “great civilization” (special canon constraints)

---

## CANON CONSTRAINT: GREAT CIVILIZATIONS (NO CURRENCY)

Rule (canon):
- GREAT CIVILIZATIONS do not use currency.
- Exchange is organized as:
  - allocation/quotas
  - reputation/merit
  - access rights
  - duty/service
  - resource scheduling
If a story shows currency in great civ:
- it must be external interface layer
- or black market
- or pre/post epoch change explicitly noted

---

## REQUIRED ARTIFACT A: CIVILIZATION PROFILE (CP)

### CP SCHEMA (CANON)

Header:
- CP_ID:
- CIV_ID:
- NAME:
- EPOCH:
- REGION/LAYER:
- VERSION:
- STATUS:

Identity:
- CIV TYPE:
- CORE MYTH / STORY:
  - what they believe about themselves
- LEGITIMACY SOURCE:
  - tradition | law | force | competence | sacred | tech

Population & Demography:
- POPULATION SCALE:
- URBANIZATION:
  - low | medium | high
- MOBILITY:
  - nomadic | mixed | settled
- HEALTH/REPRODUCTION BASELINE (optional, high-level)

Institutions (mandatory):
- GOVERNANCE:
  - council/king/AI/assembly/etc
- JUSTICE:
  - courts/custom/force
- SECURITY:
  - army/militia/contractors
- KNOWLEDGE:
  - schools/archives/priests
- PRODUCTION:
  - guilds/factories/clans
- FAITH/IDEOLOGY (optional):
- INFORMATION CONTROL (optional):
  - censorship, propaganda, open

Norms & Values:
- HONOR / SHAME:
- VIOLENCE POLICY:
  - taboo | normalized | ritualized
- FAMILY/RELATIONSHIP NORMS:
- STRANGER POLICY:
  - hospitality | suspicion | hostility
- STATUS SYSTEM:
  - class/caste/merit/none

Economy Interface (mandatory, even if “no currency”):
- EXCHANGE MODE:
  - currency | barter | allocation | access-rights | reputation | mixed
- IF NO CURRENCY:
  - allocation authority (who assigns)
  - enforcement mechanism
  - scarcity handling
- RESOURCE PRIORITIES:
  - food, water, energy, tech, labor
- TRADE/CONTACT POLICY:
  - open | controlled | closed

Infrastructure & Logistics:
- TRANSPORT:
- COMMUNICATION:
- ENERGY:
- FOOD SYSTEM:
- WATER SYSTEM:
- HOUSING MODEL:
- MAINTENANCE MODEL:
  - who keeps systems running

Threat Model:
- EXTERNAL THREATS:
- INTERNAL THREATS:
- FAILURE MODES:
  - what collapses them

Canon Locks:
- NON-NEGOTIABLES:
  - 3–10 rules that must persist
- TABOOS:
- “CAN’T EXIST” LIST:
  - tech/social forms forbidden in this epoch

---

## REQUIRED ARTIFACT B: CIVILIZATION NETWORK MAP (CNM)

### CNM SCHEMA (CANON)

Header:
- CNM_ID:
- CIV_ID:
- VERSION:
- STATUS:

Settlement Nodes (repeat):
- NODE_ID:
- NAME:
- TYPE:
  - capital | hub | frontier | mine | farm | shrine | factory | port
- REGION/LAYER:
- POPULATION BAND:
- PRIMARY FUNCTION:
- DEFENSE LEVEL:
- DEPENDENCIES:
  - what it needs from other nodes
- UNIQUE FEATURES:
- CANON TAGS:

Links (repeat):
- LINK_ID:
- FROM_NODE:
- TO_NODE:
- LINK TYPE:
  - road/sea/rail/air/portal
- TIME/COST/RISK:
- CONTROL:
  - who controls the link
- BOTTLENECK FLAG:
  - yes/no

Rule:
- If a city appears in canon scenes, it must be a node (or declared ephemeral outpost).

---

## CIVILIZATION RULES (CANON)

### C1 — Institutions must exist
Если нет институтов, цивилизация не держится.
Минимум:
- управление
- безопасность
- производство/распределение
- знание/передача норм

### C2 — Network must make sense
Города и поселения не “точки на карте”:
- у них функции
- зависимости
- пути

### C3 — Legitimacy explains obedience
Если власть держится на силе — покажи страх.
Если на традиции — покажи ритуалы.
Если на эффективности — покажи результаты.

### C4 — Scarcity handling is mandatory
Как они действуют при нехватке?
Если не прописано — мир ломается при первом кризисе.

### C5 — Great civ currency ban enforced
Если цивилизация “великая”:
- currency forbidden internally
- любые деньги — только внешняя прослойка или криминал

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- cities exist with no food/water/energy model
- large population with no institutions
- empire with no transport/comms baseline
- “no currency” but characters casually buy/sell inside system
- borders/power claims with no legitimacy mechanism

Fix options:
- add missing infrastructure/maintenance models
- define exchange mode and enforcement
- define node functions and dependencies
- mark money use as external/black-market
- align legitimacy and norms

---

## PROCEDURE (HOW TO RUN)

1) Choose civ type + epoch + region
2) Define legitimacy + core myth
3) Define institutions set (minimum required)
4) Define norms and stranger policy
5) Define exchange mode (currency vs no currency)
6) Define infrastructure/logistics baselines
7) Build CNM: nodes + links + bottlenecks
8) Set canon locks and no-go list
9) Sync with geopolitics/economy engines

---

## QC CHECKLIST (MANDATORY)

- CP complete with institutions?
- exchange mode explicit (esp. no currency)?
- infrastructure/logistics defined?
- threat model includes failure modes?
- CNM exists with settlement functions and dependencies?
- canon locks set?

---

## VALIDATION RULES

- CIVV1: CP exists and explains how society functions day-to-day.
- CIVV2: CNM supports plausible settlement interdependence.
- CIVV3: Exchange/scarcity handling prevents “magic economy”.
- CIVV4: Great-civ currency ban enforced when applicable.

---

OWNER: Universe Engine
LOCK: FIXED
