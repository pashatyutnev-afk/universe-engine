# TOPIC — ECONOMY & TRADE FLOWS (WORLD / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/06__WORLD__ECONOMY_TRADE_FLOWS.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.WORLD.ECON_TRADE.001
OWNER: SYSTEM
ROLE: Provide an atomic method to build a believable economy as constrained trade flows: goods, routes, costs, chokepoints, pricing drivers, and institutional extraction; includes a flow ledger, pass/fail tests, and drift guards

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created atomic topic for economy/trade: flow ledger + pricing drivers + route constraints + institutional extraction and mismatch audits."
- REASON: "Economies break when goods appear without routes/costs and when prices ignore scarcity/control."
- IMPACT: "Entities can design consistent trade, conflict incentives, smuggling, and price shocks without teleport logic."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.WORLD.006

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
Сделать экономику мира причинной:
- товары не “есть везде”, у них есть источники и маршруты
- цены и дефицит объяснимы
- власть и конфликты вытекают из контроля потоков
- контрабанда/черный рынок — закономерный эффект, а не “фишка”

---

## 2) WHEN TO USE
- Создаёшь региональную экономику, торговые пути, дефициты, войны за ресурсы.
- В истории есть снабжение, караваны, блокада, пошлины, черный рынок.
- “Удобный” товар появляется без логистики и цены.
- Нужно понять, кто богатеет и почему.

## 3) WHEN NOT TO USE
- Ты формализуешь tech level (см. Tech Level Impact).
- Ты описываешь институты власти (см. Institutions & Power Systems).
- Ты описываешь географию/ресурсы (см. Geo & Resource Causality) — сначала туда.

---

## 4) INPUTS (MINIMUM)
- Регионы/узлы (2–6) + ключевые маршруты (routes).
- Ресурсы и товары (5–12) с источниками (source).
- Ограничения: время/вместимость/контроль/риски.
- Институты, которые взимают/контролируют (пошлины/монополии).

## 5) OUTPUTS (MINIMUM)
- TRADE FLOW LEDGER (реестр потоков).
- PRICE DRIVERS (почему именно так стоит).
- SHOCK сценарии (что ломает рынок).
- 2 PASS + 2 FAIL test cases + drift guards.

---

## 6) DEFINITIONS (STRICT)
### Flow
Поток товара/ресурса по маршруту из источника в потребление.

### Price drivers
Факторы цены: scarcity, distance/time, risk, monopoly, tax, seasonality, tech, substitution.

### Extraction
Как власть забирает часть потока: налог, пошлина, монополия, лицензии, реквизии.

### Market mismatch
Несоответствие сцен/лора логистике: товар/цены/объемы не соответствуют constraints.

---

## 7) PROCEDURE (ECONOMY AS FLOWS)
### Step 1 — Pick 5–12 GOODS (mix)
Смешай категории:
- essentials: вода/еда/топливо
- materials: металл/дерево/камень/ткань
- strategic: редкий материал/энергия/данные
- services: ремонт/охрана/перевозка

### Step 2 — For each good, define SOURCE + SUBSTITUTES
Формат:
- Good: X
  - Source: где берётся
  - Substitute: чем можно заменить (если можно)
  - Non-substitutable? YES/NO

### Step 3 — Define 2–4 CONSUMER NODES
Кто потребляет:
- город, армия, производство, элиты, станция, порт.

### Step 4 — Build ROUTE OPTIONS (2 routes per critical good)
Для критического товара:
- Route A: time / cost / capacity / risk / controller
- Route B: time / cost / capacity / risk / controller

### Step 5 — Add EXTRACTION (who takes a cut)
Для каждой связки “good + route + node”:
- tax/passage fee (%)
- monopoly markup
- confiscation risk
- enforcement (как удерживают монополию)

### Step 6 — Compute PRICE DRIVERS (no numbers needed)
Опиши цену как сумму факторов:
- scarcity + distance/time + risk + control + seasonality + substitution

Правило:
- если scarcity LOW и route SAFE, цена не может быть “очень высокой” без монополии/налога.
- если good non-substitutable и controlled, цена становится рычагом власти.

