# GENRE & STYLE ENGINES — README TEMPLATE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/06_GENRE_STYLE_ENGINES/00__TEMPLATE__README__GENRE_STYLE_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: TEMPLATE
FAMILY: 06_GENRE_STYLE_ENGINES
CLASS: STYLE (L3)
LEVEL: L3
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.STYLE.TPL.README.001
OWNER: SYSTEM
ROLE: Mandatory README (realm) template for the GENRE & STYLE engine family. Defines scope, boundaries, how-to-use, outputs, integration contracts, and anti-duplication laws.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Style family README template standardized: scope/boundaries, engine map skeleton, outputs, integration, and S0 blockers."
- REASON: "Stop family drift and keep style engines separated from narrative/world/production."
- IMPACT: "All style engines become consistent, navigable, and safely reusable."
- CHANGE_ID: UE.CHG.2026-01-08.STYLE.TPL.README.001

---

## 0) PURPOSE (LAW)

Этот README — **realm-файл** семейства `06_GENRE_STYLE_ENGINES`.

Он фиксирует:
- что такое **STYLE (L3)** в Universe Engine
- границы ответственности семейства (что МОЖНО / что НЕЛЬЗЯ)
- как пользоваться движками семьи (deterministic flow)
- какие типы артефактов семья производит (стандартизировано)
- как семья стыкуется с NARRATIVE / CHARACTER / WORLD / EXPRESSION / PRODUCTION

EXISTENCE RULE (FAMILY):
- Семейство считается живым только если:
  - README существует и соответствует этому шаблону
  - все движки семьи зарегистрированы в `02__INDEX_ALL_ENGINES.md`
  - у каждого движка есть mini-contract

---

## 1) WHAT THIS FAMILY IS (DEFINITION)

**GENRE & STYLE engines** — это движки, которые **задают “как это ощущается”**, а не “что происходит”.

Семейство владеет:
- TONE / MOOD (направление чувств)
- ATMOSPHERE (правила атмосферы и ощущений)
- SYMBOLISM / METAPHOR (палитры смысловых образов, но НЕ сюжет)
- SENSORY DETAIL (сенсорные приоритеты: звук/запах/тактильность/визуал)

Семейство не владеет:
- сюжетом и смыслом как первичной логикой (это Narrative)
- психикой/мотивацией персонажей как первичным источником (это Character)
- законами мира как первичной структурой (это World)
- механикой событий (это Expression)
- реализацией в кадре/монтаже/прод-звуке (это Knowledge Production / Sound & Music)

---

## 2) SCOPE (IN / OUT)

### 2.1 IN SCOPE (ALLOWED)
- Формализованные **ограничения стиля**, которые можно проверить
- Профили (profiles) и палитры (palettes), применимые к сценам/эпизодам/форматам
- Правила согласованности “ощущения” между сценами

### 2.2 OUT OF SCOPE (FORBIDDEN)
- Написание сюжета/сцен как первичный контент
- Определение законов мира/истории мира как первичный контент
- Определение мотиваций/травм/отношений как первичный контент
- Описание монтажных приёмов/камеры/саунд-дизайна как исполнения

Rule:
- Если нужен “как реализовать” → Style выдаёт **constraint**, Production реализует.

---

## 3) FAMILY OUTPUT TYPES (CANON SET)

Семейство обязано производить **только** артефакты “constraints/profiles”, например:

- `TONE_PROFILE`
- `MOOD_PROFILE`
- `ATMOSPHERE_RULESET`
- `SYMBOLISM_MAP`
- `METAPHOR_PALETTE`
- `SENSORY_PALETTE`
- `STYLE_INVARIANTS` (инварианты согласованности)

Запрещено выдавать как основной output:
- `SCENE_SCRIPT`, `PLOT_PLAN`, `CHARACTER_BACKSTORY`, `WORLD_LAWSET`
- `CAMERA_PLAN`, `EDITING_CUTLIST`, `MIX_SESSION` (это Production/Sound)

---

## 4) HOW TO USE (DETERMINISTIC FLOW)

Рекомендованный порядок применения:
1) Получи базовые входы:
   - Story Structure (Narrative)
   - Character constraints (Character)
   - World constraints (World)
   - Event mechanics (Expression) — если нужно
2) Выбери стиль/жанровую рамку (Production Format / Genre)
3) Прогони движки Style семьи по порядку (по номерам)
4) Сгенерируй style artifacts (profiles/palettes/rulesets)
5) Передай constraints в:
   - Narrative engines (для согласованного текста)
   - Production engines (для реализации в медиа)

Hard rule:
- Style никогда не “переписывает” Narrative/World/Character; он только ограничивает “как ощущается”.

---

## 5) ANTI-DUPLICATION BOUNDARIES (CRITICAL)

### 5.1 Style vs Narrative
- Style = “ощущение/тон/атмосфера”
- Narrative = “логика истории/структура/смысл”

### 5.2 Style vs Production (camera/editing/sound)
- Style = “constraint”
- Production = “implementation plan + execution”

### 5.3 Style vs Deep Music
- Style может задавать музыкальную палитру как constraint (“cold minimal pulse”),
- но композиция/аранж/микс — в `09_SOUND_MUSIC_ENGINES`

---

## 6) ENGINE MAP (FILL BY FAMILY)

(Сюда вставляется список движков семьи по канону.
Нумерация и названия — строго как в `02__INDEX_ALL_ENGINES.md`)

01 — <Engine 01 title> — 🔗 <raw-link>
02 — <Engine 02 title> — 🔗 <raw-link>
03 — <Engine 03 title> — 🔗 <raw-link>
...

---

## 7) MINI-CONTRACT RULE (FAMILY LAW)

Каждый engine файла этой семьи обязан иметь:

CONSUMES:
- конкретные типы входов (не “вдохновение”, а артефакты)

PRODUCES:
- конкретные style artifacts со схемами

DEPENDS_ON:
- только объявленные зависимости
- допустимо зависеть от Domain семейств, но не “замещать” их

OUTPUT_TARGET:
- обязателен (куда кладём результат в проектах)

---

## 8) S0 BLOCKERS (FAMILY STOP CONDITIONS)

- S0-1: Engine семьи пишет сюжет/сцены как primary output
- S0-2: Engine семьи описывает монтаж/камеру/микс как primary output
- S0-3: Нет output schema (невозможно проверить полноту)
- S0-4: Скрытая зависимость (не указана в DEPENDS_ON)
- S0-5: Два engines семьи объявляют одного и того же “single owner” области без tier/разделения

---

## 9) INTEGRATION (SYSTEM FIT)

Inputs:
- `02_DOMAIN_NARRATIVE_ENGINES/*`
- `03_DOMAIN_CHARACTER_ENGINES/*`
- `04_DOMAIN_WORLD_ENGINES/*`
- `05_EXPRESSION_ENGINES/*` (при необходимости)
- `07_PRODUCTION_FORMAT_ENGINES/*` (жанровая рамка)

Outputs consumed by:
- Narrative engines (как constraints на текст/сцены)
- `08_KNOWLEDGE_PRODUCTION_ENGINES/*` (реализация в визуале/монтаже/прод-звуке)
- `09_SOUND_MUSIC_ENGINES/*` (глубокая музыка — как constraint, не как инструкция)

---

## 10) TEMPLATE LINKS (RAW ONLY)

ENGINE TEMPLATE (this family):
- <raw-link to 00__TEMPLATE__ENGINE__GENRE_STYLE_ENGINES.md>

README TEMPLATE (this family):
- <raw-link to this file>

INDEX (ENG):
- <raw-link to 02__INDEX_ALL_ENGINES.md>

--- END.
