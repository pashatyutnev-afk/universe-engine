# TOPIC — TECHNOLOGY / MAGIC FRAME (WORLD / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/10__WORLD__TECHNOLOGY_MAGIC_FRAME.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.WORLD.TECH_MAGIC_FRAME.001
OWNER: SYSTEM
ROLE: Provide an atomic method to define a world’s “power system” (technology or magic) as a constrained, testable mechanism: effects, costs, access, risks, countermeasures, and anti-deus rules; includes a System Card, pass/fail tests, and drift guards

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created atomic topic for tech/magic systems: effect catalog + constraint matrix + countermeasures + test cases to prevent deus-ex solutions."
- REASON: "Power systems break worlds when they are undefined or unlimited; constraints create drama and consistent problem-solving."
- IMPACT: "Entities can design systems that generate conflicts and solutions without breaking lore consistency."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.WORLD.010

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
Определить “силовую систему” мира (технологию или магию) так, чтобы:
- эффекты были ясны и ограничены,
- цена и риски были реальными,
- доступ был контролируем,
- существовали контрмеры,
- любое применение было проверяемо тест-кейсами,
- исключить deus-ex (“спасли потому что можно”).

---

## 2) WHEN TO USE
- Вводишь магию/пси/сверхтехнологию/артефакты/систему сил.
- Нужно, чтобы система генерировала драму, а не отменяла её.
- В истории появляются “удобные” решения без цены.

## 3) WHEN NOT TO USE
- Ты фиксируешь отдельный закон мира (см. World Laws & Constraints) — сначала рамка системы, потом отдельные laws.
- Ты делаешь tech-level матрицу на уровне общества (см. Tech Level Impact) — здесь механика силы.

---

## 4) INPUTS (MINIMUM)
- Название системы (что это).
- 3–7 базовых эффектов, которые она даёт.
- Контекст мира: ресурсы/институты/угрозы.

## 5) OUTPUTS (MINIMUM)
- POWER SYSTEM CARD (эффекты/ограничения/стоимость/доступ/контрмеры).
- 2 PASS + 2 FAIL test cases.
- Drift guards (как система не “ползёт” к всемогуществу).

---

## 6) DEFINITIONS (STRICT)
### Effect
Наблюдаемый результат (“делает X”), а не “в целом усиливает”.

### Cost
Что тратится/теряется при применении (ресурс/время/здоровье/репутация/риск).

### Access
Кто/где/когда может применять (инфраструктура, талант, лицензия, артефакт).

### Risk / Side effect
Побочный эффект: следы, откат, заражение, поломка, тревога, моральная цена.

### Countermeasure
Как этому сопротивляются (технологически, социально, институционально).

---

## 7) PROCEDURE (POWER SYSTEM CARD)
### Step 1 — Define SYSTEM IDENTITY (one paragraph)
- “Что это такое” (физика/ритуал/устройство/сеть/пси-эффект)
- почему существует (источник/происхождение)
- где границы (что это НЕ делает)

### Step 2 — List 3–7 CORE EFFECTS (verbs)
Формат:
- E1: “позволяет ___ при условиях ___”
- E2: …

Правило:
- эффект = один понятный результат.

### Step 3 — Constraint matrix (minimum 5 constraints)
Минимум 5 ограничений (лучше 7):
- C1: Resource (что расходуется)
- C2: Time (сколько длится)
- C3: Range/Distance (дальность)
- C4: Precision (точность/ошибка)
- C5: Access (кто может)
- C6: Infrastructure (где работает)
- C7: Detection (следы/тревога)

### Step 4 — Define COSTS (minimum 3)
Цена должна быть ощутимой:
- ресурс/деньги/здоровье/репутация/долг/время/риск войны

### Step 5 — Define RISKS / SIDE EFFECTS (minimum 3)
- R1: …
- R2: …
- R3: …

### Step 6 — Define COUNTERMEASURES (minimum 3)
Как мир защищается:
- CM1: техническая защита
- CM2: социальная/правовая
- CM3: тактическая (обход/обман/экранирование)

