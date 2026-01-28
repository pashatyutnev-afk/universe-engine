# TOPIC — DIALOGUE & SUBTEXT (NARRATIVE / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/07__NARRATIVE__DIALOGUE_SUBTEXT.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.NARR.DIALOGUE_SUBTEXT.001
OWNER: SYSTEM
ROLE: Provide an atomic method to write dialogue as action with subtext: goal, obstacle, power, hidden agenda, and state change; includes a Dialogue Beat Card, pass/fail tests, and a rewrite toolkit

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created atomic topic for dialogue/subtext: dialogue-as-action, subtext mapping, power moves, and beat-level structure with audit gates."
- REASON: "Dialogue fails when it is information dumping or 'chatting'. Subtext and power create tension and narrative movement."
- IMPACT: "Entities can produce sharper scenes, reduce exposition dumps, and maintain character consistency through dialogue mechanics."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.NARR.007

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_narrative
- type_topic
- skill_procedure
- gate_quality
- maturity_seed

---

## 1) PURPOSE
Диалог — это действие, а не разговор.
Этот модуль даёт процедуру, как писать диалог так, чтобы:
- у каждого участника была цель,
- был подтекст (скрытый мотив),
- была борьба за власть/рамку,
- реплики меняли состояние сцены (state change),
- информация выдавалась через конфликт, а не через “лекцию”.

---

## 2) WHEN TO USE
- Диалоги скучные, “плоские”, похожи на пояснения автора.
- Персонажи говорят то, что они и так знают (exposition dump).
- Сцена должна изменить отношения/решение/доступ, но выходит “болтовня”.

## 3) WHEN NOT TO USE
- Ты проектируешь общий каркас сцены (см. Scene Craft) — сначала цель/конфликт/исход.
- Ты строишь причинность между сценами (см. Cause–Effect Chain).
- Ты делаешь речь/дикцию/стилизацию голоса (это отдельный модуль).

---

## 4) INPUTS (MINIMUM)
- Контекст сцены: цель героя, ставки, оппозиция.
- Два (или больше) участника диалога.
- Что каждый хочет получить/избежать.
- Что каждый скрывает или не может сказать прямо.

## 5) OUTPUTS (MINIMUM)
- Dialogue Beat Card (на 1 диалоговый отрезок).
- 3–7 диалоговых битов (beats) с изменением давления/силы.
- PASS/REWORK/FAIL по “диалог двигает сцену”.

---

## 6) DEFINITIONS (STRICT)
### Dialogue as action
Реплика = попытка изменить другого/ситуацию (получить уступку, доступ, правду, время).

### Subtext
Что персонаж на самом деле делает репликой:
- просит, угрожает, проверяет, манипулирует, защищается, торгуется, избегает.

### Frame / Power
Кто задаёт правила разговора:
- тему, темп, границы, кто кому должен объясняться.

### Beat
Микро-изменение: новая информация, смена тактики, рост давления, переворот позиции.

---

## 7) CORE PRINCIPLES (STRICT)
1) **Каждый диалог должен иметь результат** (state change).
2) **Прямые слова ≠ истинный мотив** (subtext обязателен, если есть конфликт).
3) **Вопросы = оружие** (контроль рамки).
4) **Экспозиция должна быть “платной”**: за правду платят ценой/риском/уступкой.
5) **Повтор запрещён**: если реплика не меняет давление/позицию — она лишняя.

---

## 8) PROCEDURE (DIALOGUE BEAT DESIGN)
### Step 1 — Define TALK GOALS (for each speaker)
Для каждого:
- GOAL (что получить)
- FEAR (что нельзя допустить)
- LEVER (чем давит/что предлагает)

### Step 2 — Define SUBTEXT (one verb per speaker)
Выбери глагол:
- test / probe / threaten / charm / bargain / stall / mislead / confess / recruit / shame

### Step 3 — Define POWER STATE (before)
Кто сверху?
- Power: A > B, или A = B
Почему:
- ресурс/доступ/знание/статус/оружие/время

### Step 4 — Build 3–7 BEATS
Каждый beat должен включать:
- Move (ход): реплика как действие (что делает)
- Counter (ответ): сопротивление
- Shift (сдвиг): что изменилось (инфо/власть/доступ/отношение)

Обязательное правило:
- минимум 1 “BUT” (осложнение) в середине (см. cause/effect).

