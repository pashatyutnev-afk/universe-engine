# PILLAR — CHARACTER CRAFT (FOUNDATION TOME)
FILE: 04_KNOWLEDGE_BASE/01_PILLARS/02__PILLAR__CHARACTER_CRAFT.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: PILLAR
INDEX_TYPE: FOUNDATION_TOME
LEVEL: L2
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.PILLAR.CHARACTER.001
OWNER: SYSTEM
ROLE: Foundational character craft knowledge: principles, high-level procedures, quality frame, common failures; detailed methods live in TOPICS and quality instruments live in SHARED_LIBRARIES

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Initialized Character Craft pillar as foundation tome skeleton compatible with KB source-lock and usage gate."
- REASON: "Provide stable character-design framework for all entities without duplicating atomic topics."
- IMPACT: "Entities can reference character principles consistently; topics/libraries will carry actionable details and checks."
- CHANGE_ID: UE.CHG.2026-01-14.KB.PILLAR.CHAR.001

---

## 0) PURPOSE (WHAT THIS PILLAR GIVES)
Этот PILLAR задаёт фундамент “МАСТЕРСТВО ПЕРСОНАЖА”:
- принципы построения персонажа (ядро),
- высокоуровневые процедуры (как проектировать героя/антагониста/каст),
- рамку качества (что считается “живым” персонажем),
- типовые провалы и профилактику.

Детальные техники, чеклисты, рубрики и конкретные примеры должны жить в:
- TOPICS (атомарные модули)
- SHARED_LIBRARIES (checklists/rubrics/templates/patterns/examples)

---

## 1) SOURCE-LOCK / NO FANTASY (ABSOLUTE)
- Никакой фантазии и домыслов “как должно быть”.
- Конкретные нормы/пороги/форматы закрепляются в TOPICS/LIBRARIES по PATH/RAW.
- Этот PILLAR — рамка и фундаментальные принципы.

---

## 2) CORE PRINCIPLES (FOUNDATION)
### P1) Desire + obstacle = character engine
Герой проявляется через желание/цель и препятствие.

### P2) Choice reveals value
Ценности персонажа видны в выборе, особенно под давлением.

### P3) Contradictions make humans
Небольшие противоречия (сочетаемые) делают персонажа живым.

### P4) Wound drives behavior
Травма/незакрытая потребность часто объясняет реактивное поведение.

### P5) Competence has a price
Сильные стороны всегда имеют цену/ограничение.

### P6) Relationships are mirrors
Персонаж читается через отношения: кто его раскрывает, кто ломает, кто поддерживает.

### P7) Arc is earned through consequences
Рост происходит из последствий, а не из “решил измениться”.

### P8) Dialogue is behavior
Речь — это форма действия, не “информация”.

---

## 3) HIGH-LEVEL PROCEDURES (HOW TO BUILD)
### Proc A) Create a main character (hero)
1) Определи желание/цель (что хочет сейчас).
2) Определи страх/потерю (что боится потерять).
3) Определи внутреннюю рану (что болит).
4) Определи ограничение/дефект (что мешает).
5) Определи ценности (что “нельзя” нарушить).
6) Определи ключевой выбор в кульминации (что должен выбрать).
7) Определи последствия выбора (цена).

### Proc B) Create an antagonist (force of opposition)
1) Определи, чему он препятствует (какой цели героя).
2) Определи его “правоту” (в чём он считает себя правым).
3) Определи ресурс/власть (чем он давит).
4) Определи слабость/слепую зону.
5) Определи эскалацию давления по актам/эпизодам.

### Proc C) Build relationships (cast web)
1) Для каждого важного отношения: роль (mentor/rival/ally/love/foil).
2) Что это отношение вытаскивает наружу в герое.
3) Конфликт/напряжение в связи (что не совпадает).
4) Момент проверки (когда отношения ломаются/укрепляются).

### Proc D) Character arc (earned change)
1) Стартовая стратегия героя (как он выживает сейчас).
2) Давление ломает стратегию (провалы).
3) Новый выбор → новая цена.
4) Финальная версия героя — как следствие опыта.

---

## 4) QUALITY FRAME (WHAT “GOOD” LOOKS LIKE)
Персонаж считается качественным, если:
- желания и ставки ясны,
- поведение объяснимо (даже если неожиданно),
- выборы имеют цену и последствия,
- есть внутреннее противоречие/напряжение,
- отношения раскрывают разные грани,
- речь и действия согласованы с ценностями (или осознанно нарушают их),
- арка строится на опыте и последствиях.

Проверки качества должны делаться через:
- RUBRIC modules (SHARED_LIBRARIES/20_RUBRICS)
- QA/VAL гейты (если применимо)

---

## 5) COMMON FAILURE MODES (ANTI-PATTERNS, HIGH LEVEL)
### F1) “Cardboard character”
Персонаж = набор клише без желания, раны и цены.

### F2) “No consequences”
Действия не имеют последствий → герой не меняется.

### F3) “Info-dump dialogue”
Речь объясняет сюжет вместо поведения/намерения.

### F4) “Unmotivated shifts”
Персонаж резко меняет позицию без давления и цены.

### F5) “Everyone sounds the same”
У персонажей нет различимого речевого/поведенческого профиля.

> Детальные анти-паттерны и фиксы — в PATTERN/ANTI модулях.

---

## 6) REQUIRED CONNECTIONS (WHERE DETAILS LIVE)
Эта секция — список целевых ссылок (PATH) для TOPICS/LIBRARIES.
Пока они могут быть пустыми (будут добавлены при наполнении).

### TOPICS (to create in 10_TOPICS/20_CHARACTER/)
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/20_CHARACTER/TOPIC__MOTIVATION_DESIRE.md
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/20_CHARACTER/TOPIC__WOUND_TRAUMA.md
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/20_CHARACTER/TOPIC__VALUES_MORAL_COMPASS.md
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/20_CHARACTER/TOPIC__CHARACTER_ARC.md
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/20_CHARACTER/TOPIC__RELATIONSHIP_DYNAMICS.md
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/20_CHARACTER/TOPIC__DIALOGUE_VOICE_PROFILE.md
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/20_CHARACTER/TOPIC__BEHAVIOR_UNDER_PRESSURE.md

### SHARED LIBRARIES (to create)
#### Rubrics
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/20_RUBRICS/RUBRIC__CHARACTER_QUALITY.md
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/20_RUBRICS/RUBRIC__DIALOGUE_QUALITY.md

#### Checklists
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/10_CHECKLISTS/CL__CHARACTER_PASS.md
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/10_CHECKLISTS/CL__VOICE_DIFFERENTIATION.md

#### Templates
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/30_TEMPLATES/TPL__CHARACTER_PROFILE.md
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/30_TEMPLATES/TPL__RELATIONSHIP_MAP.md

#### Examples
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/50_EXAMPLES/EXAMPLE__CHARACTER_PASS_PACK.md
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/50_EXAMPLES/EXAMPLE__CHARACTER_FAIL_PACK.md

---

## 7) ENTITY USAGE (HOW ENTITIES SHOULD CONSUME THIS)
Сущности подключают этот PILLAR через KB_SOURCES:
- как фундамент для character задач,
- а решения/варианты — через TOPICS,
- проверки — через RUBRICS/CHECKLISTS/QA/VAL.

---

## 8) NEXT EXPANSION (CONTROLLED)
Расширение допускается только:
- добавлением принципов/процедур верхнего уровня,
- добавлением ссылок на новые TOPICS/LIBRARIES,
- без переноса атомарных техник внутрь PILLAR.

Все изменения фиксируются в KB_CHANGELOG.

--- END.
