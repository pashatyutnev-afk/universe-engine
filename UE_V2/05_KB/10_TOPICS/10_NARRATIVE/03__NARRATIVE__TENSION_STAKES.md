# TOPIC — TENSION & STAKES (NARRATIVE / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/03__NARRATIVE__TENSION_STAKES.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.NARR.TENSION_STAKES.001
OWNER: SYSTEM
ROLE: Provide an actionable procedure to define and escalate stakes and maintain scene-to-scene tension; includes pass/fail examples and a quick audit checklist

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created atomic topic for tension/stakes: stake statement, escalation ladder, and tension check for scenes/outlines."
- REASON: "Without stakes, scenes become inert; tension is the engine that forces decisions and creates momentum."
- IMPACT: "Entities can build measurable tension and avoid flat sequences using a deterministic escalation procedure."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.NARR.003

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
Дать процедуру, как:
- сформулировать ставки (что можно потерять/получить),
- сделать ставки **конкретными и проверяемыми**,
- эскалировать напряжение по сценам,
- проверить, что сцена “держит давление”.

---

## 2) WHEN TO USE
- Сцены ощущаются “ровными” и скучными.
- Герой действует без цены и угрозы.
- Можно остановить историю в любой момент без последствий.

## 3) WHEN NOT TO USE
- Ты проверяешь причинность между сценами (это другой topic).
- Ты делаешь структуру поворотных точек (это другой topic).
- Ты пишешь чисто атмосферную вставку без изменения состояния (обычно всё равно ошибка — см. EDGE в примерах).

---

## 4) INPUTS (MINIMUM)
- Текущая сцена (goal/obstacle/outcome).
- Контекст истории: что герою важно, что он боится потерять.
- Оппозиция/угроза (кто/что давит).

## 5) OUTPUTS (MINIMUM)
- “Stake statement” (1–2 строки).
- Эскалационная лестница (escalation ladder) для ближайших сцен.
- Решение: PASS/REWORK/FAIL по напряжению.

---

## 6) PROCEDURE (STAKE STATEMENT + ESCALATION LADDER)
### Step 1 — Write the STAKE STATEMENT (one sentence)
Формат:
- “Если герой **не добьётся X**, он потеряет **Y** (конкретно), и это приведёт к **Z** (последствие).”

Правила:
- Y должно быть конкретным (жизнь/свобода/доступ/отношение/ресурс/репутация/секрет).
- Z должно быть причинным следствием (а не “будет плохо”).

### Step 2 — Classify stake type (choose 1–2)
- physical (жизнь/тело/безопасность)
- social (статус/отношения/репутация)
- material (деньги/ресурс/доступ/инструмент)
- moral (ценность/обещание/вина/табу)
- identity (кто он “на самом деле”, раскрытие/самоуважение)

### Step 3 — Add TIME PRESSURE (urgency)
Добавь одно:
- deadline (время кончается)
- window (шанс бывает один раз)
- decay (состояние ухудшается)
- pursuit (за героем охота)

Без давления ставки часто “не включаются”.

### Step 4 — Build ESCALATION LADDER (3 rungs)
Сделай 3 ступени эскалации на ближайший кусок:
- R1: базовый риск (что потеряешь сейчас)
- R2: усиление (потеря больше / шанс меньше)
- R3: необратимость (точка, после которой назад нельзя)

Правило:
- каждая следующая ступень должна быть **хуже** или **дороже**.

### Step 5 — Put stakes into the scene mechanics
Проверь, что stakes видны через:
- выбор героя (risk choice),
- сопротивление оппозиции,
- цену (price) или последствия (consequence).

Если stakes “на бумаге”, но не влияют на действия — это FAIL.

### Step 6 — Tension check: “Can we pause?”
Задай вопрос:
- “Можно ли поставить паузу и ничего не изменится?”
Если “да” — напряжения нет (REWORK/FAIL).

---

## 7) QUICK CHECKLIST (PASS/FAIL)
- [ ] Stake statement конкретен (X/Y/Z)
- [ ] Тип ставок определён (physical/social/material/moral/identity)
- [ ] Есть давление времени (deadline/window/decay/pursuit)
- [ ] Есть лестница эскалации (R1/R2/R3)
- [ ] Ставки влияют на выбор/тактику/цену в сцене
- [ ] Пауза невозможна без потерь (tension is active)

PASS IF:
- все пункты true

REWORK IF:
- stakes есть, но не влияют на механику сцены

FAIL IF:
- stakes размыты (“будет плохо”) или отсутствуют

---

## 8) EXAMPLES (MANDATORY)
### 8.1 PASS EXAMPLE
CONTEXT:
- Герой пытается добыть доступ к серверной, чтобы скачать доказательства.
STAKE STATEMENT:
- “Если герой не получит доступ, он потеряет шанс доказать правду, и его обвинят, что приведёт к аресту.”
TYPE:
- social + physical (репутация → арест)
TIME PRESSURE:
- window: сервер отключат через 20 минут
ESCALATION LADDER:
- R1: охрана усиливает проверку
- R2: герой теряет фальшивый пропуск и становится подозреваемым
- R3: тревога блокирует сектор (необратимость) + начинается погоня
WHY PASS:
- stakes конкретны, давят на выбор, эскалация ухудшает положение.

### 8.2 FAIL EXAMPLE
CONTEXT:
- Герой “хочет поговорить с другом”.
STAKE STATEMENT:
- “Если не поговорит, будет грустно.”
WHY FAIL:
- Y размыто, Z не определено, нет давления времени, нет цены.

### 8.3 EDGE EXAMPLE (quiet scene)
CONTEXT:
- После провала герой молчит, друг ждёт признания.
STAKE STATEMENT:
- “Если герой не признается сейчас, он потеряет доверие друга, и команда распадётся.”
TYPE:
- social
TIME PRESSURE:
- decay: доверие падает с каждой ложью
WHY EDGE:
- сцена тихая, но stakes активны (отношения и распад команды — реальное изменение).

---

## 9) COMMON FAILURE MODES
- Failure: “ставки только в голове автора”
  Fix: встроить stakes в выбор героя и сопротивление оппозиции.
- Failure: “нет времени”
  Fix: добавить deadline/window/decay/pursuit.
- Failure: “эскалации нет”
  Fix: прописать 3 ступени, где каждая хуже.
- Failure: “цена отсутствует”
  Fix: добавить price (что герой отдаёт) или consequence (что теряет).

---

## 10) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/01__NARRATIVE__SCENE_CRAFT.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/02__NARRATIVE__CAUSE_EFFECT_CHAIN.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/04__NARRATIVE__TURNING_POINTS.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/06__NARRATIVE__PACING_RHYTHM.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 11) COMPLIANCE
- SOURCE_LOCK: required (no invention beyond KB; this module defines a checkable procedure)
- MEMORY: allowed only if STATE=VERIFIED and meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
