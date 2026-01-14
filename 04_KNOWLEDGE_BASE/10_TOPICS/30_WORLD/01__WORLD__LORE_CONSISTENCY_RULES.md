# TOPIC — WORLD LAWS & CONSTRAINTS (WORLD / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/01__WORLD__WORLD_LAWS_CONSTRAINTS.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.WORLD.LAWS.001
OWNER: SYSTEM
ROLE: Provide an atomic, actionable method to define world laws as testable rules with constraints, exception cost, and validation cases; prevents rule-less magic and lore drift

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created atomic topic for world laws: rule statement + constraints + exceptions with cost + test cases and a drift guard checklist."
- REASON: "Worldbuilding breaks when rules are vague or mutable; laws must be explicit, constrained, and testable."
- IMPACT: "Entities can create consistent lore, prevent deus-ex solutions, and audit new content against world law constraints."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.WORLD.001

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
Закон мира = проверяемое правило, которое ограничивает решения и делает мир правдивым.
Этот модуль даёт процедуру, как:
- сформулировать закон как правило (rule statement),
- определить ограничения (constraints),
- описать исключения и цену исключений (exception cost),
- создать тест-кейсы (PASS/FAIL),
- защититься от “lore drift”.

---

## 2) WHEN TO USE
- Ты вводишь магию/технологию/силу/феномен и хочешь, чтобы он не ломал мир.
- В сюжете появляется “удобное решение из воздуха”.
- В разных сценах правила работают по-разному.

## 3) WHEN NOT TO USE
- Ты проектируешь цивилизацию/культуру (это другой topic).
- Ты делаешь географию/ресурсы/экономику (другой topic).
- Ты фиксируешь терминологию (reference realm).

---

## 4) INPUTS (MINIMUM)
- Феномен/система, которую вводим (магия/технология/соц-правило/экология).
- Что этот феномен “умеет делать” (capability).
- Какие задачи он может “сломать”, если без ограничений.

## 5) OUTPUTS (MINIMUM)
- World Law Card (rule + constraints + exceptions + cost).
- 2 PASS + 2 FAIL test cases.
- Drift guard checklist для будущих сцен.

---

## 6) DEFINITIONS (STRICT)
### Rule statement
Одно предложение формата “IF/THEN”.

### Constraint
Ограничение: что запрещено/дорого/невозможно.

### Exception
Исключение: редкий случай, когда правило нарушается.

### Exception cost
Цена исключения: что платится и почему это не “бесплатная кнопка”.

### Test case
Проверка: пример применения, который должен пройти/провалиться.

---

## 7) PROCEDURE (WORLD LAW CARD)
### Step 1 — Write RULE STATEMENT (IF/THEN)
Формат:
- “Если ___ (условие), то ___ (эффект), иначе ___ (нет эффекта).”

Правила:
- одно правило = один эффект (не свалка)
- избегать “в целом/обычно/может быть”

### Step 2 — Define 3 CONSTRAINTS (minimum)
Для эффекта выпиши минимум 3 ограничения:
- C1: ресурс/стоимость (энергия/время/материал/риск)
- C2: условие доступа (кто может/где/когда)
- C3: побочный эффект (side effect) или риск

### Step 3 — Define 0–2 EXCEPTIONS (only if needed)
Если исключения нужны — выпиши максимум 2:
- E1: ...
- E2: ...

Если исключения “много” — закон плохой или слишком общий.

### Step 4 — Define EXCEPTION COST (mandatory if exceptions exist)
Для каждого исключения:
- “Цена: ___”
Цена должна:
- быть высокой/редкой/ограничивающей
- оставлять последствия (необратимость или долг)

### Step 5 — Add FORBIDDEN USES (anti-deus list)
Выпиши 3 запрета:
- F1: нельзя использовать для “решения главной проблемы без цены”
- F2: нельзя отменять смерть/потерю без заранее заданной цены
- F3: нельзя делать эффект бесконечно/без ресурса

