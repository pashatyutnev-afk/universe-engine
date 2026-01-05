# ENG DOMAIN WORLD ENGINES — REALM (FAMILY README)
FILE: 00__README__DOMAIN_WORLD_ENGINES.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 04_DOMAIN_WORLD_ENGINES
CLASS: DOMAIN (L2)
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
ROLE: Realm rules + boundaries + interfaces for World domain engines

---

## 0) PURPOSE (REALM LAW)

Эта FAMILY владеет **миром как системой**: как устроена реальность, какие законы в ней действуют,
какие эпохи и шкалы времени, какие цивилизации и структуры власти, как работают ресурсы/экономика,
как устроены технологии (и/или магия), какие мифы/верования формируют картину мира,
и как экология/среда влияет на всё остальное.

World domain отвечает за:
- структуру мира (уровни, слои, география/космос, границы)
- законы мира (физика/соц-законы/магические правила)
- таймлайн и эпохи (историческая сетка мира)
- цивилизации (культура, институты, быт, нормы)
- власть и конфликты (силовые контуры, доминирование, рычаги)
- геополитику (акторы, сферы влияния, союзы, войны)
- экономику и ресурсы (производство, логистика, scarcity/abundance)
- технологии и магию (уровни, ограничения, цена, последствия)
- мифологию и верования (картина мира внутри мира)
- среду и экологию (климат, биомы, риски, устойчивость)

---

## 1) SCOPE (WHAT THIS FAMILY OWNS)

### THIS FAMILY OWNS
- World structure + constraints (где/что возможно)
- World laws (правила реальности)
- Timeline/epochs (как устроено время мира)
- Civilizations (социальные системы)
- Power/conflict systems (кто контролирует что и почему)
- Geopolitics (отношения акторов)
- Economy/resources (ресурсная модель)
- Technology/magic (тех/маг стек и ограничения)
- Belief systems (мифы/религии/идеологии)
- Environment/ecology (среда и последствия)

### THIS FAMILY DOES NOT OWN
- Сюжетные арки, сцены, драматургия (это `02_DOMAIN_NARRATIVE_ENGINES`)
- Персонажная психология/мотивация/речь (это `03_DOMAIN_CHARACTER_ENGINES`)
- Формат выпуска (книга/сериал/игра) (это `07_PRODUCTION_FORMAT_ENGINES`)
- Камера/монтаж/арт/генерация медиа (это `08_KNOWLEDGE_PRODUCTION_ENGINES`)
- Governance pipeline (это `00_GOVERNANCE_ENGINES`)

---

## 2) CRITICAL BOUNDARIES (ANTI-DUPLICATION)

### World Timeline vs Story Timeline
- Таймлайн мира (эпохи, историческая сетка) — World domain
- Таймлайн истории (события сюжета, структура, сцены) — Narrative domain

### Economy vs Plot Stakes
- Экономика/ресурсы как система мира — World domain
- Ставки/напряжение/драм. давление — Narrative domain (с опорой на World constraints)

### Belief Systems vs Theme
- Внутримировые верования/идеологии — World domain
- Авторские темы/смысл/месседж — Narrative domain

---

## 3) CANON ORDER (MANDATORY)

Порядок внутри `04_DOMAIN_WORLD_ENGINES` строгий:

01 — World Structure Engine  
02 — World Law Engine  
03 — Timeline & Epoch Engine  
04 — Civilization Engine  
05 — Conflict & Power Engine  
06 — Geopolitics Engine  
07 — Economy & Resource Engine  
08 — Technology & Magic Engine  
09 — Mythology & Belief Engine  
10 — Environment & Ecology Engine  

---

## 4) INTERFACES (INPUT/OUTPUT TYPES)

### INPUT TYPES (typical)
- WORLD_SEED
- CORE_IDENTITY_SNAPSHOT (опционально)
- CANON_FACTS (existing)
- NARRATIVE_REQUIREMENTS (optional: что нужно для истории)
- CHARACTER_REQUIREMENTS (optional: что нужно для персонажей)

### OUTPUT TYPES (typical)
- WORLD_MODEL
- WORLD_LAWSET
- TIMELINE_EPOCH_GRID
- CIVILIZATION_PROFILES
- POWER_CONFLICT_MAP
- GEOPOLITICS_MAP
- ECONOMY_RESOURCE_MODEL
- TECH_MAGIC_STACK
- BELIEF_SYSTEMS_PACK
- ENV_ECOLOGY_MODEL

OUTPUT_TARGET (recommended):
- `04_PROJECTS/<project>/02_WORLD/`
- `04_PROJECTS/<project>/CANON/WORLD/`

---

## 5) DEPENDENCY RULES

- World engines могут зависеть от:
  - CORE (базовая идентичность проекта/вселенной)
  - GOVERNANCE (для фиксации канона и изменений)
- World engines НЕ зависят от:
  - Production layer (арт/монтаж/генерация)
- Любые изменения “законов мира” обязаны быть отражены в governance.

---

## 6) REQUIRED LINKS

- Global index: `../02__INDEX_ALL_ENGINES.md`
- Narrative family: `../02_DOMAIN_NARRATIVE_ENGINES/`
- Character family: `../03_DOMAIN_CHARACTER_ENGINES/`
- Governance change control: `../00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md`

---

## 7) AUTHOR RULES (MANDATORY)

- Каждый движок обязан иметь mini-contract.
- В каждом движке должна быть секция “Boundaries / Not owned”.
- Нельзя вводить “скрытые” законы мира без фиксации.
- Если World domain вводит ограничения — он должен явно назвать цену/последствия.

---

OWNER: Universe Engine
LOCK: OPEN
