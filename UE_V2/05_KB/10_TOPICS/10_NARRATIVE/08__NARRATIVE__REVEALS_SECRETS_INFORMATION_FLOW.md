# TOPIC — REVEALS, SECRETS & INFORMATION FLOW (NARRATIVE / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/08__NARRATIVE__REVEALS_SECRETS_INFORMATION_FLOW.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.NARR.INFO_FLOW.001
OWNER: SYSTEM
ROLE: Atomic method to manage story information as a flow: who knows what, when, and at what price; includes an Info Ledger, reveal types, anti-cheat rules, pass/fail tests, and drift guards

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created atomic topic for information flow: Info Ledger + reveal taxonomy + price-of-truth rules + anti-cheat checks."
- REASON: "Stories break from exposition dumps and unfair twists; information must be controlled, paid for, and causally revealed."
- IMPACT: "Entities can design satisfying reveals, maintain mystery, and avoid contradictions by tracking knowledge states."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.NARR.008

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
Управлять историей через поток информации:
- кто что знает (knowledge state),
- кто что скрывает (secrets),
- когда и почему раскрывается (reveal),
- какая цена за правду (price of truth),
- как избежать “твиста из воздуха” и инфо-дампа.

---

## 2) WHEN TO USE
- В истории есть тайны, расследование, шпионаж, интрига.
- Нужны твисты/раскрытия, которые должны быть честными.
- Персонажи слишком много объясняют словами.
- Возникают логические дыры “почему они не знали/не сказали”.

## 3) WHEN NOT TO USE
- Ты проектируешь одну сцену без тайны (используй scene craft / dialogue).
- Ты формируешь мир-лоры (это world topics).
- Ты пишешь чисто линейный экшен без загадок (можно, но всё равно полезно для контроля экспозиции).

---

## 4) INPUTS (MINIMUM)
- Список ключевых тайн/фактов (3–10).
- Список персонажей/фракций (акторы знания).
- План сцен/эпизодов (хотя бы грубо).

## 5) OUTPUTS (MINIMUM)
- INFO LEDGER (таблица тайн, носителей знания, триггеров раскрытия).
- Reveal plan (где и как раскрывать).
- 2 PASS + 2 FAIL теста + drift guards.

---

## 6) DEFINITIONS (STRICT)
### Secret
Факт/информация, скрытая от части акторов и/или аудитории.

### Knowledge state
Кто знает что именно (в любой момент).

### Reveal
Событие, которое меняет knowledge state.

### Price of truth
Цена раскрытия: риск, уступка, потеря лица, ресурс, последствия.

### Fair reveal
Раскрытие честно, если:
- есть подготовка (setup) или причинная цепь,
- есть триггер/механизм получения,
- есть цена/последствия,
- не ломает правила мира.

---

## 7) REVEAL TYPES (TAXONOMY)
- R1: Discovery (найдено доказательство/улика)
- R2: Confession (признание под давлением/ценой)
- R3: Exposure (раскрытие третьей стороной/утечка)
- R4: Deduction (логический вывод из подсказок)
- R5: Betrayal reveal (предательство/двойная игра)
- R6: Recontextualization (старые факты получают новый смысл)
- R7: Forced reveal (ультиматум/допрос/компромат)

---

## 8) PROCEDURE (INFO LEDGER + REVEAL PLAN)
### Step 1 — List SECRETS (3–10)
Каждая тайна = одна строка.
Формат:
- S1: “факт ___”
- S2: …

### Step 2 — Assign HOLDERS (who knows)
Для каждой тайны:
- holders: кто знает (персонажи/фракции)
- stakeholders: кто пострадает/выиграет от раскрытия

### Step 3 — Define ACCESS PATH (how it can be learned)
Запрещено: “просто узнали”.
Нужно:
- evidence path (улики/архив/свидетель/наблюдение)
- leverage path (шантаж/торг/угроза)
- accident path (ошибка/утечка) — но с причинностью

