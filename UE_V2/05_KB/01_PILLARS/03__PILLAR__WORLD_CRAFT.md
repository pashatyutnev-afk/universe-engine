# PILLAR — WORLD CRAFT (FOUNDATION TOME)
FILE: 04_KNOWLEDGE_BASE/01_PILLARS/03__PILLAR__WORLD_CRAFT.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: PILLAR
INDEX_TYPE: FOUNDATION_TOME
LEVEL: L2
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.PILLAR.WORLD.001
OWNER: SYSTEM
ROLE: Foundational world craft knowledge: world laws, constraints, culture/economy/ecology frames, high-level design procedures, quality frame, and failure modes; atomic details live in TOPICS and quality instruments live in SHARED_LIBRARIES

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Initialized World Craft pillar as foundation tome skeleton compatible with KB source-lock and usage gate."
- REASON: "Provide stable worldbuilding framework without duplicating atomic topics; enables consistent lore and systemic plausibility."
- IMPACT: "Entities can reference world laws and constraints consistently; topics/libraries will carry actionable details and checks."
- CHANGE_ID: UE.CHG.2026-01-14.KB.PILLAR.WORLD.001

---

## 0) PURPOSE (WHAT THIS PILLAR GIVES)
Этот PILLAR задаёт фундамент “МАСТЕРСТВО МИРОСТРОЕНИЯ”:
- как задавать законы мира и ограничения,
- как проектировать цивилизации/культуру/экономику/экологию на системном уровне,
- как обеспечивать согласованность и “правдоподобие” мира внутри заданных правил,
- какие типовые провалы ломают мир.

Детали и конкретные техники/таблицы/чеклисты — в TOPICS/LIBRARIES.

---

## 1) SOURCE-LOCK / NO FANTASY (ABSOLUTE)
- Никаких домыслов и “добавим красивую деталь”.
- Любое правило/ограничение/определение должно иметь точку истины в KB модулях (PATH/RAW).
- Этот PILLAR — рамка: принципы и high-level процедуры.

---

## 2) CORE PRINCIPLES (FOUNDATION)
### P1) World = rules + constraints
Мир читается через правила и ограничения. Без ограничений нет правды, есть “всё возможно”.

### P2) Consistency beats novelty
Согласованность важнее новизны. Новое допустимо только если не ломает закон мира.

### P3) Cause-effect at scale
История мира должна иметь причинность: география → ресурсы → экономика → политика → культура.

### P4) Institutions shape behavior
Институты (семья, власть, религия, право, армия, экономика) формируют поведение людей.

### P5) Scarcity creates tension
Дефицит ресурсов/рисков создаёт реальное напряжение и движение систем.

### P6) Technology changes everything
Технологический уровень определяет скорость, власть, связи и форму конфликтов.

### P7) Ecology is not decoration
Экология задаёт ограничения выживания, миграции, питания и инфраструктуры.

### P8) Mythology encodes values
Мифы/вера — не “сказки”, а код ценностей и социального порядка.

---

## 3) HIGH-LEVEL PROCEDURES (HOW TO BUILD)
### Proc A) Define world laws (core)
1) Определи “что возможно” (законы мира).
2) Определи “что невозможно” (запреты).
3) Определи источники исключений (если они есть) и цену исключений.
4) Зафиксируй правила в виде проверяемых утверждений (для будущих TOPICS/CTL/VAL).

### Proc B) Build systemic layers (macro causality)
1) География/климат → ресурсы/опасности.
2) Ресурсы → экономика/логистика.
3) Экономика → власть/институты.
4) Институты → культура/нормы/конфликты.
5) Конфликты → история/травмы/мифология.

### Proc C) Civilization design (repeatable)
1) Среда обитания (где живут и почему там).
2) Ресурсная база (что добывают/производят).
3) Институты (как управляют и решают споры).
4) Технологический профиль (что умеют).
5) Ценности/табу (что “свято/запрещено”).
6) Конфликтная ось (что их ломает/движет).

