# TOPIC — ADAPTATION PIPELINE (PRODUCTION / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/02__PRODUCTION__ADAPTATION_PIPELINE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.PROD.ADAPTATION_PIPELINE.001
OWNER: SYSTEM
ROLE: Atomic method to adapt one story core into another format (book/series/game) via a deterministic pipeline: invariants, unit mapping, scene transforms, constraints, and QA gates; includes Adaptation Pack template and pass/fail checks

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created adaptation pipeline: core invariants + unit mapping + scene transforms + constraint handling + QA gates and deliverables."
- REASON: "Adaptations fail when the story core drifts or when format constraints are ignored; a pipeline makes changes traceable and consistent."
- IMPACT: "Entities can produce repeatable high-quality adaptations across formats without losing causality or character logic."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.PROD.002

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_production
- type_topic
- adaptation_pipeline
- format_transform
- gate_quality
- maturity_seed

---

## 1) PURPOSE
Дать конвейер адаптации “ядро истории → другой формат” без потери сути:
- что нельзя менять (invariants),
- что можно перестраивать (units/scenes),
- как переносить крючки, повороты, экспозицию, агентность,
- как проверять качество (QA gates).

---

## 2) WHEN TO USE
- Перевод книги в сериал/игру, сериала в книгу, и т.д.
- Нужно сделать “варианты” одной истории для разных платформ.
- Адаптация выглядит как набор случайных перестановок.

## 3) WHEN NOT TO USE
- Ты создаёшь историю с нуля (сначала narrative/world).
- Ты делаешь локальный “пересказ” одной сцены (можно без конвейера).

---

## 4) INPUTS (MINIMUM)
- Source format + исходный материал (core outline).
- Target format (book/series/game).
- Ограничения: длительность, бюджет, интерактивность, рейтинг.
- Ключевые элементы: герой, антагонист, ставки, финал, тема.

## 5) OUTPUTS (MINIMUM)
- Adaptation Pack:
  - Core Invariants
  - Unit Map
  - Transform Rules
  - Risk List
  - QA Gates result (PASS/REWORK/FAIL)

---

## 6) DEFINITIONS (STRICT)
### Invariant
Элемент ядра, который нельзя разрушать:
- центральный конфликт
- мотивация/ценности героя
- причинность ключевых событий
- цена финала (peak cost)
- правила мира (constraints)

### Unit map
Соответствие единиц:
- главы ↔ эпизоды ↔ миссии

### Transform rule
Правило преобразования:
- “экспозиция → действие/артефакт”
- “внутренний монолог → визуальный/поведенческий tell”
- “выбор → интерактивная развилка (game)”

---

## 7) ADAPTATION PIPELINE (STEP-BY-STEP)
### Step 1 — Extract STORY CORE (core sheet)
Заполни:
- Protagonist goal
- Antagonist pressure
- Stakes ladder
- Turning points (3–7)
- Climax choice + peak cost
- Theme statement (1)
Это “ядро”.

### Step 2 — Declare CORE INVARIANTS (5–10)
Список “нельзя ломать”:
- I1..I10

Правило:
- если адаптация ломает invariant — это новая история.

### Step 3 — Create FORMAT CONTRACT (target)
Сделай контракт целевого формата:
- unit type, cadence, deliverables, constraints
(см. topic PRODUCTION FORMAT)

### Step 4 — Build UNIT MAP (source→target)
Сопоставь:
- Source unit ID → Target unit ID(s)
Правила:
- допускается split (1→2) и merge (2→1), но фиксировать явно.
- каждый target-unit должен иметь objective + conflict + state change.

### Step 5 — Apply SCENE TRANSFORMS (toolbox)
Преобразования по типам:

**T1: Internal → External**
- мысли → действия/ошибки/поведенческие tells

**T2: Exposition → Paid reveal**
- “объяснение” → добыча информации (торг/допрос/ошибка/след)

