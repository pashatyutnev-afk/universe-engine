# TOPIC — MOTIVATION & DESIRE (CHARACTER / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/20_CHARACTER/01__CHARACTER__MOTIVATION_DESIRE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.CHAR.MOTIVATION.001
OWNER: SYSTEM
ROLE: Provide an atomic, actionable method to define a character’s WANT/NEED/FEAR and the PRICE they will pay; includes pass/fail examples and a quick audit checklist

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created atomic topic for character motivation: WANT/NEED/FEAR/PRICE framework and a procedure to test behavior under pressure."
- REASON: "Characters feel fake when actions are not anchored in desire and fear; this module makes motivation auditable."
- IMPACT: "Entities can build consistent character actions and avoid cardboard behavior by using a deterministic motivation card."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.CHAR.001

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_character
- type_topic
- skill_procedure
- gate_quality
- maturity_seed

---

## 1) PURPOSE
Дать процедуру, как формализовать мотивацию персонажа так, чтобы:
- действия были объяснимы,
- выборы имели цену,
- поведение под давлением было предсказуемо (внутренне согласовано).

Используется модель:
- WANT (чего хочет сейчас)
- NEED (что ему нужно на глубинном уровне)
- FEAR (чего он боится потерять/узнать/стать)
- PRICE (какую цену он готов платить)

---

## 2) WHEN TO USE
- Персонаж ведёт себя “как надо сюжету”, а не как человек.
- Сцены с героем не имеют внутренней логики выбора.
- Нужно сделать героя активным (agency) и понятным.

## 3) WHEN NOT TO USE
- Ты описываешь внешний сеттинг/мир (не character-level).
- Ты пишешь чисто комедийный скетч без психологии (если таков стиль — отдельные правила жанра).
- Ты оцениваешь качество диалогов/голоса (это отдельный topic).

---

## 4) INPUTS (MINIMUM)
- Кто персонаж (роль в истории).
- Контекст: что на кону в текущей линии.
- Оппозиция/угроза (кто/что мешает).

## 5) OUTPUTS (MINIMUM)
- Motivation Card (WANT/NEED/FEAR/PRICE).
- 1–3 “pressure tests” (как он ведёт себя под давлением).
- Решение PASS/REWORK/FAIL по мотивации.

---

## 6) PROCEDURE (MOTIVATION CARD)
### Step 1 — Write WANT (surface goal, now)
Формат: “Я хочу ___ (конкретное действие/результат)”.
Правило:
- WANT должен быть наблюдаемым (что он делает ради этого).

### Step 2 — Write NEED (deep need, identity-level)
Формат: “Мне нужно ___ (безопасность/признание/свобода/любовь/контроль/принадлежность/смысл…)”.
Правило:
- NEED объясняет, почему WANT важен.

### Step 3 — Write FEAR (loss/identity threat)
Формат: “Я боюсь ___ (потерять/быть раскрытым/оказаться никем/быть отвергнутым…)”.
Правило:
- FEAR должен реально тормозить и искажать поведение.

### Step 4 — Define PRICE (what they will pay)
Формат: “Ради WANT я готов ___ (рисковать/лгать/предать/страдать/потерять…)”.
Правило:
- PRICE должен быть конкретным и проверяемым в сценах.

### Step 5 — Define LIMIT (what they will NOT do)
Формат: “Я НЕ сделаю ___ даже ради WANT”.
Это создаёт ценности/границы (и драму, когда границы ломаются).

### Step 6 — Pressure tests (3 scenarios)
Смоделируй 3 “давления”:
- TEST A: короткий дедлайн / угроза
- TEST B: моральный выбор (ценность vs выгода)
- TEST C: риск разоблачения / потеря лица
И запиши:
- “в такой ситуации он сделает ___ потому что WANT/FEAR/PRICE”.

### Step 7 — Scene linkage (make it usable)
Для будущих сцен фиксируем:
- триггеры, которые включают FEAR
- ресурсы, которые герой считает “ценой”
- типичная тактика (обман/давление/уход/атака/торг)

---

## 7) QUICK CHECKLIST (PASS/FAIL)
- [ ] WANT конкретен и наблюдаем
- [ ] NEED объясняет важность WANT
- [ ] FEAR реально влияет на поведение (не “для красоты”)
- [ ] PRICE конкретен (что отдаёт/чем рискует)
- [ ] Есть LIMIT (граница)
- [ ] Есть 3 pressure tests с логикой “потому что”
- [ ] Можно предсказать выбор героя в сцене из этих полей

PASS IF:
- все пункты true

REWORK IF:
- WANT есть, но нет FEAR/PRICE, и выборы не предсказуемы

FAIL IF:
- мотивация размыта (“хочет счастья”) или не влияет на действия

---

## 8) EXAMPLES (MANDATORY)
### 8.1 PASS EXAMPLE
Motivation Card:
- WANT: “получить доступ к закрытому сектору сегодня”
- NEED: “доказать, что я не трус и не ошибка”
- FEAR: “быть разоблачённым как самозванец”
- PRICE: “готов рисковать свободой и лгать”
- LIMIT: “не предам единственного друга”
Pressure tests:
- Deadline: он пойдёт на подлог, потому что FEAR сильнее закона.
- Moral: если предложат сдать друга — откажется, даже если потеряет доступ (LIMIT).
- Exposure: будет агрессивно контролировать ситуацию и давить, чтобы скрыть слабость.
WHY PASS:
- WANT/NEED/FEAR/PRICE связаны и прогнозируют выборы.

### 8.2 FAIL EXAMPLE
Motivation Card:
- WANT: “быть счастливым”
- NEED: “жить хорошо”
- FEAR: “плохого”
- PRICE: “не знаю”
WHY FAIL:
- нет конкретики, нет цены, нельзя предсказать действия.

### 8.3 EDGE EXAMPLE (quiet character)
Motivation Card:
- WANT: “не говорить правду в разговоре”
- NEED: “сохранить контроль”
- FEAR: “быть отвергнутым”
- PRICE: “готов потерять доверие”
- LIMIT: “не унижу другого публично”
WHY EDGE:
- WANT не “внешний квест”, но всё равно наблюдаем (молчание/уклонение) и даёт драму.

---

## 9) COMMON FAILURE MODES
- Failure: WANT = “поговорить”
  Fix: превратить в действие/результат (получить согласие / скрыть факт / добиться уступки).
- Failure: FEAR декоративный
  Fix: привязать FEAR к конкретным триггерам и поведению.
- Failure: PRICE отсутствует
  Fix: зафиксировать, что герой реально теряет/чем рискует.
- Failure: LIMIT отсутствует
  Fix: ввести границу; иначе герой становится “всемогущим” или беспринципным без причины.

---

## 10) RELATED (PATH ONLY)
REL:
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/20_CHARACTER/02__CHARACTER__WOUND_TRAUMA.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/20_CHARACTER/03__CHARACTER__VALUES_MORAL_COMPASS.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/20_CHARACTER/04__CHARACTER__BEHAVIOR_UNDER_PRESSURE.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/20_CHARACTER/05__CHARACTER__CHARACTER_ARC.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 11) COMPLIANCE
- SOURCE_LOCK: required (no invention beyond KB; this module defines a checkable procedure)
- MEMORY: allowed only if STATE=VERIFIED and meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
