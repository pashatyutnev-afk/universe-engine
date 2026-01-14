# PILLAR — VISUAL & CINEMA (FOUNDATION TOME)
FILE: 04_KNOWLEDGE_BASE/01_PILLARS/04__PILLAR__VISUAL_CINEMA.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: PILLAR
INDEX_TYPE: FOUNDATION_TOME
LEVEL: L2
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.PILLAR.VISUAL.001
OWNER: SYSTEM
ROLE: Foundational visual/cinematic craft: composition principles, camera language, lighting principles, staging, continuity constraints, and high-level production procedures; detailed techniques live in TOPICS and quality instruments live in SHARED_LIBRARIES

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Initialized Visual & Cinema pillar as foundation tome skeleton compatible with KB source-lock and usage gate."
- REASON: "Provide stable visual language framework without duplicating atomic topics; enables consistent visual quality."
- IMPACT: "Entities can reference visual principles consistently; topics/libraries will carry actionable techniques, checklists, rubrics, and templates."
- CHANGE_ID: UE.CHG.2026-01-14.KB.PILLAR.VIS.001

---

## 0) PURPOSE (WHAT THIS PILLAR GIVES)
Этот PILLAR задаёт фундамент “ВИЗУАЛ И КИНОЯЗЫК”:
- принципы композиции и визуальной иерархии,
- язык камеры (что означает кадр и движение),
- принципы света (контраст/читаемость/настроение),
- staging (как ставится сцена в кадре),
- ограничения непрерывности (continuity) и читаемости,
- высокоуровневые процедуры проектирования визуала.

Детальные приёмы, сетапы, чеклисты, рубрики, шаблоны — в TOPICS/LIBRARIES.

---

## 1) SOURCE-LOCK / NO FANTASY (ABSOLUTE)
- Никаких домыслов и “красиво бы сделать так-то” без источника.
- Этот PILLAR — принципы и ограничения.
- Конкретные настройки/приёмы/шаблоны закрепляются модулями TOPICS/LIBRARIES по PATH.

---

## 2) CORE PRINCIPLES (FOUNDATION)
### P1) Clarity > beauty
Читаемость важнее декоративности.

### P2) Composition is information hierarchy
Композиция — это иерархия внимания: что зритель видит первым и почему.

### P3) Light defines form and meaning
Свет определяет форму, глубину и смысл (настроение/опасность/тепло/холод).

### P4) Camera is a point of view
Камера — это точка зрения. Кадр несёт позицию, не просто “показывает”.

### P5) Movement must be motivated
Движение камеры/объектов должно иметь причину (информация/эмоция/напряжение).

### P6) Continuity prevents confusion
Непрерывность (пространство/время/взгляды) нужна для понимания. Ошибки = шум.

### P7) Contrast is a control tool
Контраст (свет/форма/движение/цвет как принцип) управляет вниманием.

### P8) Visual rhythm supports narrative rhythm
Ритм смены планов и плотность деталей должны поддерживать драматургию.

> Примечание: цвет описывается как принципы контраста/читаемости, без “жёстких палитр”.

---

## 3) HIGH-LEVEL PROCEDURES (HOW TO BUILD)
### Proc A) Visual intent (top-down)
1) Определи цель сцены (эмоция/информация/напряжение).
2) Определи “главный объект внимания”.
3) Определи визуальный конфликт (что мешает чтению/что создаёт давление).
4) Определи стильные ограничения (простота/грязь/стерильность/хаос).
5) Выбери язык планов (общий/средний/крупный) по функции.

### Proc B) Shot planning (macro)
1) Establishing: где мы и что важно.
2) Coverage: кто действует и что меняется.
3) Emphasis: где пик сцены (выбор/удар/открытие).
4) Transition: как перейти в следующую сцену без потери ориентации.

### Proc C) Lighting intent (principles)
1) Читаемость форм (key/fill как идея, не конкретные числа).
2) Контраст по смыслу (опасно/безопасно; тайна/открытость).
3) Контроль фона (не перебивает главный объект).
4) Последовательность: не ломать свет без причины.