**T3: Pacing shift**
- длинная глава → серия коротких сцен/битов (для сериала)
- сцена → миссия с objective/reward (для игры)

**T4: Agency upgrade (game/interactive)**
- решения героя → игрок делает выбор
- добавить 2–3 meaningful options + costs

**T5: Setups/payoffs redistribution**
- переместить setup раньше, payoff позже, но не ломать причинность

### Step 6 — Constraint reconciliation (reality check)
Проверить:
- бюджет/локации/персонажи
- длительность/темп
- интерактивность/повторяемость (для game)
Если ограничение режет сцену:
- заменить на функциональный эквивалент (same purpose) и записать.

### Step 7 — Risk list (top 7)
Список рисков:
- потеря мотивации героя
- инфо-дамп
- пропажа крючков
- сломанная причинность
- падение stakes
- deus-ex
- формат mismatch

### Step 8 — QA GATES (pass/fail)
Проверить:
- invariants соблюдены
- cadence формата соблюдён
- агентность не упала (а в игре — выросла)
- экспозиция оплачена (no lectures)
- есть state change в каждом unit
Результат:
- PASS / REWORK / FAIL

---

## 8) ADAPTATION PACK TEMPLATE (COPY)
ADAPTATION PACK:
- SOURCE FORMAT:
- TARGET FORMAT:
- STORY CORE:
  - Goal:
  - Antagonist:
  - Stakes:
  - Turning points:
  - Climax + peak cost:
  - Theme:
- CORE INVARIANTS (5–10):
  - I1:
  - I2:
- TARGET FORMAT CONTRACT (summary):
  - Unit type:
  - Cadence:
  - Constraints:
- UNIT MAP (source→target):
  - S1 -> T1/T2:
  - S2 -> T3:
- SCENE TRANSFORM RULES USED:
  - T1:
  - T2:
- CONSTRAINT RECONCILIATION:
  - Cut/Change:
  - Functional equivalent:
- RISK LIST (top 7):
  1)
  2)
- QA GATES:
  - Invariants: PASS/FAIL
  - Cadence: PASS/FAIL
  - Agency: PASS/FAIL
  - Exposition: PASS/FAIL
  - State change per unit: PASS/FAIL
- RESULT: PASS | REWORK | FAIL

---

## 9) QUICK CHECKLIST (PASS/FAIL)
- [ ] есть story core sheet
- [ ] есть 5–10 invariants
- [ ] есть target format contract
- [ ] есть unit map (все target-units покрыты)
- [ ] применены scene transforms (указаны)
- [ ] учтены constraints (с функциональными эквивалентами)
- [ ] есть risk list
- [ ] QA gates заполнены и результат объявлен

PASS IF:
- всё соблюдено

REWORK IF:
- invariants соблюдены, но cadence/agency/exposition слабые

FAIL IF:
- сломана причинность или мотивация, или формат не обслужен

---

## 10) EXAMPLES (MANDATORY)
### 10.1 PASS EXAMPLE (book→series)
Invariant:
- герой получает пропуск ценой метки наблюдения
Transform:
- внутренний страх → визуальные tells и решение в конце эпизода
Cadence:
- cliff на метке наблюдения (конец эпизода)
WHY PASS:
- ядро сохранено, форма усилена.

### 10.2 FAIL EXAMPLE
Адаптация убрала peak cost, финал стал “бесплатным”.
WHY FAIL:
- сломан invariant (цена финала).

---

## 11) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/60_PRODUCTION/01__PRODUCTION__FORMAT_BOOK_SERIES_GAME.md
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/12__NARRATIVE__EXPOSITION_INTEGRATION.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/13__NARRATIVE__CLIMAX_RESOLUTION_PAYOFF.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/10__NARRATIVE__CHARACTER_AGENCY_DECISIONS.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 12) COMPLIANCE
- SOURCE_LOCK: required (core invariants must survive; transforms must be explicit; QA gates mandatory)
- MEMORY: allowed only if meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
