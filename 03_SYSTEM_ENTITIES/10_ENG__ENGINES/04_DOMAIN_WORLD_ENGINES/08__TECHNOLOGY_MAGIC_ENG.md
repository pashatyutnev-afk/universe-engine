# Technology & Magic Engine
FILE: 08__TECHNOLOGY_MAGIC_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 04_DOMAIN_WORLD_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines technology/magic capability system (tiers, constraints, costs, failure modes, counters, progression, availability by epoch/region); produces Capability Trees and Tech/Magic Catalogs that keep solutions, conflict, production, and world logic consistent and non-cheaty

---

## PURPOSE

Технология/магия — это “инструменты решения проблем”.
Движок нужен, чтобы:
- возможности были формализованы (не “вдруг получилось”)
- решения не ломали ставки (цена/лимиты/контры)
- было понятно: кто чем реально владеет и почему
- прогресс был привязан к эпохам, ресурсам, институтам
- изображение/эффекты в медиа были согласованы

---

## NON-GOALS

- не определяет базовые законы причинности (World Law)
- не описывает политику/власть (Geopolitics / Conflict&Power)
- не описывает экономику потоков (Economy&Resource)
Он описывает **набор возможностей и их параметры**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- World Law Spec + Exception Registry (WLS/ERX)
- Timeline & Epoch Registry (TM/ER)
- Civilization Profiles (institutions, education, production)
- Economy/Resource artifacts (RL/FM) (inputs and constraints)
- World Structure (layers/regions) (where it can exist)

### PRODUCES
- CAPABILITY TREE (CT) — canonical artifact
- TECH/MAGIC CATALOG (TMC) — items/systems registry
- AVAILABILITY MATRIX (AM) — who has what, where, when
- COST/FAILURE/CHECKS RULESET (CFC)
- COUNTER SYSTEM (CS)
- “INTRODUCE NEW TECH/MAGIC” protocol

### DEPENDS_ON
- 04_DOMAIN_WORLD_ENGINES/02__WORLD_LAW_ENG.md
- 04_DOMAIN_WORLD_ENGINES/03__TIMELINE_EPOCH_ENG.md
- 04_DOMAIN_WORLD_ENGINES/07__ECONOMY_RESOURCE_ENG.md

### OUTPUT_TARGET
- Feeds:
  - conflict (weapons, deterrence, asymmetry)
  - geopolitics (tech dependency, access)
  - narrative (solutions and limitations)
  - knowledge production (visual depiction, VFX rules)
  - continuity (capability locks)

---

## CANON TERMS

### CAPABILITY
Функция, которую можно применить:
- healing, stealth, fast-travel, energy projection, fabrication, sensing, memory edit, etc.

### TIER
Уровень мощности/сложности, с:
- требуемыми ресурсами
- лимитами
- рисками

### COST
Цена применения/владения:
- ресурс, время, редкость, мораль, деградация, риск обнаружения

### FAILURE MODE
Как ломается:
- перегрев, откат, заражение, шум, зависимость, коррупция, поломка

### COUNTER
Контр-механизм:
- защита, подавление, детектор, анти-материал, ритуал, протокол

---

## TECH/MAGIC MODES (STANDARD)

- TECHNOLOGY (engineering-based)
- MAGIC (rule-based power)
- HYBRID (tech + magic)
- BIO (biotech/organic)
- INFORMATIONAL (memetics, cognition, data manipulation)

Rule:
- Mode must align with World Law causality constraints.

---

## TIERING STANDARD

### Suggested tier labels (choose one set)
Option A (simple):
- T0: mundane
- T1: advanced
- T2: exceptional
- T3: frontier
- T4: paradigm-shift

Option B (world-specific):
- define custom labels, but keep 5 levels max.

---

## REQUIRED ARTIFACT A: CAPABILITY TREE (CT)

### CT SCHEMA (CANON)

Header:
- CT_ID:
- WORLD_ID:
- MODE:
  - tech | magic | hybrid | mixed
- VERSION:
- STATUS:

Capabilities (repeat):
- CAP_ID:
- NAME:
- MODE:
- TIER:
- WHAT IT DOES (one sentence):
- INPUTS:
  - resource/skill/conditions
- LIMITS:
  - range, duration, precision, cooldown, access
- COST:
- CONSEQUENCES:
- FAILURE MODES:
- DETECTION SIGNATURE:
  - how others can notice it
- COUNTERS:
  - list of COUNTER_ID or description
- PREREQUISITES:
  - required CAP_IDs / institutions / resources
- FORBIDDEN IN:
  - epochs/regions/layers where it cannot exist
- NARRATIVE SAFETY:
  - why it won’t trivialize stakes

Rule:
- Any “problem-solver” capability must have strong limits/cost/counter.

---

## REQUIRED ARTIFACT B: TECH/MAGIC CATALOG (TMC)

### TMC SCHEMA (CANON)

Header:
- TMC_ID:
- WORLD_ID:
- VERSION:
- STATUS:

