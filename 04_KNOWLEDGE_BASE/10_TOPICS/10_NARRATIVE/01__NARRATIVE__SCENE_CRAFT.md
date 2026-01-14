# TOPIC — SCENE CRAFT (NARRATIVE / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/01__NARRATIVE__SCENE_CRAFT.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.NARR.SCENE_CRAFT.001
OWNER: SYSTEM
ROLE: Provide an atomic, actionable procedure for designing a scene as a unit of goal + conflict + outcome; includes pass/fail examples and check criteria

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created atomic topic for scene craft: goal/obstacle/tactics/outcome and a quick quality checklist with PASS/FAIL examples."
- REASON: "Scenes are the smallest unit that must create change; without a stable procedure, narrative quality collapses."
- IMPACT: "Entities can design scenes deterministically; rubrics/checklists can validate scene quality."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.NARR.001

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
Сцена — минимальная единица истории, которая обязана **изменить состояние** (информацию, отношения, позицию, угрозу или план).  
Этот модуль даёт процедуру, как проектировать сцену так, чтобы она не была “пустой”.

---

## 2) WHEN TO USE
- Нужно придумать/переписать сцену так, чтобы она работала как “единица действия”.
- Сцена ощущается скучной, статичной, “проходной”.
- Нужно повысить напряжение и причинность между сценами.

## 3) WHEN NOT TO USE
- Ты пишешь логлайн/синопсис на уровне истории (это не scene-level).
- Ты делаешь раскадровку/визуализацию кадрами (это другой модуль).
- Ты решаешь монтаж/постановку — здесь только структура сцены, не режиссёрские решения.

---

## 4) INPUTS (MINIMUM)
- Кто в сцене главный действующий (actor).
- Чего он хочет в этой сцене (goal).
- Почему сейчас (pressure / urgency).
- Кто/что мешает (opposition).

## 5) OUTPUTS (MINIMUM)
- Scene unit: цель → конфликт → исход (изменение состояния)
- “Next-state hook”: что стало иначе к концу сцены

---

## 6) PROCEDURE (SCENE UNIT DESIGN)
### Step 1 — Define GOAL (one sentence)
Сформулируй цель сцены как действие:
- “получить/убедить/спасти/выкрасть/скрыть/разоблачить…”
Запрещено: “поговорить”, “побыть”, “посидеть” без результата.

### Step 2 — Define STAKES (what changes if fail)
- Что герой теряет/получает прямо сейчас.
- Что ухудшится, если он не добьётся цели.

### Step 3 — Define OPPOSITION (active resistance)
Оппозиция должна сопротивляться:
- персонаж/система/среда/внутренний страх
Минимум: одна причина, почему “не получится легко”.

### Step 4 — Define TACTICS (attempts)
Герой пробует 1–3 тактики:
- давление / просьба / обман / угроза / обмен / хитрость / риск
Правило: тактика должна быть видна как действие, а не объяснение.

### Step 5 — Define OUTCOME (change of state)
К концу сцены обязательно:
- успех (но с ценой), или
- частичный успех, или
- провал (но с новым знанием/угрозой/поворотом)

Запрещено: “ничего не изменилось”.

### Step 6 — Define TURN (micro-turn)
Укажи момент, где сцена поворачивает:
- новая информация
- смена власти/позиции
- обнажение ценности/ложи
- появление новой угрозы

### Step 7 — Define NEXT HOOK
Что сцена запускает дальше:
- новая цель
- новый риск
- новый конфликт
- новая обязанность/долг

---

## 7) QUICK CHECKLIST (PASS/FAIL)
- [ ] GOAL выражен действием (1 строка)
- [ ] STAKES ясны (что на кону)
- [ ] OPPOSITION активна (почему трудно)
- [ ] Есть минимум 1 попытка (TACTICS)
- [ ] OUTCOME меняет состояние
- [ ] Есть TURN (микро-поворот)
- [ ] Есть NEXT HOOK (сцепка со следующей сценой)

PASS IF:
- все пункты true

FAIL IF:
- цель размыта, или нет сопротивления, или исход не меняет состояние

---

## 8) EXAMPLES (MANDATORY)
### 8.1 PASS EXAMPLE
INPUT:
- Actor: героиня хочет получить пропуск в закрытый сектор.
- Opposition: офицер подозрителен; пропуск выдаётся только по распоряжению.
OUTPUT (scene unit):
- GOAL: получить пропуск сегодня.
- STAKES: без пропуска команда не успеет; риск разоблачения растёт.
- OPPOSITION: офицер требует подтверждение и проверяет базу.
- TACTICS: героиня сначала давит авторитетом, затем предлагает обмен информацией.
- TURN: офицер узнаёт имя героини и меняет тон — он связан с её прошлым.
- OUTCOME: пропуск выдан, но офицер ставит отметку “наблюдение”.
- NEXT HOOK: команда получает доступ, но становится объектом слежки.
WHY PASS:
- есть цель, сопротивление, действия, изменение состояния и сцепка.

### 8.2 FAIL EXAMPLE
INPUT:
- “двое сидят и обсуждают план, пока ничего не происходит”
OUTPUT:
- GOAL: “обсудить план”
- OPPOSITION: нет
- OUTCOME: “решили что-нибудь потом”
WHY FAIL:
- нет активной цели-действия, нет сопротивления, нет изменения состояния.

### 8.3 EDGE EXAMPLE (IF APPLICABLE)
INPUT:
- Сцена “атмосферы/паузы” после травмы героя.
OUTPUT:
- GOAL: герой пытается скрыть слабость и сохранить контроль.
- OPPOSITION: внутренняя боль + присутствие свидетеля (друг/враг).
- OUTCOME: герой срывается и выдаёт уязвимость → отношение меняется.
WHY EDGE:
- сцена внешне “тихая”, но всё равно обязана менять состояние (отношение/власть/правду).

---

## 9) COMMON FAILURE MODES
- Failure: “цель = поговорить”
  Fix: сформулировать цель как действие с результатом.
- Failure: “нет сопротивления”
  Fix: добавить активного оппонента или системное ограничение.
- Failure: “исход без изменения”
  Fix: обязать сцену завершиться новым состоянием (инфо/угроза/отношение/план).

---

## 10) RELATED (PATH ONLY)
REL:
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/02__NARRATIVE__CAUSE_EFFECT_CHAIN.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/03__NARRATIVE__TENSION_STAKES.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/04__NARRATIVE__TURNING_POINTS.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 11) COMPLIANCE
- SOURCE_LOCK: required (no invention beyond KB; this module is a procedure template)
- MEMORY: allowed only if STATE=VERIFIED and meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