### Step 5 — Insert “PRICE OF TRUTH” (if exposition occurs)
Если нужна информация, то:
- кто-то платит (уступкой, риском, компроматом, потерей лица)
Иначе это dump.

### Step 6 — Define TURN (micro-turn)
Момент, где разговор меняет направление:
- раскрытие,
- угрозы,
- смена рамки (“ты тут не судья”),
- новая ставка.

### Step 7 — Define OUTCOME (state change)
К концу диалога обязательно:
- уступка / отказ / новая цель / новая угроза / потеря доверия / доступ открыт/закрыт.

---

## 9) DIALOGUE BEAT CARD FORMAT (COPY)
DIALOGUE BEAT CARD:
- CONTEXT:
- SPEAKERS:
  - A:
    - Goal:
    - Fear:
    - Lever:
    - Subtext verb:
  - B:
    - Goal:
    - Fear:
    - Lever:
    - Subtext verb:
- POWER STATE (before):
- BEATS (3–7):
  - Beat 1:
    - A move:
    - B counter:
    - Shift:
  - Beat 2:
    - ...
- PRICE OF TRUTH (if any):
- MICRO-TURN:
- OUTCOME (state change):
- PASS/FAIL NOTES:

---

## 10) QUICK CHECKLIST (PASS/FAIL)
- [ ] У каждого участника есть Goal/Fear/Lever
- [ ] У каждого есть subtext verb (что он делает репликами)
- [ ] Есть 3–7 beats, и каждый beat даёт shift
- [ ] Есть micro-turn
- [ ] Диалог заканчивается state change
- [ ] Экспозиция (если есть) “платная”
- [ ] Нет повторяющихся реплик без нового давления

PASS IF:
- все пункты true

REWORK IF:
- диалог имеет цель, но beats слабые или нет цены за правду

FAIL IF:
- “они просто поговорили”, сцена не изменилась, диалог = лекция

---

## 11) REWRITE TOOLKIT (FIX PATTERNS)
- Fix A: **Cut greetings / start late**
  Начинать ближе к конфликту.
- Fix B: **Turn statements into tactics**
  Вместо “я боюсь” → действия: уход, нападение, давление, торг.
- Fix C: **Add a lever**
  Дай персонажу ресурс/угрозу/доступ, чтобы у разговора была ставка.
- Fix D: **Pay for information**
  Пусть правда стоит уступки.
- Fix E: **Frame fight**
  Добавь борьбу за рамку: “кто задаёт вопросы”, “кто должен оправдываться”.

---

## 12) EXAMPLES (MANDATORY)
### 12.1 PASS EXAMPLE (access negotiation)
CONTEXT:
- Герою нужен пропуск; офицер не хочет рисковать.
A (герой):
- Goal: получить пропуск
- Fear: быть проверенным по базе
- Lever: информация о саботаже
- Subtext: bargain
B (офицер):
- Goal: не попасть под расследование
- Fear: потерять должность
- Lever: доступ к узлу + проверка
- Subtext: test
BEATS:
1) A просит “формально” → B тестирует вопросом “кто ты?”
   Shift: рамка у B.
2) A уходит в уклонение → B усиливает давление “проверю прямо сейчас”
   Shift: рост ставки.
3) A платит правдой (намёк на саботаж) → B меняет тон
   Shift: B заинтересован.
4) B требует цену “откуда инфо?” → A отдаёт часть источника
   Shift: price of truth.
OUTCOME:
- пропуск выдан, но с меткой наблюдения (цена).
WHY PASS:
- есть цель, рычаги, подтекст, цена и изменение состояния.

### 12.2 FAIL EXAMPLE (exposition dump)
Двое “объясняют план”, который оба знают, без сопротивления и цены.
WHY FAIL:
- нет конфликтной цели, нет рычагов, нет shift — это лекция.

---

## 13) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/01__NARRATIVE__SCENE_CRAFT.md
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/03__NARRATIVE__TENSION_STAKES.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/02__NARRATIVE__CAUSE_EFFECT_CHAIN.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/04__NARRATIVE__TURNING_POINTS.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/05__NARRATIVE__FORESHADOWING_PAYOFF.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 14) COMPLIANCE
- SOURCE_LOCK: required (module enforces dialogue-as-action; discourages decorative talk)
- MEMORY: allowed only if meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
