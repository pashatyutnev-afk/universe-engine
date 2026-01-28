# TOPIC — TECH LEVEL IMPACT (WORLD / ATOMIC MODULE)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/03__WORLD__TECH_LEVEL_IMPACT.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: ATOMIC_KB_MODULE
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.WORLD.TECH_LEVEL.001
OWNER: SYSTEM
ROLE: Provide an atomic method to define a tech level as a capability/constraint matrix and derive second-order impacts on logistics, power, conflict, and daily life; includes pass/fail examples and an audit checklist

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created atomic topic for tech level: capability matrix + constraints + second-order effects to prevent tech mismatch and lore drift."
- REASON: "Tech level must reshape society; vague tech labels cause contradictions in logistics, warfare, economy, and institutions."
- IMPACT: "Entities can derive consistent world implications from tech assumptions and audit scenes for mismatch."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.WORLD.003

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
Техуровень — это не “высокий/низкий”, а матрица возможностей и ограничений.
Модуль даёт процедуру, как:
- зафиксировать tech capability matrix,
- прописать ограничения (ресурс/доступ/стоимость/риски),
- вывести вторичные эффекты (second-order impacts) на логистику, власть, войну, быт,
- проверить сцены на “tech mismatch”.

---

## 2) WHEN TO USE
- Ты вводишь технологии (связь, транспорт, оружие, медицина, производство, вычисления).
- Мир начинает противоречить сам себе (“есть суперсвязь, но курьеры на лошадях без причины”).
- Нужна согласованность конфликтов и экономики с возможностями.

## 3) WHEN NOT TO USE
- Ты формулируешь конкретный закон мира (это другой topic).
- Ты проектируешь экономику/ресурсы детально (другой topic).
- Ты делаешь терминологию/глоссарий.

---

## 4) INPUTS (MINIMUM)
- Название техпрофиля/эпохи/набора технологий.
- Что должно быть возможно (capabilities).
- Что должно быть ограничено (constraints).

## 5) OUTPUTS (MINIMUM)
- Tech Capability Matrix (таблица доменов).
- Second-order impacts (список последствий).
- Tech mismatch audit (чеклист для сцен/лора).

---

## 6) DEFINITIONS (STRICT)
### Capability
Что технология позволяет делать (скорость/точность/масштаб/контроль/наблюдение).

### Constraint
Что мешает бесконечному применению (ресурс, редкость, доступ, риск, стоимость, инфраструктура).

### Second-order impact
Не прямой эффект, а следствие:
- “если есть X, то меняется Y” (логистика, власть, институты, преступность, война).

---

## 7) PROCEDURE (TECH CAPABILITY MATRIX)
### Step 1 — Fill TECH CAPABILITY MATRIX (8 domains)
Заполни по шкале (описательно): LOW / MID / HIGH / EXTREME.

Домены:
1) COMMUNICATION (связь)
2) TRANSPORT (перемещение)
3) ENERGY (энергия/топливо)
4) PRODUCTION (производство/ремонт)
5) COMPUTATION (вычисления/ИИ/аналитика)
6) MEDICINE (восстановление/лечения)
7) WEAPONS/SECURITY (оружие/контроль)
8) SENSORS/SURVEILLANCE (наблюдение)

Для каждого домена укажи:
- capability (что умеют)
- constraint (что ограничивает)

### Step 2 — Add 3 GLOBAL CONSTRAINTS (system-wide)
Минимум 3:
- инфраструктура (где работает)
- доступ (кто имеет)
- стоимость/редкость (что ограничивает масштаб)

### Step 3 — Derive SECOND-ORDER IMPACTS (minimum 10)
Выведи последствия в категориях:
- logistics (как движутся люди/товары)
- power/institutions (кто контролирует)
- conflict (как воюют/давят)
- economy (что становится ценным/дешёвым)
- daily life (как живут обычные)
- crime/countermeasures (как нарушают и защищаются)

Формат:
- “Если COMMUNICATION=HIGH, то … (следствие)”

