# TOPIC — PACING & RHYTHM (NARRATIVE / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/06__NARRATIVE__PACING_RHYTHM.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.NARR.PACING.001
OWNER: SYSTEM
ROLE: Provide an actionable method to control pacing and rhythm using tension curve, beat density, and scene purpose; includes pass/fail examples and a quick audit checklist

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created atomic topic for pacing/rhythm: tension curve mapping, beat density rules, and rewrite levers for tempo control."
- REASON: "Even with good scenes, stories fail if tempo is wrong; pacing must be auditable and adjustable."
- IMPACT: "Entities can diagnose slow/flat pacing and apply specific levers (compress/expand/alternate) without guesswork."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.NARR.006

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
Дать процедуру, как управлять темпом и ритмом истории:
- построить tension curve (кривая напряжения),
- проверить плотность событий/поворотов (beat density),
- определить, где нужно ускорить/замедлить,
- применить конкретные “рычаги” правки.

---

## 2) WHEN TO USE
- История “тянется” или “несётся” без смысла.
- Сцены хорошие по отдельности, но вместе — скука/усталость.
- В середине провал темпа (mid-sag), или финал “слишком быстро”.

## 3) WHEN NOT TO USE
- Сцены не меняют состояние (сначала исправь scene craft).
- Нет ставок/давления (сначала исправь stakes).
- Нет причинности (сначала исправь cause/effect).

---

## 4) INPUTS (MINIMUM)
- Список сцен/битов в порядке.
- Для каждой: цель, конфликт, исход (change of state), stakes.
- Важные turning points.

## 5) OUTPUTS (MINIMUM)
- Tension curve (низ/сред/выс по сценам).
- Beat density карта (где частота изменений слишком низкая/высокая).
- Plan: какие сцены сжать/расширить/переставить/удалить/разбить.

---

## 6) DEFINITIONS (STRICT)
### Beat
Минимальное изменение в сцене:
- новая информация
- смена тактики
- рост давления
- микро-поворот

### Beat density
Плотность битов: сколько “изменений” происходит на единицу сцены/страницы/минуты (в вашей системе — просто по счёту).

### Tension curve
Распределение напряжения по последовательности сцен:
- low / mid / high (достаточно трех уровней).

---

## 7) PROCEDURE (TENSION CURVE + BEAT DENSITY)
### Step 1 — Label each scene by PURPOSE (one)
Для каждой сцены выбери функцию:
- PUSH (толкает конфликт вперёд, рост риска)
- REVEAL (раскрытие информации)
- TURN (поворотная точка, state flip)
- BREATH (пауза/восстановление, но с изменением состояния)
- SETUP (посадка будущего payoff)

Правило:
- сцена без функции = кандидат на удаление/слияние.

### Step 2 — Assign TENSION LEVEL (low/mid/high)
Оцени по stakes/давлению:
- LOW: риск мал, но есть движение/изменение
- MID: риск ощутим, давление растёт
- HIGH: угроза/точка невозврата/жёсткий конфликт

### Step 3 — Count BEATS per scene (1..N)
Посчитай, сколько раз “что-то изменилось” внутри сцены:
- 1–2 beat = медленно
- 3–5 beat = нормально
- 6+ beat = быстро/плотно

(Это ориентир, не закон. Важно — контраст.)

### Step 4 — Detect pacing problems (patterns)
Ищи паттерны:
- FLATLINE: 3+ сцены подряд с одним уровнем tension (например MID/MID/MID)
- MID-SAG: длинный участок без TURN и без роста stakes
- HYPER-CLUSTER: много HIGH сцен подряд без дыхания
- EMPTY BREATH: “пауза” без изменения состояния (это не breath, это пустота)

### Step 5 — Apply pacing levers (fix tools)
Выбери рычаги:

