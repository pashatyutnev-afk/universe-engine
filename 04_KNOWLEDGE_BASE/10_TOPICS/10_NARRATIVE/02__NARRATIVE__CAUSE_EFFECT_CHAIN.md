# TOPIC — CAUSE–EFFECT CHAIN (NARRATIVE / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/02__NARRATIVE__CAUSE_EFFECT_CHAIN.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.NARR.CAUSE_EFFECT.001
OWNER: SYSTEM
ROLE: Provide a deterministic method to build story as an unbroken chain of cause→effect between scenes; includes tests, failure modes, and rewrite patterns

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created atomic topic for causal chaining: because/therefore/but rule, link labels, and a chain quality gate with PASS/FAIL examples."
- REASON: "Without causality, story becomes a list of events; engagement drops and logic breaks."
- IMPACT: "Scenes become necessary, not arbitrary; easier validation and stronger pacing."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.NARR.002

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_narrative
- type_topic
- causality
- structure
- gate_quality
- rewrite_patterns
- maturity_seed

---

## 1) PURPOSE
Построить историю как цепочку, где каждое событие:
- происходит **потому что** предыдущее случилось, и
- **поэтому** ведёт к следующему,
а не как “и потом ещё вот это”.

---

## 2) CORE PRINCIPLE (LAW)
### 2.1 "AND THEN" IS A WARNING
Если сцены соединяются “и потом…”, цепь слабая.

### 2.2 "BECAUSE / THEREFORE / BUT" RULE
Между сценами должны работать связки:
- **ПОТОМУ ЧТО** (cause)
- **ПОЭТОМУ** (therefore)
- **НО** (complication / reversal)

Если ты не можешь честно вставить эти связки — сцена вероятно лишняя или переписана неправильно.

---

## 3) WHEN TO USE
- История ощущается как набор эпизодов без необходимости.
- Сцены “классные”, но не тянут друг друга.
- Появляются логические дыры (“почему они вдруг тут?”).
- Нужно ускорить/усилить сюжет без добавления нового контента.

## 4) WHEN NOT TO USE
- Ты проектируешь одну сцену отдельно (используй Scene Craft).
- Ты строишь тему/смысл/мораль (это другой модуль).
- Ты решаешь жанровые конвенции (это другой уровень).

---

## 5) INPUTS (MINIMUM)
- Список сцен/битов (хотя бы 5–10 точек)
- Для каждой сцены: цель/конфликт/исход (можно грубо)
- Главная линия угрозы/ставок (на уровне истории)

## 6) OUTPUTS (MINIMUM)
- Причинно-следственная цепочка сцена→сцена
- Для каждой сцены: “почему она неизбежна” (link label)
- Список проблемных звеньев + план фиксов (rewrite patterns)

---

## 7) PROCEDURE (CAUSE–EFFECT CHAIN)
### Step 1 — Write scenes as numbered nodes
S1, S2, S3… (минимум 5)

### Step 2 — For each transition, write a LINK LABEL
Формат:
- `S1 -> S2 : BECAUSE ...`
или
- `S1 -> S2 : THEREFORE ...`
или
- `S1 -> S2 : BUT ...`

Требование: в LINK LABEL должна быть **конкретика**, не абстракция.

Плохо:
- “потому что они решили”
Хорошо:
- “потому что их вычислили по отпечатку, и укрытие стало опасным”

### Step 3 — Run the "AND THEN" test
Прочитай цепь как:
- “S1, И ПОТОМ S2, И ПОТОМ S3…”
Если звучит нормально — значит причинность слабая.

### Step 4 — Apply one of 5 FIX PATTERNS to weak links
Если link label не рождается — выбери фикс:

**Pattern A — MAKE THE CONSEQUENCE EXPLICIT**
- Добавь в исход S1 конкретное последствие, которое вынуждает S2.

**Pattern B — ADD AN ACTIVE FORCE**
- Введи давление: противник/система/срок/ресурс.

**Pattern C — CONVERT A SCENE INTO A CONSEQUENCE**
- Сцена “обсуждения” становится следствием провала/удачи и меняет план.

**Pattern D — MERGE**
- Две сцены без причинности объединяются в одну (экономия времени + рост энергии).

**Pattern E — REORDER**
- Переставь сцены так, чтобы причина стояла раньше эффекта.

### Step 5 — Ensure each scene changes STATE and creates NEXT PRESSURE
Проверка на уровне сцены:
- исход S(i) должен менять положение дел
- и запускать давление для S(i+1)

---

## 8) QUALITY GATE (PASS/FAIL)
### 8.1 Chain must satisfy:
- [ ] У каждого перехода есть LINK LABEL (BECAUSE/THEREFORE/BUT)
- [ ] Нет длинной серии “THEREFORE” без “BUT” (иначе скучно)
- [ ] Нет длинной серии “BUT” без “THEREFORE” (иначе каша)
- [ ] Каждая сцена имеет последствия (next pressure)
- [ ] Удаление одной сцены ломает цепь (иначе она декоративная)

PASS IF:
- цепь читается как “потому что/поэтому/но”, без провалов

FAIL IF:
- много “и потом”
- link labels расплывчатые (“они поговорили/они подумали”)
- сцены можно выкинуть без потерь

---

## 9) EXAMPLES (MANDATORY)
### 9.1 PASS EXAMPLE (mini-chain)
S1: Герой крадёт ключ (успех, но его видит камера)
S2: **BECAUSE** камера записала лицо, служба безопасности блокирует выходы
S3: **THEREFORE** герой вынужден идти через техтоннели
S4: **BUT** в тоннелях он встречает того, кто знает его прошлое и требует услугу
S5: **THEREFORE** герой получает путь наружу ценой нового долга

Почему PASS:
- каждое звено вынуждено предыдущим; есть осложнение (BUT) и цена.

### 9.2 FAIL EXAMPLE (weak chain)
S1: “они едут в город”
S2: “они заходят в бар”
S3: “они встречают человека”
Связка:
- “и потом”
Почему FAIL:
- нет причины, почему именно бар; встречу можно сделать где угодно; сцены не неизбежны.

### 9.3 FIX EXAMPLE (rewrite)
Исходно: “они заходят в бар”
FIX Pattern A:
- S1 исход: “их ищут по официальным входам”
- S2: **THEREFORE** они идут в подпольный бар как в единственный нелегальный вход к информатору
Теперь сцена стала неизбежной.

---

## 10) COMMON FAILURE MODES
- Failure: сцены = “локации” (смена декораций без причин)
  Fix: привязать локацию к ограничению/угрозе/ресурсу.
- Failure: мотивация словами вместо давления
  Fix: добавить внешнее давление (срок, преследование, дефицит).
- Failure: лишняя сцена “пояснение”
  Fix: перенести информацию в конфликт/исход другой сцены или вырезать.

---

## 11) RELATED (PATH ONLY)
REL:
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/01__NARRATIVE__SCENE_CRAFT.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/03__NARRATIVE__TENSION_STAKES.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/04__NARRATIVE__TURNING_POINTS.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/06__NARRATIVE__PACING_RHYTHM.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 12) COMPLIANCE
- SOURCE_LOCK: required (no invention beyond KB; module defines deterministic linking procedure)
- MEMORY: allowed only if STATE=VERIFIED and meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