### Proc D) Lore consistency loop (control)
1) Каждое новое утверждение проверяется на конфликт с законами мира.
2) Если конфликт — либо запрет, либо исправление, либо формальное исключение с ценой.
3) Любые исключения фиксируются как отдельные модули (policy/constraint/topic) и проверяются.

---

## 4) QUALITY FRAME (WHAT “GOOD” LOOKS LIKE)
Мир считается качественным, если:
- законы мира ясны и ограничивают решения,
- причинность “работает” на уровне систем,
- культура и институты объясняют поведение,
- экономика/ресурсы поддерживают логистику и власть,
- экология влияет на жизнь, а не “фон”,
- новые элементы не ломают старые правила.

Проверки качества должны делаться через:
- RUBRIC modules (world/lore consistency)
- CTL policies (если используются)
- VAL/QA проверки согласованности

---

## 5) COMMON FAILURE MODES (ANTI-PATTERNS, HIGH LEVEL)
### F1) “Rule-less magic”
Есть “магия/сила”, но нет ограничений → всё решается чем угодно.

### F2) “Cosmetic world”
Мир — декорация: география/экономика/экология не влияет ни на что.

### F3) “Institution vacuum”
Нет институтов, но есть большие общества → поведение не объяснимо.

### F4) “Tech mismatch”
Технологии/логистика не соответствуют заявленной картине (и это ломает причинность).

### F5) “Lore drift”
Правила меняются от сцены к сцене без фиксации и цены.

---

## 6) REQUIRED CONNECTIONS (WHERE DETAILS LIVE)
Эта секция — список целевых ссылок (PATH) для будущих TOPICS/LIBRARIES.
Пока они могут быть пустыми (будут добавлены при наполнении).

### TOPICS (to create in 10_TOPICS/30_WORLD/)
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/TOPIC__WORLD_LAWS_CONSTRAINTS.md
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/TOPIC__GEOGRAPHY_RESOURCE_CAUSALITY.md
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/TOPIC__INSTITUTIONS_POWER_SYSTEMS.md
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/TOPIC__ECONOMY_LOGISTICS.md
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/TOPIC__ECOLOGY_SURVIVAL.md
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/TOPIC__MYTHOLOGY_VALUE_ENCODING.md
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/TOPIC__TECH_LEVEL_IMPACT.md
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/30_WORLD/TOPIC__LORE_CONSISTENCY_RULES.md

### SHARED LIBRARIES (to create)
#### Rubrics
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/20_RUBRICS/RUBRIC__WORLD_CONSISTENCY.md
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/20_RUBRICS/RUBRIC__CIVILIZATION_PLAUSIBILITY.md

#### Checklists
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/10_CHECKLISTS/CL__WORLD_LAWS_CHECK.md
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/10_CHECKLISTS/CL__LORE_DRIFT_GUARD.md

#### Templates
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/30_TEMPLATES/TPL__WORLD_LAWS_SHEET.md
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/30_TEMPLATES/TPL__CIVILIZATION_PROFILE.md

#### Examples
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/50_EXAMPLES/EXAMPLE__WORLD_PASS_PACK.md
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/50_EXAMPLES/EXAMPLE__WORLD_FAIL_PACK.md

---

## 7) ENTITY USAGE (HOW ENTITIES SHOULD CONSUME THIS)
Сущности подключают этот PILLAR через KB_SOURCES:
- как фундамент для world/lore задач,
- детали и решения — через TOPICS,
- проверки согласованности — через RUBRICS/CL/VAL/QA,
- конфликт норм — через policy/решение (CTL) и фиксируется в XREF.

---

## 8) NEXT EXPANSION (CONTROLLED)
Расширение допускается только:
- добавлением принципов/процедур верхнего уровня,
- добавлением ссылок на новые TOPICS/LIBRARIES,
- без переноса атомарных таблиц/конкретики внутрь PILLAR.

Все изменения фиксируются в KB_CHANGELOG.

--- END.