### Step 7 — Anti-deus rules (forbidden uses)
Запреты (минимум 4):
- F1: нельзя решать главную проблему без цены
- F2: нельзя отменять смерть/потери без заранее заданной цены и следа
- F3: нельзя бесконечно масштабировать эффект без инфраструктуры/ресурса
- F4: нельзя “появлять” новую способность без нового закона/версии

### Step 8 — Test cases (2 PASS + 2 FAIL)
PASS: применение в рамках constraints/cost/risk.
FAIL: попытка использовать систему как чит-кнопку.

### Step 9 — Drift guards (3+)
- Guard 1: новые эффекты добавлять только через отдельный law card + тесты
- Guard 2: стоимость не снижать без объяснения и последствий
- Guard 3: доступ не расширять без институционального/технологического сдвига

---

## 8) POWER SYSTEM CARD FORMAT (COPY)
POWER SYSTEM CARD:
- SYSTEM NAME:
- IDENTITY (what it is / what it is not):
- CORE EFFECTS (3–7):
  - E1:
  - E2:
- CONSTRAINT MATRIX (5–7):
  - C1 Resource:
  - C2 Time:
  - C3 Range:
  - C4 Precision:
  - C5 Access:
  - C6 Infrastructure:
  - C7 Detection:
- COSTS (3+):
  - Cost 1:
- RISKS / SIDE EFFECTS (3+):
  - Risk 1:
- COUNTERMEASURES (3+):
  - CM1:
  - CM2:
  - CM3:
- FORBIDDEN USES (4+):
  - F1:
  - F2:
  - F3:
  - F4:
- TEST CASES:
  - PASS 1:
  - PASS 2:
  - FAIL 1:
  - FAIL 2:
- DRIFT GUARDS (3+):
  - G1:
  - G2:
  - G3:

---

## 9) QUICK CHECKLIST (PASS/FAIL)
- [ ] Есть 3–7 core effects
- [ ] Есть 5–7 constraints
- [ ] Есть 3+ costs
- [ ] Есть 3+ risks
- [ ] Есть 3+ countermeasures
- [ ] Есть 4+ forbidden uses
- [ ] Есть 2 PASS + 2 FAIL теста
- [ ] Есть 3+ drift guards

PASS IF:
- все пункты true

REWORK IF:
- эффекты есть, но нет цены/контрмер/запретов

FAIL IF:
- система может “всё” или растёт без контроля

---

## 10) EXAMPLES (MANDATORY)
### 10.1 PASS EXAMPLE (restricted gateway)
SYSTEM:
- “Шлюзовая сеть” открывает проходы на 10 секунд.
CONSTRAINTS:
- работает только на узлах инфраструктуры
- требует ключ-канал (расходуется)
- срабатывание поднимает тревогу
COUNTERMEASURES:
- блокировка узлов, ловушки, контроль ключей
FAIL CASE:
- “открыть проход где угодно без узла и бесшумно” → FAIL (нарушение инфраструктуры + detection).
WHY PASS:
- есть цена, ограничения и защита мира.

### 10.2 FAIL EXAMPLE (unbounded magic)
SYSTEM:
- “маг может сделать всё, если сильно захочет”
WHY FAIL:
- нет эффектов/ограничений/контрмер — deus-ex.

---

## 11) COMMON FAILURE MODES
- Failure: эффекты слишком широкие
  Fix: дробить на отдельные эффекты (E1..E7) и ограничивать каждый.
- Failure: нет контрмер
  Fix: мир всегда отвечает на силу — иначе это чит.
- Failure: стоимость символическая
  Fix: добавить цену, которая меняет поведение/политику/экономику.
- Failure: “новая способность в середине”
  Fix: запрет (F4) + отдельный law topic с тестами.

---

## 12) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/01__WORLD__WORLD_LAWS_CONSTRAINTS.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/02__WORLD__LORE_CONSISTENCY_RULES.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/03__WORLD__TECH_LEVEL_IMPACT.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 13) COMPLIANCE
- SOURCE_LOCK: required (module enforces constrained, testable design; discourages decorative invention)
- MEMORY: allowed only if meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