Items/Systems (repeat):
- ITEM_ID:
- NAME:
- TYPE:
  - device | ritual | organism | facility | protocol | artifact
- CAPABILITIES PROVIDED:
  - CAP_ID list
- REQUIRED INPUTS:
- OPERATORS:
  - who can use it
- BUILD/MAINTAIN REQUIREMENTS:
  - parts, skills, institutions
- RELIABILITY:
  - stable | fragile | experimental | cursed
- FAILURE MODES:
- COUNTERS/DEFENSES:
- VISUAL/AUDIO SIGNATURE:
  - depiction rules for production
- CANON LOCK:
  - immutable constraints
- SECURITY CLASS:
  - public | restricted | secret | forbidden

Rule:
- If an artifact/system appears in canon scenes, it must be cataloged (or explicitly “unknown/one-off”).

---

## REQUIRED ARTIFACT C: AVAILABILITY MATRIX (AM)

### AM SCHEMA (CANON)

Matrix entries (repeat):
- ENTRY_ID:
- CAP_ID / ITEM_ID:
- WHO HAS IT:
  - ACTOR_ID / CIV_ID
- WHERE:
  - region/layer/node
- WHEN:
  - epoch/time window
- ACCESS MODE:
  - public | controlled | rare | black market | myth-only
- COST TO ACQUIRE:
  - money | allocation | duty | risk | quest
- WHY THEY HAVE IT:
  - resources, institutions, treaties, conquest
- DEPENDENCIES:
  - critical flows or chokepoints (RL/FM links)

Rule:
- Availability must not contradict economy/industry/education.

---

## REQUIRED ARTIFACT D: COST/FAILURE/CHECKS RULESET (CFC)

### CFC SCHEMA (CANON)

For each tier/mode:
- ACTIVATION CHECK:
  - skill/condition requirement
- COST TYPES:
- FAILURE TYPES:
- ESCALATION RISK:
  - repeated use makes it worse?
- MAINTENANCE POLICY:
  - who fixes it, how often

Rule:
- Repeated use must produce fatigue/maintenance demand unless explicitly “free” by world law (rare).

---

## REQUIRED ARTIFACT E: COUNTER SYSTEM (CS)

### CS SCHEMA (CANON)

Counters (repeat):
- COUNTER_ID:
- NAME:
- WHAT IT STOPS:
  - CAP_ID list
- HOW IT WORKS:
- LIMITS:
- COST:
- WHO CAN DEPLOY:
- DETECTION:
- WHY IT EXISTS:
  - prevents invincible powers

Rule:
- Every high-tier capability must have at least one counter.

---

## TECH/MAGIC RULES (CANON)

### TM1 — Must obey World Law
Если capability нарушает WLS:
- либо запрещено
- либо это exception из ERX (и тогда регистрируется)

### TM2 — No free solutions
Любой “читерский” инструмент обязан иметь:
- жесткие лимиты
- цену
- и/или контр-систему

### TM3 — Availability must be earned
Если цивилизация имеет высокую тех/маг штуку:
- должна иметь ресурсы/институты/логистику
Иначе это сказка.

### TM4 — Progress ties to epochs
Уровни должны быть связаны с эпохами.
“Сверх-тех в каменном веке” возможно только как:
- руины/наследие
- внешняя интервенция
- единичный артефакт (с ограничениями)

### TM5 — Depiction lock for production
Чтобы медиа-артефакты были consistent:
- у каждой ключевой технологии/магии есть signature
- визуальные правила (цвет, форма, звук, эффект)

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- a capability trivializes major stakes with no cost/counter
- tech appears without supply/maintenance chain
- availability contradicts geopolitics control (e.g., blocked resource)
- repeated use has no fatigue/maintenance
- counter never works (invincible power)
- “unknown” capability used as plot solve

Fix options:
- add limits/costs and enforce them in scenes
- add maintenance inputs tied to RL/FM
- move availability to restricted/rare and explain access
- add counter system and show it being used
- register as ERX exception or forbid

---

## PROCEDURE (HOW TO RUN)

1) Choose mode (tech/magic/hybrid) and tier system
2) Draft capability tree (start with 10–30 core capabilities)
3) Create catalog entries for any on-screen systems
4) Build availability matrix by epoch/region/actor
5) Define cost/failure/checks per tier
6) Define counters for high-tier capabilities
7) Sync with economy/flows and geopolitics control
8) Lock canon and route changes via governance

---

## QC CHECKLIST (MANDATORY)

- CT exists with limits/cost/counters?
- TMC exists for used artifacts/systems?
- AM ties availability to resources/institutions/epochs?
- CFC defines fatigue/maintenance and failure?
- CS exists and prevents invincible powers?
- WLS/ERX compliance checked?

---

## VALIDATION RULES

- TMV1: Capabilities are bounded and non-cheaty.
- TMV2: Availability is plausible and epoch-linked.
- TMV3: Costs/failures/counters preserve stakes and balance.
- TMV4: Depiction signatures enable consistent media production.

---

OWNER: Universe Engine
LOCK: FIXED
