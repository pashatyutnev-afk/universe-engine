# ENG EXPRESSION ENGINES — REALM (FAMILY README)
FILE: 00__README__EXPRESSION_ENGINES.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 05_EXPRESSION_ENGINES
CLASS: EXPRESSION (L3)
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
ROLE: Realm rules + boundaries + interfaces for Expression engines (events, causality, conflict, turning points)

---

## 0) PURPOSE (REALM LAW)

Эта FAMILY владеет **выражением истории как механикой событий**:
не “что это значит” (meaning), не “как это снято” (production),
а **как события устроены** и **как они превращаются в цепочки действия**.

Expression engines отвечают за:
- формирование событий (Event)
- причинно-следственные связи (Cause–Effect)
- конфликт как механизм (Conflict)
- поворотные точки (Turning Point)
- кульминацию (Climax)
- развязку (Resolution)
- системные шоки (System Shock)
- расписание/тайминг событий (Event Scheduling)
- случайность/хаос как управляемый фактор (Randomness & Chaos)

---

## 1) OWNERSHIP (BOUNDARIES)

### THIS FAMILY OWNS
- EVENT MECHANICS: что считается событием и как его формировать
- CAUSAL CHAINS: как строится причинность
- CONFLICT MECHANICS: столкновение сил/интересов как устройство
- TURNING POINTS: изменения состояния системы/героя/мира
- CLIMAX/RESOLUTION: вершина и закрытие “петли”
- SHOCK EVENTS: редкие/разрушающие изменения
- SCHEDULING: порядок и распределение событий во времени истории
- RANDOMNESS: как вводить неопределённость, не ломая канон

### THIS FAMILY DOES NOT OWN
- Темы/смысл/месседж (это `02_DOMAIN_NARRATIVE_ENGINES/10__THEME_MEANING_ENG.md`)
- Пейсинг/ритм story-time (это `02_DOMAIN_NARRATIVE_ENGINES/05__PACING_RHYTHM_ENG.md`)
- Персонажная мотивация/психология/диалог (это `03_DOMAIN_CHARACTER_ENGINES`)
- Законы мира/экономика/тех-стек (это `04_DOMAIN_WORLD_ENGINES`)
- Монтажный/экранный ритм, продакшн-структура (это `08_KNOWLEDGE_PRODUCTION_ENGINES`)

---

## 2) CRITICAL BOUNDARIES (ANTI-DUPLICATION)

### Expression vs Narrative (Structure)
- Narrative domain задаёт “архитектуру истории” (арки, сцены, смысл)
- Expression domain задаёт “механику событий” (цепи, столкновения, переломы)

### Scheduling vs Pacing
- Scheduling = логический порядок событий и их размещение
- Pacing = ощущаемая скорость/напряжение story-time (narrative)

### Conflict vs Power
- Conflict engine = механизм столкновения внутри истории/системы событий
- Conflict & Power (world) = силовые контуры мира как система реальности

---

## 3) CANON ORDER (MANDATORY)

01 — Event Engine  
02 — Cause–Effect Engine  
03 — Conflict Engine  
04 — Turning Point Engine  
05 — Climax Engine  
06 — Resolution Engine  
07 — System Shock Engine  
08 — Event Scheduling Engine  
09 — Randomness & Chaos Engine  

---

## 4) INTERFACES (INPUT/OUTPUT TYPES)

### INPUT TYPES (typical)
- STORY_SEED
- WORLD_CONSTRAINTS (optional)
- CHARACTER_STATE (optional)
- CANON_FACTS (existing)
- SCENE_LIST (optional)

### OUTPUT TYPES (typical)
- EVENT_LIST
- CAUSAL_GRAPH
- CONFLICT_MAP
- TURNING_POINT_SET
- CLIMAX_BLUEPRINT
- RESOLUTION_PLAN
- SHOCK_EVENT_RULES
- EVENT_SCHEDULE
- RANDOMNESS_POLICY

OUTPUT_TARGET (recommended):
- `04_PROJECTS/<project>/03_NARRATIVE/EXPRESSION/`
- `04_PROJECTS/<project>/CANON/NARRATIVE/EXPRESSION/`

---

## 5) DEPENDENCY RULES

- Expression engines могут опираться на:
  - Narrative logic / story structure (как “контекст”)
  - World constraints (что вообще возможно)
  - Character states (кто в каком состоянии)
- Но Expression engines не владеют этими слоями.

---

## 6) REQUIRED LINKS

- Global index: `../02__INDEX_ALL_ENGINES.md`
- Narrative family: `../02_DOMAIN_NARRATIVE_ENGINES/`
- World family: `../04_DOMAIN_WORLD_ENGINES/`
- Governance change control: `../00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md`

---

## 7) AUTHOR RULES (MANDATORY)

- У каждого движка обязателен mini-contract.
- В каждом движке должна быть секция Boundaries.
- Любая “случайность” должна иметь пределы и объяснение, иначе ломает канон.

---

OWNER: Universe Engine
LOCK: OPEN
