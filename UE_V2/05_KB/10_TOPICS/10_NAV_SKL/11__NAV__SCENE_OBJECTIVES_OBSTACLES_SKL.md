# TOPIC — SCENE OBJECTIVES & OBSTACLES (NARRATIVE / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/11__NARRATIVE__SCENE_OBJECTIVES_OBSTACLES.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.NARR.OBJECTIVES_OBSTACLES.001
OWNER: SYSTEM
ROLE: Atomic method to define scene objectives as observable outcomes and obstacles as active resistance with constraints; includes Objective/Obstacle Card, pass/fail tests, and rewrite patterns

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created atomic topic for scene objectives/obstacles: objective clarity, obstacle taxonomy, constraints, and success/failure outcomes."
- REASON: "Scenes fail when objectives are vague and obstacles are passive; clarity drives conflict and pacing."
- IMPACT: "Entities can design scenes that are measurable, opposed, and consequence-driven."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.NARR.011

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_narrative
- type_topic
- scene_design
- gate_quality
- maturity_seed

---

## 1) PURPOSE
Сделать цели и препятствия сцены операциональными:
- цель = наблюдаемый результат,
- препятствие = активное сопротивление + ограничения,
- исход = успех/частичный успех/провал с последствиями.

---

## 2) WHEN TO USE
- Сцены “размытые”, непонятно, что герои пытаются сделать.
- Конфликт слабый: препятствие не сопротивляется.
- Сцена не имеет ясного исхода, можно выкинуть без потерь.

## 3) WHEN NOT TO USE
- Ты строишь общую причинность между сценами (cause/effect).
- Ты пишешь диалоговые биты (dialogue/subtext) — но цель/препятствие нужно иметь заранее.

---

## 4) INPUTS (MINIMUM)
- Кто главный действующий (actor).
- Контекст: ставки, давление времени, оппозиция.
- Что нужно получить/изменить в этой сцене.

## 5) OUTPUTS (MINIMUM)
- Objective/Obstacle Card.
- Список 2–3 возможных исходов (success/partial/fail) с последствиями.
- PASS/REWORK/FAIL по ясности сцены.

---

## 6) DEFINITIONS (STRICT)
### Objective
Наблюдаемый результат к концу сцены:
- “получить пропуск”, “убедить X согласиться”, “украсть ключ”, “скрыть факт”.

### Vague objective (forbidden)
- “поговорить”, “узнать”, “побыть”, “обсудить” без результата.

### Obstacle
Активное сопротивление:
- персонаж, система, среда, внутренний страх (но выраженный действием).

### Constraint
Ограничение, которое делает задачу трудной:
- дедлайн, наблюдение, дефицит, правило, пространство.

---

## 7) OBSTACLE TYPES (TAXONOMY)
- O1: Active opponent (персонаж сопротивляется)
- O2: System rule (доступ/пропуска/законы)
- O3: Resource limit (нет денег/времени/топлива)
- O4: Environment hazard (шторм, токс-туман, холод)
- O5: Information asymmetry (кто-то знает больше)
- O6: Internal block (страх/рана) — но должен проявляться как действие

---

## 8) PROCEDURE (OBJECTIVE/OBSTACLE CARD)
### Step 1 — Write OBJECTIVE as “get/change” (one sentence)
Формат:
- “Герой должен ___ (получить/изменить) ___ к концу сцены.”

Проверка:
- можно ли определить, получилось или нет? (YES/NO)

### Step 2 — Define STAKES (what it affects)
Одна строка:
- “Если не получится, будет ___ (конкретное последствие).”

### Step 3 — Add CONSTRAINT (why now)
Минимум одно:
- дедлайн / окно / погоня / ресурс на исходе / наблюдение

### Step 4 — Define OBSTACLE (choose 1–2 types)
Выбери типы O1..O6 и опиши конкретно:
- кто сопротивляется и как
- что система запрещает
- какой ресурс лимитирует

### Step 5 — Define OPPONENT GOAL (if obstacle is a character)
Если O1:
- “Оппонент хочет ___ (свой objective)”.
Без цели оппонент не сопротивляется.

### Step 6 — Define TACTICS (1–3)
Какие попытки будут:
- торг / обман / давление / риск / обход / компромисс

### Step 7 — Define OUTCOMES (3 вариантов)
- Success: что получено + какая цена (если есть)
- Partial: что получено частично + новый риск
- Fail: что сорвалось + новое давление/угроза (не “ничего”)

---

## 9) OBJECTIVE/OBSTACLE CARD FORMAT (COPY)
OBJECTIVE/OBSTACLE CARD:
- ACTOR:
- OBJECTIVE (observable):
- STAKES (if fail):
- CONSTRAINT (why now):
- OBSTACLE TYPE(S) (O1..O6):
- OBSTACLE (concrete resistance):
- OPPONENT GOAL (if O1):
- TACTICS (1–3):
- OUTCOMES:
  - Success:
  - Partial:
  - Fail:
- PASS/FAIL NOTES:

---

## 10) QUICK CHECKLIST (PASS/FAIL)
- [ ] Objective наблюдаем и проверяем (получилось/нет)
- [ ] Stakes конкретны
- [ ] Есть constraint (почему сейчас)
- [ ] Obstacle активен и конкретен
- [ ] Если есть оппонент — у него есть goal
- [ ] Есть 1–3 tactics
- [ ] Есть 3 outcomes (success/partial/fail) с последствиями

PASS IF:
- все пункты true

REWORK IF:
- objective есть, но obstacle пассивен или нет outcomes

FAIL IF:
- objective размытый или нет сопротивления/последствий

---

## 11) REWRITE TOOLKIT (FIX PATTERNS)
- Fix A: **Make objective measurable**
  “узнать” → “получить подтверждение/доказательство/пароль”.
- Fix B: **Add an active obstacle**
  Сделай сопротивление: оппонент с целью или системное правило.
- Fix C: **Add constraint**
  Дедлайн/окно/наблюдение.
- Fix D: **Add outcomes**
  Варианты успеха/частичного/провала с новым давлением.

---

## 12) EXAMPLES (MANDATORY)
### 12.1 PASS EXAMPLE
ACTOR:
- героиня
OBJECTIVE:
- “получить пропуск в закрытый сектор”
STAKES:
- без пропуска команда не успеет, риск разоблачения растёт
CONSTRAINT:
- окно 10 минут до смены охраны
OBSTACLE:
- O2 system rule + O1 офицер подозрителен
OPPONENT GOAL:
- офицер хочет не попасть под расследование
TACTICS:
- давление авторитетом, торг информацией
OUTCOMES:
- Success: пропуск выдан, но метка наблюдения
- Partial: пропуск временный на 5 минут
- Fail: тревога, имя героини внесено в список
WHY PASS:
- objective измерим, obstacle активен, есть последствия.

### 12.2 FAIL EXAMPLE
OBJECTIVE:
- “поговорить с офицером”
OBSTACLE:
- “он занят”
WHY FAIL:
- нет измеримого результата, obstacle пассивен, нет stakes.

---

## 13) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/01__NARRATIVE__SCENE_CRAFT.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/09__NARRATIVE__CONFLICT_SCENE_DYNAMICS.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/10__NARRATIVE__CHARACTER_AGENCY_DECISIONS.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/03__NARRATIVE__TENSION_STAKES.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 14) COMPLIANCE
- SOURCE_LOCK: required (objective must be measurable; obstacles must be active)
- MEMORY: allowed only if meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
