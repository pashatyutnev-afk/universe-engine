# TOPIC — GEOGRAPHY & RESOURCE CAUSALITY (WORLD / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/04__WORLD__GEOGRAPHY_RESOURCE_CAUSALITY.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.WORLD.GEO_RES_CAUSALITY.001
OWNER: SYSTEM
ROLE: Provide an atomic method to make geography and resources causally enforceable through constraints, access, logistics, and conflict consequences; includes a geo-resource map card, pass/fail tests, and drift guards

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created atomic topic for geography/resource causality: map card + constraints + logistics/consequence derivation and mismatch audit."
- REASON: "Worlds break when geography is decorative; terrain and resources must constrain movement, economy, and power."
- IMPACT: "Entities can design believable logistics and conflicts; prevents 'teleport economies' and map drift."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.WORLD.004

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_world
- type_topic
- skill_procedure
- gate_quality
- maturity_seed

---

## 1) PURPOSE
Сделать географию и ресурсы **причинными**, а не декоративными:
- где можно жить и почему
- как реально перемещаются люди/товары
- что является дефицитом и что это меняет
- какие точки неизбежно становятся узлами власти/конфликта

---

## 2) WHEN TO USE
- Создаёшь регион/карту/маршрут/город/границу.
- В истории есть путешествия, войны, торговля, снабжение.
- Появляется “телепортационная экономика”: всё есть везде без причин.
- Конфликты не связаны с землёй/ресурсами.

## 3) WHEN NOT TO USE
- Ты формализуешь технологические возможности (см. Tech Level Impact).
- Ты формулируешь закон мира (см. World Laws & Constraints).
- Ты проектируешь институты/политику (см. Institutions & Power Systems — следующий модуль).

---

## 4) INPUTS (MINIMUM)
- Регион/узел (название, тип: город/пустыня/порт/перевал/шахта/река/станция).
- Ключевые ресурсы (3–7).
- Барьеры (terrain, climate, hazards).
- Доступные технологии/транспорт (по техуровню).

## 5) OUTPUTS (MINIMUM)
- GEO-RESOURCE MAP CARD (карточка региона/узла).
- Логистические ограничения (routes + costs + time).
- Вторичные эффекты: власть/конфликт/экономика/быт.
- 2 PASS + 2 FAIL test cases + drift guards.

---

## 6) DEFINITIONS (STRICT)
### Resource
То, что ограничивает развитие/войну/власть:
- вода, еда, энергия, металлы, редкие материалы, данные, безопасные зоны, рабочая сила.

### Constraint
Ограничение, которое делает мир “жёстким”:
- время, расстояние, сезонность, инфраструктура, риск, пропускная способность, контроль.

### Route
Конкретный путь снабжения/перемещения с ценой и уязвимостью.

### Chokepoint
Узел/проход, который концентрирует поток (перевал, мост, порт, ворота, станция).

---

## 7) PROCEDURE (GEO-RESOURCE CAUSAL MAP)
### Step 1 — Define the REGION NODE
Заполни:
- Node type: city / port / mine / pass / river / station / frontier / wasteland
- Population viability: почему тут можно/нельзя жить (вода/почвы/тепло/защита)

### Step 2 — List 3–7 KEY RESOURCES
Для каждого ресурса:
- source: где добывается/получается
- scarcity: abundant / limited / rare
- dependency: от чего зависит (сезон/инфраструктура/охрана)
- substitute: чем можно заменить (если можно)

### Step 3 — Define 3 CONSTRAINTS (minimum)
Ограничения должны быть жёсткими и проверяемыми:
- C1: distance/time (сколько реально идти/ехать)
- C2: capacity (сколько можно перевезти/пропустить)
- C3: risk/control (кто контролирует, какие угрозы)

### Step 4 — Build ROUTE MAP (at least 2 routes)
Опиши минимум 2 маршрута:
- Route A: быстрый/дорогой/опасный
- Route B: медленный/дешевле/скрытный
Для каждого:
- time
- cost
- capacity
- failure mode (что ломает маршрут)

### Step 5 — Identify 1–3 CHOKEPOINTS
- какие точки контролируют потоки
- что произойдёт, если chokepoint перекроют

