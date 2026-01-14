# TOPIC — CONFLICT & GEOPOLITICS CAUSALITY (WORLD / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/07__WORLD__CONFLICT_GEOPOLITICS_CAUSALITY.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.WORLD.CONFLICT_GEO.001
OWNER: SYSTEM
ROLE: Provide an atomic method to build conflicts as causal geopolitics: actors, interests, constraints, leverage points, escalation ladders, and resolution conditions; includes a conflict map card, pass/fail tests, and drift guards

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created atomic topic for conflict/geopolitics causality: interest maps + leverage points + escalation ladder + off-ramps with test cases."
- REASON: "Conflicts feel fake when they lack material constraints and incentives; geopolitics must be explainable through resources, chokepoints, and survival logic."
- IMPACT: "Entities can design believable wars, cold conflicts, alliances, and betrayals without 'because evil' shortcuts."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.WORLD.007

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
Сделать конфликты мира причинными:
- каждый актор имеет интересы и ограничения
- есть рычаги (leverage points): ресурсы/узлы/информация/безопасность
- эскалация не случайна: есть лестница и триггеры
- есть условия деэскалации/мира (off-ramps), иначе “вечная война” без причины

---

## 2) WHEN TO USE
- Вводишь войну, блокаду, холодную войну, партизанщину, санкции, шпионаж.
- Нужно объяснить союзы/предательства.
- География/ресурсы/экономика уже определены и должны порождать борьбу.
- Конфликт в сюжете выглядит натянутым.

## 3) WHEN NOT TO USE
- Ты ещё не определил ресурсы/маршруты/узлы контроля (сначала Geo/Resource + Economy).
- Ты описываешь частный личный конфликт персонажей (это character-level).
- Ты формулируешь конкретные законы мира (это другой topic).

---

## 4) INPUTS (MINIMUM)
- 2–6 акторов (государства/кланы/корпорации/ордена).
- Ресурсы/чокпоинты/инфраструктура, которые можно контролировать.
- Техуровень и ограничения логистики.
- Институты, которые обеспечивают контроль.

## 5) OUTPUTS (MINIMUM)
- CONFLICT MAP CARD (акторы+интересы+рычаги+ограничения).
- Escalation ladder (R1..R4) + triggers.
- Off-ramps (условия деэскалации).
- 2 PASS + 2 FAIL test cases + drift guards.

---

## 6) DEFINITIONS (STRICT)
### Actor
Сторона конфликта с ресурсами, ограничениями и целью (не “народ вообще”).

### Interest
Что актор хочет сохранить/получить:
- безопасность, ресурс, доступ, статус, идеологию, рынки, буфер, выживание.

### Constraint
Что ограничивает актора:
- логистика, дефицит, внутренние элиты, легитимность, технологические ограничения, сезон.

### Leverage point
Рычаг давления:
- chokepoint, ресурс, инфраструктура, информация, заложники, кредиты, союзники.

### Off-ramp
Реалистичный выход из эскалации:
- уступка, гарантия, обмен, автономия, буфер, договор по ресурсу.

---

## 7) PROCEDURE (CONFLICT MAP)
### Step 1 — List ACTORS (2–6)
Для каждого актора:
- name
- core goal (1 строка)
- fear (что потеряет)
- constraint (что мешает)

### Step 2 — Define THE PRIZE (what is fought over)
Выбери 1–3:
- ресурс (вода/энергия/металл/данные)
- chokepoint (перевал/порт/станция)
- инфраструктура (сеть связи/производство)
- безопасность (буферная зона)

### Step 3 — Build INTEREST MAP (why each actor cares)
Для каждого актора:
- Interest A (primary)
- Interest B (secondary)
- Red line (что нельзя потерять)

### Step 4 — Identify LEVERAGE POINTS (3–6)
Свяжи рычаги с географией/экономикой:
- L1: chokepoint control
- L2: trade blockade
- L3: alliance leverage
- L4: sabotage route
- L5: info/blackmail

### Step 5 — Define ESCALATION LADDER (R1..R4)
Лестница должна быть причинной:

- R1: давление низкой интенсивности (пошлины/санкции/провокации)
- R2: силовые инциденты (рейды/диверсии/захват узла)
- R3: открытая война/блокада (масштабный контроль потоков)
- R4: тотальная ставка (точка невозврата: разрушение инфраструктуры/геноцид/ядерный эквивалент)