### Step 6 — Create TEST CASES (2 PASS + 2 FAIL)
PASS тесты:
- соответствуют правилу и ограничениям
FAIL тесты:
- нарушают хотя бы 1 constraint или forbidden use

### Step 7 — Drift guard (future audit)
Определи “что проверять всегда”:
- “Не добавили ли новую способность?”
- “Не убрали ли цену?”
- “Не появилось ли скрытое исключение?”

---

## 8) WORLD LAW CARD FORMAT (COPY)
WORLD LAW CARD:
- RULE:
- CONSTRAINTS:
  - C1:
  - C2:
  - C3:
- EXCEPTIONS (optional):
  - E1:
- EXCEPTION COST (if exceptions):
  - Cost:
- FORBIDDEN USES:
  - F1:
  - F2:
  - F3:
- TEST CASES:
  - PASS 1:
  - PASS 2:
  - FAIL 1:
  - FAIL 2:
- DRIFT GUARD:
  - Check 1:
  - Check 2:
  - Check 3:

---

## 9) QUICK CHECKLIST (PASS/FAIL)
- [ ] RULE формата IF/THEN и однозначен
- [ ] Есть минимум 3 constraints
- [ ] Исключений максимум 2 (или нет)
- [ ] Если есть исключение — есть exception cost
- [ ] Есть forbidden uses (anti-deus)
- [ ] Есть 2 PASS + 2 FAIL test cases
- [ ] Есть drift guard (3 проверки)

PASS IF:
- все пункты true

REWORK IF:
- правила понятны, но constraints или тесты слабые

FAIL IF:
- “сила без ограничений” или исключения без цены

---

## 10) EXAMPLES (MANDATORY)
### 10.1 PASS EXAMPLE (resource + access + side effect)
WORLD LAW CARD:
- RULE: “Если устройство подключено к ядру станции, то оно может открывать один закрытый шлюз на 10 секунд; иначе шлюз не открывается.”
- CONSTRAINTS:
  - C1: требует редкий ключ-канал (расходуется)
  - C2: работает только на территории станции
  - C3: запуск поднимает локальную тревогу
- EXCEPTIONS:
  - E1: “аварийный режим” открывает шлюз без ключа
- EXCEPTION COST:
  - Cost: “в аварийном режиме выгорает блок управления и сектор блокируется навсегда”
- FORBIDDEN USES:
  - F1: нельзя открывать “всё подряд”
  - F2: нельзя делать бесшумно
  - F3: нельзя использовать вне станции
- TEST CASES:
  - PASS: герой открывает один шлюз, но тревога начинается
  - PASS: герой не может открыть шлюз вне станции
  - FAIL: герой пытается открыть три шлюза подряд без ключа
  - FAIL: герой пытается открыть “главный шлюз” без последствий
WHY PASS:
- ограничения и цена исключения защищают от читерства.

### 10.2 FAIL EXAMPLE (rule-less magic)
LAW:
- “У героя есть сила открывать любые двери когда угодно.”
WHY FAIL:
- нет constraints, нет цены, нет тестов → deus-ex.

---

## 11) COMMON FAILURE MODES
- Failure: “правило слишком общее”
  Fix: сузить правило до одной функции/эффекта.
- Failure: “исключений много”
  Fix: убрать исключения, или разделить на 2 разных закона.
- Failure: “цены нет”
  Fix: добавить resource + side effect + последствия.
- Failure: “нет тестов”
  Fix: написать 2 PASS и 2 FAIL как обязательную валидацию.

---

## 12) RELATED (PATH ONLY)
REL:
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/02__WORLD__LORE_CONSISTENCY_RULES.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/03__WORLD__TECH_LEVEL_IMPACT.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/04__WORLD__GEOGRAPHY_RESOURCE_CAUSALITY.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 13) COMPLIANCE
- SOURCE_LOCK: required (no invention beyond KB; this module defines a checkable procedure and card)
- MEMORY: allowed only if STATE=VERIFIED and meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
