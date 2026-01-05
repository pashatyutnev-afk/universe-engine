# ENG PRODUCTION FORMAT ENGINES — REALM (FAMILY README)
FILE: 00__README__PRODUCTION_FORMAT_ENGINES.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 07_PRODUCTION_FORMAT_ENGINES
CLASS: PRODUCTION (L3)
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
ROLE: Realm rules + boundaries + interfaces for selecting/adapting release formats (book/series/short/youtube/game)

---

## 0) PURPOSE (REALM LAW)

Эта FAMILY отвечает за **формат выпуска** проекта:
как именно история/материал будет упакован и произведён как продукт.

Здесь решается:
- какой формат выбран (книга / сериал / короткий контент / YouTube long / игра)
- какие ограничения и требования формат накладывает на narrative/style/production
- как адаптировать материал под формат без разрушения канона

---

## 1) OWNERSHIP (BOUNDARIES)

### THIS FAMILY OWNS
- Genre selection as product framing (жанр как упаковка для аудитории)
- Genre blending rules for release packaging
- Format adaptation (перевод одного формата в другой)
- Book format constraints (главы, темп чтения, объём)
- Series/Episode constraints (сезоны, эпизоды, серийная драматургия)
- Short content constraints (хук, длительность, плотность)
- YouTube longform constraints (ритм подачи, структура выпуска, удержание)
- Game narrative constraints (игровые петли, квест-структура, агентность игрока)

### THIS FAMILY DOES NOT OWN
- Сюжетные законы и канон истории (см. `02_DOMAIN_NARRATIVE_ENGINES`)
- Механика событий/причинность/конфликт (см. `05_EXPRESSION_ENGINES`)
- Глубокий стиль/символизм/сенсорика как художественный язык (см. `06_GENRE_STYLE_ENGINES`)
- Продакшн-исполнение (камера/свет/монтаж/саунд на уровне производства) (см. `08_KNOWLEDGE_PRODUCTION_ENGINES`)
- Глубокая музыка (см. `09_SOUND_MUSIC_ENGINES`)
- Факты мира и его законы (см. `04_DOMAIN_WORLD_ENGINES`)
- Персонажная психология/речь (см. `03_DOMAIN_CHARACTER_ENGINES`)

---

## 2) CRITICAL BOUNDARIES (ANTI-DUPLICATION)

### Genre vs Style
- Genre здесь — как **продуктовая рамка/обещание аудитории**
- Style (тон/атмосфера/символизм) принадлежит `06_GENRE_STYLE_ENGINES`

### Format Rhythm vs Editing Rhythm
- Формат может задавать требования к “плотности/темпу” материала
- Монтаж/экранный ритм принадлежит `08_KNOWLEDGE_PRODUCTION_ENGINES/07__EDITING_MONTAGE_ENG.md`

### Format vs Story Structure
- Формат задаёт ограничения и “контейнер”
- История и драматургия принадлежат Narrative engines (L2)

---

## 3) CANON ORDER (MANDATORY)

01 — Genre Engine  
02 — Genre Blending Engine  
03 — Format Adaptation Engine  
04 — Book Format Engine  
05 — Series & Episode Engine  
06 — Short Content Engine  
07 — YouTube Longform Engine  
08 — Game Narrative Engine  

---

## 4) FORMAT INTERFACES (INPUT/OUTPUT TYPES)

### INPUT TYPES (typical)
- PROJECT_INTENT (цель проекта)
- AUDIENCE_TARGET (аудитория/платформа)
- NARRATIVE_MATERIAL (синопсис/арки/сцены)
- STYLE_PROFILE (optional)
- PRODUCTION_CONSTRAINTS (ресурсы/время/платформа)

### OUTPUT TYPES (typical)
- FORMAT_SPEC (главный документ формата)
- GENRE_PACKAGE
- EPISODE_BLUEPRINT / CHAPTER_BLUEPRINT
- SHORT_SCRIPT_RULESET
- YT_LONGFORM_STRUCTURE
- GAME_NARRATIVE_LOOP_SPEC

OUTPUT_TARGET (recommended):
- `04_PROJECTS/<project>/01_PRODUCTION/FORMAT/`
- `04_PROJECTS/<project>/CANON/FORMAT/`

---

## 5) GOVERNANCE RULES (MANDATORY)

- Выбор формата — каноническое решение: фиксируется в audit/change control.
- Смена формата = change request (влияет на структуру артефактов и пайплайн).

---

## 6) REQUIRED LINKS

- Global index: `../02__INDEX_ALL_ENGINES.md`
- Change Control: `../00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md`
- Narrative family: `../02_DOMAIN_NARRATIVE_ENGINES/`
- Production family: `../08_KNOWLEDGE_PRODUCTION_ENGINES/`
- Style family: `../06_GENRE_STYLE_ENGINES/`

---

## 7) AUTHOR RULES (MANDATORY)

- У каждого движка обязателен mini-contract.
- Каждый движок обязан выдавать **FORMAT_SPEC** (или производный артефакт) как проверяемый результат.
- Формат должен быть повторяемым (не “вкусовщина”), а параметризуемым.

---

OWNER: Universe Engine
LOCK: OPEN