Для каждого уровня:
- trigger (что включает)
- objective (что хотят добиться)
- cost (что рискуют потерять)

### Step 6 — Add OFF-RAMPS (2–4)
Для каждого off-ramp:
- какой компромисс
- кому выгодно
- почему сейчас возможно (условия)

Правило:
- если нет off-ramps, конфликт должен быть объяснён как “экзистенциальный” с ценой и логикой.

### Step 7 — Resolution conditions (what ends it)
Опиши 1–3 условия завершения:
- ресурс перераспределён
- узел нейтрализован/демилитаризован
- логистика стала невозможной
- смена власти/раскол элит

### Step 8 — Test cases + mismatch audit
PASS: действия акторов соответствуют интересам и constraints.
FAIL: актор действует против интересов без компенсации или игнорирует логистику.

---

## 8) CONFLICT MAP CARD FORMAT (COPY)
CONFLICT MAP CARD:
- CONFLICT NAME:
- PRIZE (1–3):
  - P1:
- ACTORS (2–6):
  - A1:
    - Goal:
    - Fear:
    - Constraint:
    - Red line:
  - A2: ...
- LEVERAGE POINTS (3–6):
  - L1:
  - L2:
- ESCALATION LADDER (R1..R4):
  - R1:
    - Trigger:
    - Objective:
    - Cost:
  - R2:
  - R3:
  - R4:
- OFF-RAMPS (2–4):
  - O1:
  - O2:
- RESOLUTION CONDITIONS (1–3):
  - End 1:
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
- [ ] 2–6 акторов с goal/fear/constraint/red line
- [ ] есть PRIZE (1–3)
- [ ] есть leverage points (3–6) привязанные к географии/экономике
- [ ] есть escalation ladder R1..R4 с trigger/objective/cost
- [ ] есть 2–4 off-ramps
- [ ] есть условия завершения
- [ ] есть 2 PASS + 2 FAIL теста
- [ ] есть drift guards

PASS IF:
- все пункты true

REWORK IF:
- конфликты есть, но нет рычагов/лестницы/выходов

FAIL IF:
- “они воюют потому что плохие” без причин и ограничений

---

## 10) EXAMPLES (MANDATORY)
### 10.1 PASS EXAMPLE (chokepoint war)
PRIZE:
- горный перевал + поток металла
ACTORS:
- A1 (клан перевала): goal = контроль пошлин; fear = потерять власть; constraint = мало людей
- A2 (портовый город): goal = стабильные поставки; fear = голод/дороговизна; constraint = пиратский риск по морю
LEVERAGE:
- блокада перевала, союз с пиратами, диверсия на тропах
ESCALATION:
- R1: поднятие пошлин (trigger = дефицит)
- R2: рейд на караван (trigger = отказ платить)
- R3: блокада и осада (trigger = убийство представителя)
OFF-RAMP:
- гарантированный коридор + фиксированная пошлина + совместная охрана
WHY PASS:
- действия вытекают из потоков, ограничений и интересов.

### 10.2 FAIL EXAMPLE
Задано:
- A2 зависит от перевала (единственный путь)
В сюжете:
- “A2 просто перестаёт покупать и всё нормально”
WHY FAIL:
- игнорируется зависимость/логистика → mismatch.

---

## 11) COMMON FAILURE MODES
- Failure: нет constraints у акторов
  Fix: добавить логистику/внутреннюю политику/ресурсные лимиты.
- Failure: нет off-ramps
  Fix: добавить компромиссы и условия деэскалации.
- Failure: escalation прыгает сразу в R4
  Fix: прописать R1..R3 и триггеры.

---

## 12) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/04__WORLD__GEOGRAPHY_RESOURCE_CAUSALITY.md
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/06__WORLD__ECONOMY_TRADE_FLOWS.md
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/05__WORLD__INSTITUTIONS_POWER_SYSTEMS.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/03__WORLD__TECH_LEVEL_IMPACT.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 13) COMPLIANCE
- SOURCE_LOCK: required (no invention beyond KB; module defines checkable maps/ladders)
- MEMORY: allowed only if STATE=VERIFIED and meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