### Step 4 — Define TRIGGER for reveal
Что запускает раскрытие:
- давление времени
- конфликт интересов
- ошибка
- победа/поражение
- необходимость для следующего шага

### Step 5 — Define PRICE OF TRUTH
Для каждой тайны укажи цену раскрытия:
- кто платит
- чем платит
- что ломается/меняется (state change)

### Step 6 — Place REVEALS (where in story)
Для каждой тайны выбери:
- Scene/Episode slot (примерно)
- Reveal type (R1..R7)
- Micro-turn effect (как меняется цель/власть/отношения)

### Step 7 — Anti-cheat checks
Проверь:
- reveal не появляется без access path
- цена реальна, не символическая
- reveal не отменяет stakes без последствий
- тайна не “заморожена” слишком долго без давления (иначе скука)

### Step 8 — Mismatch audit (knowledge logic)
Проверить логически:
- если актор мог знать (имел доступ) — почему не узнал?
- если узнал — почему не использовал?
Если нет ответа → REWORK.

---

## 9) INFO LEDGER FORMAT (COPY)
INFO LEDGER:
| SECRET_ID | SECRET (fact) | HOLDERS (who knows) | STAKES (who loses/wins) | ACCESS PATH (how learned) | TRIGGER | REVEAL TYPE (R1..R7) | PRICE OF TRUTH | PLACEMENT (scene/ep) | STATE CHANGE |
|---|---|---|---|---|---|---|---|---|---|

---

## 10) QUICK CHECKLIST (PASS/FAIL)
- [ ] Есть 3–10 тайн
- [ ] У каждой тайны есть holders + stakes
- [ ] У каждой тайны есть access path (не “просто”)
- [ ] У каждой тайны есть trigger раскрытия
- [ ] У каждой тайны есть price of truth
- [ ] У каждой тайны есть reveal type и placement
- [ ] Anti-cheat checks пройдены
- [ ] Knowledge mismatch audit пройден

PASS IF:
- все пункты true

REWORK IF:
- есть тайны, но нет цены/триггеров/механизма доступа

FAIL IF:
- твисты из воздуха или инфо-дампы без конфликта

---

## 11) EXAMPLES (MANDATORY)
### 11.1 PASS EXAMPLE (paid discovery)
SECRET:
- “офицер работает на другую фракцию”
ACCESS PATH:
- найден журнал доступа + несостыковка времени (R1 discovery)
TRIGGER:
- после провала операции нужно понять, кто слил маршрут
PRICE:
- герой раскрывает свой источник и теряет прикрытие
STATE CHANGE:
- доверие рушится, начинается охота
WHY PASS:
- есть механизм получения, триггер, цена и последствия.

### 11.2 FAIL EXAMPLE (unfair twist)
SECRET:
- “оказывается, всё было подстроено самым умным злодеем”
ACCESS PATH:
- отсутствует
PRICE:
- нет
WHY FAIL:
- нет механизма и цены → читерство.

---

## 12) COMMON FAILURE MODES
- Failure: тайна раскрыта “разговором” без цены
  Fix: сделать “price of truth” (торг/риск/компромат) и сопротивление.
- Failure: слишком много тайн без движения
  Fix: добавить triggers и промежуточные “partial reveals”.
- Failure: knowledge mismatch (“почему не спросили раньше?”)
  Fix: добавить constraint/страх/ложную информацию/контроль доступа.

---

## 13) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/05__NARRATIVE__FORESHADOWING_PAYOFF.md
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/02__NARRATIVE__CAUSE_EFFECT_CHAIN.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/07__NARRATIVE__DIALOGUE_SUBTEXT.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/04__NARRATIVE__TURNING_POINTS.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/03__NARRATIVE__TENSION_STAKES.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 14) COMPLIANCE
- SOURCE_LOCK: required (module enforces causal access paths and paid reveals)
- MEMORY: allowed only if meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