### Step 6 — Derive SECOND-ORDER EFFECTS (minimum 8)
Вывести последствия:
- Economy: что выгодно/дорого
- Power: кто контролирует chokepoints/resources
- Conflict: за что воюют/давят
- Culture: какие привычки/правила рождаются
- Crime: контрабанда/пиратство/подделка
- Daily life: рацион, вода, топливо, транспорт, жильё

Формат:
- “Если ресурс X редок и route A уязвим, то …”

### Step 7 — Mismatch audit (anti-teleport checks)
Проверь в сценах/лоре:
- не перемещается ли армия/товар “быстрее маршрутов”
- не появляется ли ресурс “без source”
- не игнорируется ли сезон/погода/контроль chokepoints
Если да — REWORK или ввод контрмер/закона/техобъяснения.

---

## 8) GEO-RESOURCE MAP CARD FORMAT (COPY)
GEO-RESOURCE MAP CARD:
- REGION NODE:
  - Type:
  - Viability:
- KEY RESOURCES (3–7):
  - R1:
    - Source:
    - Scarcity:
    - Dependency:
    - Substitute:
- CONSTRAINTS:
  - C1:
  - C2:
  - C3:
- ROUTES (2+):
  - Route A:
    - Time:
    - Cost:
    - Capacity:
    - Failure mode:
  - Route B:
    - Time:
    - Cost:
    - Capacity:
    - Failure mode:
- CHOKEPOINTS (1–3):
  - CP1:
- SECOND-ORDER EFFECTS (8+):
  1)
  2)
- TEST CASES:
  - PASS 1:
  - PASS 2:
  - FAIL 1:
  - FAIL 2:
- DRIFT GUARDS (2+):
  - Guard 1:
  - Guard 2:

---

## 9) QUICK CHECKLIST (PASS/FAIL)
- [ ] Есть REGION NODE + viability (почему тут можно жить)
- [ ] Есть 3–7 ресурсов с source/scarcity/dependency
- [ ] Есть 3 constraints (time/capacity/risk-control)
- [ ] Есть 2 routes с time/cost/capacity/failure
- [ ] Есть 1–3 chokepoints
- [ ] Есть 8+ second-order effects
- [ ] Есть 2 PASS + 2 FAIL test cases
- [ ] Есть drift guards

PASS IF:
- все пункты true

REWORK IF:
- есть карта, но нет логистики/ограничений/последствий

FAIL IF:
- география декоративна и не ограничивает действия

---

## 10) EXAMPLES (MANDATORY)
### 10.1 PASS EXAMPLE (port + choke)
REGION NODE:
- Type: port city
- Viability: вода + рыба + защищённая бухта; вокруг скалы
RESOURCES:
- R1: питьевая вода (limited; зависит от источника в горах)
- R2: соль (abundant; береговые выпарки)
- R3: металл (rare; привозной, зависит от караванов)
CONSTRAINTS:
- C1: в горы 2 дня пешком, зимой 4 дня
- C2: перевал пропускает только 10 телег/день
- C3: перевал контролирует клан, берёт пошлину
ROUTES:
- A: морем быстро, но пиратский риск высокий
- B: через перевал медленно, но стабильнее при охране
CHOKEPOINT:
- перевал (перекрытие = голод/рост цен)
SECOND-ORDER:
- власть у клана перевала; контрабанда по морю; металл дорог; культура экономии воды
WHY PASS:
- логистика и контроль создают экономику и конфликт, ничего не “телепортируется”.

### 10.2 FAIL EXAMPLE (teleport economy)
Задано:
- вода limited и перевал узкий
В сцене:
- “каждый день в город приходит огромный караван без задержек и пошлин”
WHY FAIL:
- нарушает capacity/control constraints → mismatch.

---

## 11) COMMON FAILURE MODES
- Failure: ресурсы без источника
  Fix: указать source + dependency.
- Failure: маршруты без времени/пропускной способности
  Fix: добавить time/capacity и failure mode.
- Failure: chokepoint не влияет на власть
  Fix: вывести вторичные эффекты (кто контролирует и как).

---

## 12) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/03__WORLD__TECH_LEVEL_IMPACT.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/01__WORLD__WORLD_LAWS_CONSTRAINTS.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/02__WORLD__LORE_CONSISTENCY_RULES.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/05__WORLD__INSTITUTIONS_POWER_SYSTEMS.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 13) COMPLIANCE
- SOURCE_LOCK: required (no invention beyond KB; this module defines a checkable mapping procedure)
- MEMORY: allowed only if STATE=VERIFIED and meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
