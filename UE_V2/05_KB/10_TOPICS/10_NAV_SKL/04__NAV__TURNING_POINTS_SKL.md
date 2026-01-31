# TOPIC — TURNING POINTS (NARRATIVE / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/04__NARRATIVE__TURNING_POINTS.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.NARR.TURNING_POINTS.001
OWNER: SYSTEM
ROLE: Provide an actionable method to design and audit turning points as irreversible state changes; includes pass/fail examples and a checklist to distinguish real turns from fake beats

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created atomic topic for turning points: definition as state flip, turn types, and an audit/repair procedure."
- REASON: "Stories stagnate without real turns; turning points create inevitability, escalation, and momentum."
- IMPACT: "Entities can insert and verify true turning points that change goals, stakes, or power balance."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.NARR.004

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
Поворотная точка (turning point) — это **не событие**, а **переворот состояния**, после которого история не может продолжаться как раньше.

Модуль даёт:
- определение “настоящего поворота”,
- типы поворотов,
- процедуру проектирования,
- аудит “фейковых поворотов” и их ремонт.

---

## 2) WHEN TO USE
- История “ровная”: много событий, но мало изменений.
- Кульминации/пики не ощущаются.
- Сцены можно переставлять или выкидывать без потери.

## 3) WHEN NOT TO USE
- Ты проектируешь общий актовый план (это отдельный модуль/шаблон).
- Ты проектируешь одну сцену (turn может быть внутри сцены, но сцена — отдельный topic).
- Ты пишешь чисто атмосферный эпизод без давления (обычно ошибка — см. related topics про stakes).

---

## 4) INPUTS (MINIMUM)
- Текущее состояние: цель героя, ставки, баланс сил, доступные ресурсы.
- Список ближайших сцен/событий.
- Оппозиция и её давление.

## 5) OUTPUTS (MINIMUM)
- Turn definition (до/после) в 2–4 строках.
- Тип поворота.
- Цена (cost) и необратимость (irreversibility proof).
- Сцепка (what it forces next).

---

## 6) DEFINITIONS (STRICT)
### 6.1 State
STATE = набор условий, которые определяют “как сейчас живёт история”:
- GOAL (что герой пытается сделать)
- STAKES (что на кону)
- POWER BALANCE (кто контролирует ситуацию)
- ACCESS (что доступно/закрыто)
- INFORMATION (что известно/скрыто)

### 6.2 Turning Point
TURN = событие/решение/открытие, которое **переворачивает минимум 1 компонент STATE** так, что:
- старый план больше не работает,
- возникает новая цель/угроза/ограничение,
- требуется новый путь.

---

## 7) PROCEDURE (DESIGN A REAL TURN)
### Step 1 — Write BEFORE state (5 fields)
BEFORE:
- GOAL:
- STAKES:
- POWER:
- ACCESS:
- INFORMATION:

### Step 2 — Choose a TURN TYPE (one)
Выбери тип:
- REVELATION (новая правда меняет решения)
- BETRAYAL (союз ломается, доверие падает)
- LOCKDOWN (доступ закрыт, ресурсы пропали)
- COSTLY WIN (успех с ценой/ущербом)
- ESCALATION (угроза поднимается на уровень выше)
- ROLE FLIP (переворот власти/инициативы)
- POINT OF NO RETURN (невозвратность: нельзя откатить)

### Step 3 — Define the TURN EVENT (one sentence)
Коротко: что произошло или какое решение принято.

### Step 4 — Write AFTER state (same 5 fields)
AFTER:
- GOAL:
- STAKES:
- POWER:
- ACCESS:
- INFORMATION:

Правило:
- минимум 1 поле должно измениться существенно (лучше 2–3).

### Step 5 — Prove IRREVERSIBILITY
Ответь:
- “Почему нельзя вернуть как было?”
Один из доказательных якорей:
- ресурс потрачен/уничтожен
- доверие разрушено
- знание раскрыто (невозможно “разузнать обратно”)
- началась охота/тревога/внешняя реакция
- моральная граница пересечена
- время окно закрыто

### Step 6 — Define COST (price paid)
Укажи цену:
- потерян ресурс/союз/безопасность/репутация/невинность/время

### Step 7 — Define FORCED NEXT MOVE
Что turn заставляет сделать дальше:
- новая цель
- новая тактика
- новый риск
- новый оппонент

---

## 8) QUICK CHECKLIST (PASS/FAIL)
- [ ] Есть BEFORE state (5 полей)
- [ ] Есть AFTER state (5 полей)
- [ ] Изменилось минимум 1 поле существенно (лучше 2+)
- [ ] Есть доказательство необратимости (irreversibility proof)
- [ ] Есть цена (cost)
- [ ] Turn заставляет следующий шаг (forced next move)

PASS IF:
- все пункты true

FAIL IF:
- “поворот” ничего не меняет, или можно откатить, или нет цены

---

## 9) EXAMPLES (MANDATORY)
### 9.1 PASS EXAMPLE — Revelation + Lockdown
BEFORE:
- GOAL: украсть файл и уйти незаметно
- STAKES: разоблачение = арест
- POWER: охрана контролирует сектор
- ACCESS: есть фальшивый пропуск
- INFORMATION: герой думает, что камеры слепы
TURN EVENT:
- “герой видит: камеры записывают и его лицо уже распознано”
AFTER:
- GOAL: не украсть, а выжить и уйти
- STAKES: арест становится неминуемым при задержке
- POWER: охрана усиливает контроль
- ACCESS: пропуск больше не помогает
- INFORMATION: герой знает, что его уже идентифицировали
IRREVERSIBILITY:
- лицо распознано, тревога может подняться в любой момент
COST:
- потеря “тихого” пути; риск и время
FORCED NEXT MOVE:
- срочный побег через технический тоннель
WHY PASS:
- меняются цель, доступ и информация; есть необратимость и цена.

### 9.2 FAIL EXAMPLE — Fake beat
BEFORE:
- GOAL: договориться
TURN EVENT:
- “персонаж говорит ‘я подумаю’”
AFTER:
- GOAL: всё ещё договориться
WHY FAIL:
- состояние не изменилось, нет цены, нет необратимости.

### 9.3 EDGE EXAMPLE — Costly win
BEFORE:
- GOAL: спасти союзника
TURN EVENT:
- “союзник спасён, но герой раскрывает своё имя”
AFTER:
- GOAL: теперь скрываться бессмысленно; нужно ломать систему
IRREVERSIBILITY:
- имя раскрыто (знание уже у врага)
COST:
- потеря анонимности
WHY EDGE:
- внешне “победа”, но она меняет траекторию из-за цены.

---

## 10) COMMON FAILURE MODES
- Failure: “turn без after-state”
  Fix: выписать AFTER и доказать, что старый план не работает.
- Failure: “turn без цены”
  Fix: добавить cost или сделать turn неполным (rework).
- Failure: “turn можно откатить”
  Fix: добавить якорь необратимости (ресурс/знание/охота/окно времени).

---

## 11) RELATED (PATH ONLY)
REL:
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/01__NARRATIVE__SCENE_CRAFT.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/02__NARRATIVE__CAUSE_EFFECT_CHAIN.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/03__NARRATIVE__TENSION_STAKES.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/05__NARRATIVE__FORESHADOWING_PAYOFF.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/06__NARRATIVE__PACING_RHYTHM.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 12) COMPLIANCE
- SOURCE_LOCK: required (no invention beyond KB; this module defines a checkable procedure)
- MEMORY: allowed only if STATE=VERIFIED and meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
