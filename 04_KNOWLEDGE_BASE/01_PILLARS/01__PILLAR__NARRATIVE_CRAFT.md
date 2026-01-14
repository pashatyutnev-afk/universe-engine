# PILLAR — NARRATIVE CRAFT (FOUNDATION TOME)
FILE: 04_KNOWLEDGE_BASE/01_PILLARS/01__PILLAR__NARRATIVE_CRAFT.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: PILLAR
INDEX_TYPE: FOUNDATION_TOME
LEVEL: L2
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.PILLAR.NARRATIVE.001
OWNER: SYSTEM
ROLE: Foundational narrative craft knowledge: principles, high-level procedures, quality frame, common failures; detailed techniques live in TOPICS and quality instruments live in SHARED_LIBRARIES

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Initialized Narrative Craft pillar as foundation tome skeleton compatible with KB source-lock and usage gate."
- REASON: "Provide stable high-level narrative framework for all entities without duplicating atomic topics."
- IMPACT: "Entities can reference narrative principles consistently; topics/libraries will carry actionable details and checks."
- CHANGE_ID: UE.CHG.2026-01-14.KB.PILLAR.NARR.001

---

## 0) PURPOSE (WHAT THIS PILLAR GIVES)
Этот PILLAR задаёт фундамент “НАРРАТИВНОЕ МАСТЕРСТВО”:
- принципы построения истории,
- высокоуровневые процедуры (как проектировать сюжет),
- рамку качества (что считается хорошо/плохо),
- типовые провалы и способы их предотвращения.

Детальные техники, чеклисты, рубрики и конкретные примеры должны жить в:
- TOPICS (атомарные модули)
- SHARED_LIBRARIES (checklists/rubrics/templates/patterns/examples)

---

## 1) SOURCE-LOCK / NO FANTASY (ABSOLUTE)
- Никакой фантазии и домыслов “как должно быть”.
- Этот документ — рамка. Конкретные нормы и проверки берутся из TOPICS/LIBRARIES по PATH/RAW.
- Если внутри PILLAR встречается правило, оно должно быть закреплено ссылками на модули (см. References).

---

## 2) CORE PRINCIPLES (FOUNDATION)
### P1) Story is change under pressure
История — это изменение (героя/системы) под давлением обстоятельств.

### P2) Causality beats sequence
События должны быть связаны причинно-следственно, а не просто “списком”.

### P3) Stakes are the engine
Без ставок нет напряжения: всегда ясно, что можно выиграть/потерять.

### P4) Character action reveals values
Герой раскрывается через выбор и действие, не через объяснения.

### P5) Scene is a unit of conflict + outcome
Сцена должна иметь цель, препятствие и результат (изменение состояния).

### P6) Payoff must justify setup
Любой “крючок” требует отдачи; любая отдача требует подготовки.

### P7) Clarity first
Понимание зрителя/читателя важнее сложности.

### P8) Consistency with controlled surprises
Не ломать логику ради твиста; неожиданное обязано быть объяснимым задним числом.

> Примечание: детальные определения, шкалы и техники закрепляются в TOPICS.

---

## 3) HIGH-LEVEL PROCEDURES (HOW TO BUILD)
### Proc A) Story design (top-down)
1) Определи “изменение” (что должно измениться к финалу).
2) Определи ставки и угрозу потерь.
3) Определи главный конфликт (кто/что против чего).
4) Спроектируй серию “поворотов” (turning points) с ростом давления.
5) Зафиксируй кульминацию (climax) как неизбежный выбор.
6) Проверь причинность между ключевыми событиями.

### Proc B) Scene design (unit-level)
1) Цель сцены.
2) Препятствие (конфликт).
3) Тактика героя (попытка).
4) Результат (изменение состояния).
5) Крючок для следующего шага (если нужно).

### Proc C) Rewrite loop (quality loop)
1) Проверь ясность (кто чего хочет и почему).
2) Проверь причинность (почему это произошло).
3) Проверь ставки (что на кону).
4) Проверь темп (не стоит ли сцена на месте).
5) Убери объяснения, усили действие/выбор.

---

## 4) QUALITY FRAME (WHAT “GOOD” LOOKS LIKE)
Нарратив считается качественным, если:
- у героя есть ясное желание/цель,
- препятствия реальны и нарастают,
- последствия действий ощутимы,
- сцены меняют состояние мира/героя,
- напряжение не падает без причины,
- развязка соответствует подготовке.

Проверки качества должны делаться через:
- RUBRIC modules (SHARED_LIBRARIES/20_RUBRICS)
- QA/VAL гейты (если применимо)

---

## 5) COMMON FAILURE MODES (ANTI-PATTERNS, HIGH LEVEL)
### F1) “Events without causality”
События происходят потому что “так надо”, без причинности.

### F2) “No stakes”
Нет ощутимых потерь/выигрыша → всё кажется пустым.

### F3) “Static scenes”
Сцены не меняют состояние → история стоит.

### F4) “Exposition dumping”
Объяснения вместо выбора/действий.

### F5) “Twist by cheat”
Твист ломает логику и правила мира.

> Детальные анти-паттерны и исправления — в PATTERN/ANTI модулях.

---

## 6) REQUIRED CONNECTIONS (WHERE DETAILS LIVE)
Эта секция — список целевых ссылок (PATH), которые должны быть созданы в TOPICS/LIBRARIES.
Пока они могут быть пустыми (будут добавлены при наполнении).

### TOPICS (to create in 10_TOPICS/10_NARRATIVE/)
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/TOPIC__SCENE_CONSTRUCTION.md
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/TOPIC__CAUSE_EFFECT_CHAIN.md
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/TOPIC__TENSION_STAKES.md
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/TOPIC__TURNING_POINTS.md
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/TOPIC__FORESHADOWING_PAYOFF.md
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/10_NARRATIVE/TOPIC__PACING_RHYTHM.md

### SHARED LIBRARIES (to create)
#### Rubrics
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/20_RUBRICS/RUBRIC__NARRATIVE_QUALITY.md
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/20_RUBRICS/RUBRIC__SCENE_QUALITY.md

#### Checklists
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/10_CHECKLISTS/CL__SCENE_REWRITE.md
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/10_CHECKLISTS/CL__STAKES_CLARITY.md

#### Templates
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/30_TEMPLATES/TPL__SCENE_PACK.md
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/30_TEMPLATES/TPL__STORY_OUTLINE.md

#### Examples
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/50_EXAMPLES/EXAMPLE__NARRATIVE_PASS_PACK.md
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/50_EXAMPLES/EXAMPLE__NARRATIVE_FAIL_PACK.md

---

## 7) ENTITY USAGE (HOW ENTITIES SHOULD CONSUME THIS)
Сущности подключают этот PILLAR через KB_SOURCES:
- как обязательный фундамент (REQUIRED) для narrative задач,
- а детальные решения — через TOPICS и проверки через RUBRICS/CHECKLISTS.

---

## 8) NEXT EXPANSION (CONTROLLED)
Расширять этот PILLAR можно только:
- добавляя принципы/процедуры верхнего уровня,
- добавляя ссылки на новые TOPICS/LIBRARIES,
- не перетаскивая атомарные техники внутрь PILLAR.

Все изменения фиксируются в KB_CHANGELOG.

--- END.