**Accelerate (ускорить)**
- COMPRESSION: выкинуть повторяющиеся биты, оставить только разворот
- MERGE: объединить две сцены в одну с одним исходом
- ENTER LATE: начинать сцену ближе к конфликту
- EXIT EARLY: выходить сразу после исхода
- TURN SOONER: сдвинуть поворот ближе

**Decelerate (замедлить)**
- EXPAND CONSEQUENCE: показать цену и последствия
- ADD RESISTANCE: усилить сопротивление (но не болтовней)
- ADD DECISION: вставить выбор героя с ценой
- BREATH WITH CHANGE: пауза, но с изменением отношений/плана

**Rhythm control (ритм)**
- ALTERNATE: чередовать PUSH/REVEAL/BREATH/TURN
- CONTRAST: после HIGH дать LOW/MID с важной сменой
- SETUP→PAYOFF spacing: посадка раньше, сборка позже (без затяжки)

### Step 6 — Re-map tension curve
После правок ещё раз отметь:
- уровни tension
- где turning points
- beat density
и проверь, что кривая стала “живой” (есть волны и рост).

---

## 8) QUICK CHECKLIST (PASS/FAIL)
- [ ] У каждой сцены есть функция (PUSH/REVEAL/TURN/BREATH/SETUP)
- [ ] Tension curve не “плоская” (нет 3+ одинаковых подряд без причины)
- [ ] Есть turning points в ключевых местах (не только в конце)
- [ ] Beat density не проваливается на длинных участках
- [ ] Есть дыхание между high-кластерами, но breath меняет состояние
- [ ] Применены рычаги (compress/merge/enter late/exit early и т.д.)

PASS IF:
- все пункты true

REWORK IF:
- есть проблемы, но исправимы без переписывания основы

FAIL IF:
- mid-sag/flatline доминируют, а сцены не меняют состояние

---

## 9) EXAMPLES (MANDATORY)
### 9.1 PASS EXAMPLE (healthy rhythm)
SEQUENCE (purpose / tension / beats):
- S1: SETUP / LOW / 2
- S2: PUSH / MID / 4
- S3: REVEAL / MID / 3
- S4: TURN / HIGH / 3
- S5: BREATH (with change) / LOW / 2
- S6: PUSH / MID / 4
WHY PASS:
- есть волны tension, есть поворот, breath не пустой, плотность битов варьируется.

### 9.2 FAIL EXAMPLE (mid-sag)
SEQUENCE:
- S1: REVEAL / MID / 2
- S2: REVEAL / MID / 2
- S3: REVEAL / MID / 2
- S4: REVEAL / MID / 2
WHY FAIL:
- flatline + низкая плотность, нет TURN, нет роста stakes → провал середины.

### 9.3 EDGE EXAMPLE (high cluster)
SEQUENCE:
- S1: TURN / HIGH / 5
- S2: PUSH / HIGH / 6
- S3: PUSH / HIGH / 6
Fix:
- вставить BREATH with change (LOW) и/или снизить плотность, чтобы сохранить эффект HIGH.
WHY EDGE:
- без контраста аудитория “глохнет”.

---

## 10) COMMON FAILURE MODES
- Failure: “пауза без изменения”
  Fix: breath должен менять отношения/план/правду, иначе удалить/слить.
- Failure: “много объяснений”
  Fix: enter late + compress exposition в действия/выбор.
- Failure: “всё high”
  Fix: добавить контраст и последствия вместо постоянной эскалации.
- Failure: “всё mid”
  Fix: добавить turn и реальные ставки; пересобрать ladder.

---

## 11) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/01__NARRATIVE__SCENE_CRAFT.md
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/03__NARRATIVE__TENSION_STAKES.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/04__NARRATIVE__TURNING_POINTS.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/05__NARRATIVE__FORESHADOWING_PAYOFF.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/02__NARRATIVE__CAUSE_EFFECT_CHAIN.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 12) COMPLIANCE
- SOURCE_LOCK: required (no invention beyond KB; this module defines a checkable procedure)
- MEMORY: allowed only if STATE=VERIFIED and meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