### Proc D) Continuity control (constraints)
1) Пространство: ось, направления, позиции.
2) Время: логика смены действий.
3) Взгляды: кто куда смотрит и почему.
4) Детали: ключевые объекты не “телепортируются”.

---

## 4) QUALITY FRAME (WHAT “GOOD” LOOKS LIKE)
Визуал считается качественным, если:
- главный объект читается без усилий,
- композиция ведёт взгляд,
- свет поддерживает смысл и форму,
- камера “говорит” (точка зрения ясна),
- движение мотивировано,
- continuity не ломает ориентацию,
- стиль последовательный (без случайных скачков).

Проверки качества должны делаться через:
- RUBRIC modules (visual quality / composition / continuity)
- CHECKLISTS (preflight, continuity guard)
- QA/VAL гейты (если применимо)

---

## 5) COMMON FAILURE MODES (ANTI-PATTERNS, HIGH LEVEL)
### F1) “Pretty but unreadable”
Красиво, но не ясно что происходит.

### F2) “Unmotivated camera”
Камера движется без функции → шум.

### F3) “Lighting chaos”
Свет скачет или рушит смысл/форму.

### F4) “Continuity breaks”
Ось/взгляды/позиции ломаются → зритель теряется.

### F5) “Flat staging”
Нет глубины, нет уровней, нет направленности действия.

---

## 6) REQUIRED CONNECTIONS (WHERE DETAILS LIVE)
Список целевых ссылок (PATH) на будущие TOPICS/LIBRARIES.

### TOPICS (to create in 10_TOPICS/40_VISUAL/)
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/40_VISUAL/TOPIC__VISUAL_COMPOSITION_PRINCIPLES.md
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/40_VISUAL/TOPIC__SHOT_LANGUAGE_PLANS.md
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/40_VISUAL/TOPIC__CAMERA_MOVEMENT_MOTIVATION.md
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/40_VISUAL/TOPIC__LIGHTING_CONTRAST_READABILITY.md
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/40_VISUAL/TOPIC__STAGING_BLOCKING.md
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/40_VISUAL/TOPIC__CONTINUITY_AXIS_EYELINES.md
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/40_VISUAL/TOPIC__VISUAL_RHYTHM_PACING.md

### SHARED LIBRARIES (to create)
#### Rubrics
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/20_RUBRICS/RUBRIC__VISUAL_CLARITY_QUALITY.md
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/20_RUBRICS/RUBRIC__CONTINUITY_QUALITY.md

#### Checklists
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/10_CHECKLISTS/CL__VISUAL_PREFLIGHT.md
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/10_CHECKLISTS/CL__CONTINUITY_GUARD.md

#### Templates
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/30_TEMPLATES/TPL__SHOT_LIST.md
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/30_TEMPLATES/TPL__VISUAL_SCENE_PACK.md

#### Examples
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/50_EXAMPLES/EXAMPLE__VISUAL_PASS_PACK.md
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/50_EXAMPLES/EXAMPLE__VISUAL_FAIL_PACK.md

---

## 7) ENTITY USAGE (HOW ENTITIES SHOULD CONSUME THIS)
Сущности подключают этот PILLAR через KB_SOURCES:
- как фундамент для visual/cinema задач,
- детали — через TOPICS,
- контроль качества — через RUBRICS/CL/QA/VAL.

Важно:
- PILLAR фиксирует принципы и ограничения,
- конкретные “монтажные решения” и детальные режиссёрские варианты не закрепляются здесь (они живут в отдельных модулях с чёткими рамками/рисками).

---

## 8) NEXT EXPANSION (CONTROLLED)
Расширение допускается только:
- добавлением принципов/процедур верхнего уровня,
- добавлением ссылок на новые TOPICS/LIBRARIES,
- без переноса атомарных техник внутрь PILLAR.

Все изменения фиксируются в KB_CHANGELOG.

--- END.