### Step 4 — Identify “IMPOSSIBLE WITHOUT EXPLANATION”
Выпиши 3–5 вещей, которые НЕ должны происходить при этом техуровне:
- “при HIGH surveillance невозможно ‘просто исчезнуть’ без контрмер”
- “при LOW transport невозможно быстро перекидывать армии без логистики”

### Step 5 — Tech mismatch audit (scene check)
Для любой сцены проверяй:
- соответствует ли действие capability?
- учтены ли constraints?
- есть ли контрмеры там, где должны быть?

---

## 8) MATRIX FORMAT (COPY)
TECH CAPABILITY MATRIX:
- COMMUNICATION: <LOW|MID|HIGH|EXTREME>
  - CAPABILITY:
  - CONSTRAINT:
- TRANSPORT: ...
- ENERGY: ...
- PRODUCTION: ...
- COMPUTATION: ...
- MEDICINE: ...
- WEAPONS/SECURITY: ...
- SENSORS/SURVEILLANCE: ...

GLOBAL CONSTRAINTS:
- G1:
- G2:
- G3:

SECOND-ORDER IMPACTS (10+):
1)
2)
...

IMPOSSIBLE WITHOUT EXPLANATION (3–5):
- ...
- ...

---

## 9) QUICK CHECKLIST (PASS/FAIL)
- [ ] Заполнены 8 доменов матрицы (capability + constraint)
- [ ] Есть 3 global constraints
- [ ] Есть 10+ second-order impacts
- [ ] Есть 3–5 “impossible without explanation”
- [ ] Проведён mismatch audit для ключевых сцен/лора

PASS IF:
- все пункты true

REWORK IF:
- матрица есть, но нет последствий или ограничений

FAIL IF:
- техуровень описан словами без проверяемых следствий

---

## 10) EXAMPLES (MANDATORY)
### 10.1 PASS EXAMPLE (high comms + high surveillance)
MATRIX (fragment):
- COMMUNICATION: HIGH
  - CAPABILITY: мгновенная связь в пределах сети
  - CONSTRAINT: сеть работает только в инфраструктурных узлах
- SENSORS/SURVEILLANCE: HIGH
  - CAPABILITY: распознавание лиц и трекинг в публичных зонах
  - CONSTRAINT: слепые зоны вне узлов, контрмеры возможны
SECOND-ORDER IMPACTS:
- логистика становится быстрее, но контролируемой
- преступность смещается в “слепые зоны” и к подделке идентичности
- власть держится на контроле узлов сети
IMPOSSIBLE WITHOUT EXPLANATION:
- “герой просто исчез в центре города” (нужно объяснение: контрмеры/слепая зона)
WHY PASS:
- есть ограничения и выводы, сцены можно проверять.

### 10.2 FAIL EXAMPLE (tech mismatch)
Заявлено:
- COMMUNICATION=HIGH (везде связь)
В сцене:
- “нужно отправить курьера 3 дня, чтобы передать сообщение”
Почему FAIL:
- mismatch: либо связь не везде (constraint), либо сцена должна объяснить отсутствие связи.

---

## 11) COMMON FAILURE MODES
- Failure: “tech level без ограничений”
  Fix: добавить constraints (доступ/инфраструктура/стоимость).
- Failure: “нет вторичных эффектов”
  Fix: выписать 10+ impacts по категориям.
- Failure: “сцены игнорируют наблюдение/логистику”
  Fix: провести mismatch audit и добавить контрмеры/объяснения.

---

## 12) RELATED (PATH ONLY)
REL:
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/01__WORLD__WORLD_LAWS_CONSTRAINTS.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/02__WORLD__LORE_CONSISTENCY_RULES.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/04__WORLD__GEOGRAPHY_RESOURCE_CAUSALITY.md
- REL: complements -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/05__WORLD__INSTITUTIONS_POWER_SYSTEMS.md

XREF:
- XREF: task_to_scope -> PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/01__TASK_TO_KB_SCOPE_MAP.md

---

## 13) COMPLIANCE
- SOURCE_LOCK: required (no invention beyond KB; this module defines a checkable matrix procedure)
- MEMORY: allowed only if STATE=VERIFIED and meaning unchanged
- KB_USAGE_GATE: reference this topic via PATH in KB_SOURCES when used

--- END.