### Step 7 — Create 3 SHOCK SCENARIOS
Шоки обязаны менять цены/конфликты:
- S1: блокада chokepoint
- S2: провал урожая/сезонность/катастрофа
- S3: война/налоговый скачок/потеря охраны

Для каждого:
- что дорожает
- что исчезает
- кто выигрывает/проигрывает
- какие новые преступления/контрмеры появляются

### Step 8 — Mismatch audit (anti-teleport economy)
Проверь лор/сцены:
- товар появляется без source/route → FAIL
- объемы не соответствуют capacity → FAIL
- цена игнорирует risk/control/scarcity → REWORK/FAIL
- черный рынок отсутствует при сильных ограничениях → REWORK (обычно должен появиться)

---

## 8) TRADE FLOW LEDGER FORMAT (COPY)
TRADE FLOW LEDGER (rows = flows):
| FLOW_ID | GOOD | SOURCE NODE | DEST NODE | ROUTE (A/B) | TIME | CAPACITY | RISK | CONTROLLER | EXTRACTION (tax/monopoly) | PRICE DRIVERS | NOTES |
|---|---|---|---|---|---|---|---|---|---|---|---|

SHOCK SCENARIOS:
- S1:
  - Price shift:
  - Winners/Losers:
  - New conflict/crime:
- S2:
- S3:

---

## 9) QUICK CHECKLIST (PASS/FAIL)
- [ ] Есть 5–12 товаров (смешанные категории)
- [ ] Для каждого товара есть source + substitute
- [ ] Есть 2–4 consumer nodes
- [ ] Для критических товаров есть 2 route option с time/capacity/risk/controller
- [ ] Есть extraction (налоги/монополии) и механизм удержания
- [ ] Есть price drivers (объяснение цен)
- [ ] Есть 3 shock scenarios с последствиями
- [ ] Проведён mismatch audit (anti-teleport)

PASS IF:
- все пункты true

REWORK IF:
- есть товары/маршруты, но нет extraction/price drivers/shocks

FAIL IF:
- товары/цены/объемы не привязаны к source/routes/constraints

---

## 10) EXAMPLES (MANDATORY)
### 10.1 PASS EXAMPLE (controlled chokepoint)
GOOD: металл
- Source: шахты на севере (rare)
- Dest: портовый город
Routes:
- A: перевал (2 дня, capacity низкая, controller = клан перевала, tax высокий)
- B: морем (быстрее, но пиратский risk высокий)
Price drivers:
- scarcity (rare) + control (tax/monopoly) + risk (pirates) → металл дорог
Shock:
- блокада перевала → металл резко дорожает, контрабанда морем растёт, клан богатеет/теряет легитимность
WHY PASS:
- цена и конфликт вытекают из маршрутов и контроля.

### 10.2 FAIL EXAMPLE (teleport goods)
Задано:
- металл rare и capacity низкая
В сцене:
- “в городе дешёвый металл в избытке каждую неделю”
WHY FAIL:
- нарушает scarcity + capacity; без нового source/route/tech это невозможно.

---

## 11) COMMON FAILURE MODES
- Failure: “цены как в нашем мире без причин”
  Fix: выписать price drivers и привязать к risk/control/scarcity.
- Failure: “нет extraction”
  Fix: добавить налоги/пошлины/монополии и механизм enforcement.
- Failure: “нет шоков”
  Fix: добавить 3 shock сценария — экономика без шоков мертва.
- Failure: “нет контрабанды при запретах”
  Fix: добавить black-market flows и контрмеры.

---

## 12) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/04__WORLD__GEOGRAPHY_RESOURCE_CAUSALITY.md
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/05__WORLD__INSTITUTIONS_POWER_SYSTEMS.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/03__WORLD__TECH_LEVEL_IMPACT.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/01__WORLD__WORLD_LAWS_CONSTRAINTS.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/02__WORLD__LORE_CONSISTENCY_RULES.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 13) COMPLIANCE
- SOURCE_LOCK: required (no invention beyond KB; this module defines checkable ledgers and audits)
- MEMORY: allowed only if STATE=VERIFIED and meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
