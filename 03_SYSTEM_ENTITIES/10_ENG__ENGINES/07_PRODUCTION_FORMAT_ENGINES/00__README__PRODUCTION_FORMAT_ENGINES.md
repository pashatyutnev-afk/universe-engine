# PRODUCTION FORMAT ENGINES — Realm
FILE: 00__README__PRODUCTION_FORMAT_ENGINES.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 07_PRODUCTION_FORMAT_ENGINES
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Realm file for production/format engines (genre, format rules, adaptation, medium-specific pipelines)

---

## WHAT THIS FAMILY IS

**PRODUCTION_FORMAT_ENGINES** — слой, который отвечает за превращение канона/идей/сюжетной логики в
**реально выпускаемый продукт** под конкретный формат:

- книга
- сериал/эпизоды
- short content
- YouTube longform
- игровая нарративная структура

Это не про “что в мире”, а про:
- как упаковать
- какие правила у формата
- какие ограничения и возможности
- какой “пайплайн выпуска”

---

## WHY IT EXISTS

Без него проект тонет:
- есть мир/сюжет, но нет продуктовой формы
- темп и структура ломаются при переносе между форматами
- жанр плавает от сцены к сцене
- невозможно масштабировать выпуск

---

## INPUT / OUTPUT

### Inputs
- Canon constraints (world law, continuity)
- Narrative/character/world engines outputs
- Project goals (audience, platform, release cadence)
- Production constraints (time, scope, assets)

### Outputs
- Format spec (правила формата)
- Genre spec (жанр, обещание аудитории)
- Structure templates (эпизод, глава, выпуск)
- Adaptation mapping (что переносим/режем/сливаем)
- Quality gates (для QA/VAL)

---

## FAMILY-WIDE CANON TERMS

### FORMAT SPEC
Документ с правилами:
- unit of content (глава/эпизод/видео/миссия)
- duration/length targets
- beat density (сколько смысловых событий на единицу)
- cliffhanger / hook rules
- recap rules
- CTA rules (если платформа требует)

### RELEASE CADENCE
- как часто выходит контент
- как устроена сезонность
- как делаем “пакеты” (batch)

### ADAPTATION MAP
- перенос из исходника в целевой формат:
  - keep / cut / merge / split / transform

---

## FAMILY CONTENTS

01 — Genre Engine
02 — Genre Blending Engine
03 — Format Adaptation Engine
04 — Book Format Engine
05 — Series & Episode Engine
06 — Short Content Engine
07 — YouTube Longform Engine
08 — Game Narrative Engine

---

## FAMILY-WIDE VALIDATION

- PF1: Любой формат имеет “unit of content” и чёткие метрики длины.
- PF2: Жанр — это обещание. Оно не нарушается без осознанного переворота.
- PF3: Адаптация всегда фиксирует: keep/cut/merge/split/transform.
- PF4: На каждый формат есть шаблон структуры (template) для штамповки.

---
OWNER: Universe Engine
STATUS: FIXED
