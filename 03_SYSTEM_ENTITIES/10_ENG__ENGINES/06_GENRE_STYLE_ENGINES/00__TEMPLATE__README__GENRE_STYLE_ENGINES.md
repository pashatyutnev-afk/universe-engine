# ENG GENRE & STYLE ENGINES — REALM (FAMILY README)
FILE: 00__README__GENRE_STYLE_ENGINES.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 06_GENRE_STYLE_ENGINES
CLASS: STYLE (L3)
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
ROLE: Realm rules + boundaries + interfaces for tone/mood/atmosphere/symbolism/sensory style control

---

## 0) PURPOSE (REALM LAW)

Эта FAMILY владеет **ощущением произведения**:
тоном, настроением, атмосферой, эмоциональным резонансом, символизмом,
метафорикой и сенсорной детализацией.

Задача: чтобы любая сцена/эпизод/артефакт имели **единый стиль** и
правильную “температуру ощущения” без дублирования функций narrative/world/production.

---

## 1) OWNERSHIP (BOUNDARIES)

### THIS FAMILY OWNS
- Tone & Mood (тон и настроение)
- Atmosphere (атмосфера: воздух, давление, среда)
- Emotional Resonance (какой след остаётся в читателе/зрителе)
- Symbolism (символические образы и смысловые якоря)
- Metaphor (метафорические конструкции как стиль мышления)
- Sensory Detail (сенсорика: звук/запах/тактильность/визуальные ощущения)

### THIS FAMILY DOES NOT OWN
- Сюжетная структура/сцены/арки (см. `02_DOMAIN_NARRATIVE_ENGINES`)
- Механика событий/причинность/конфликт (см. `05_EXPRESSION_ENGINES`)
- Мотивация/психология/речь персонажей (см. `03_DOMAIN_CHARACTER_ENGINES`)
- Законы мира/история/эпохи/экономика/технологии (см. `04_DOMAIN_WORLD_ENGINES`)
- Продакшн-реализация: камера/свет/монтаж/саунд на уровне производства (см. `08_KNOWLEDGE_PRODUCTION_ENGINES`)
- Глубокая музыка (композиция/гармония/аранж/вокал/микс) (см. `09_SOUND_MUSIC_ENGINES`)

---

## 2) CRITICAL BOUNDARIES (ANTI-DUPLICATION)

### Style vs Meaning
- Meaning (Theme/Message) принадлежит Narrative (Theme & Meaning)
- Style — это **как чувствуется**, а не “что автор хотел сказать”

### Atmosphere vs World Environment
- World Environment = факты мира (климат/экология/условия)
- Atmosphere = художественная подача ощущения среды (давление/температура/вкус)

### Style vs Production
- Production engines решают “как снять/сделать/смонтировать”
- Style engines задают “какая эмоция и язык образов”, независимо от медиа

---

## 3) CANON ORDER (MANDATORY)

01 — Tone & Mood Engine  
02 — Atmosphere Engine  
03 — Emotional Resonance Engine  
04 — Symbolism Engine  
05 — Metaphor Engine  
06 — Sensory Detail Engine  

---

## 4) STYLE INTERFACES (INPUT/OUTPUT TYPES)

### INPUT TYPES (typical)
- STORY_CONTEXT (scene/episode context)
- CHARACTER_STATE (optional)
- WORLD_CONSTRAINTS (optional)
- THEME_GUIDANCE (optional, read-only)
- PRODUCTION_CONTEXT (optional)

### OUTPUT TYPES (typical)
- STYLE_PROFILE (единый профиль стиля)
- TONE_MOOD_PROFILE
- ATMOSPHERE_PROFILE
- RESONANCE_TARGET
- SYMBOL_SET
- METAPHOR_BANK
- SENSORY_PALETTE

OUTPUT_TARGET (recommended):
- `04_PROJECTS/<project>/03_NARRATIVE/STYLE/`
- `04_PROJECTS/<project>/CANON/STYLE/`

---

## 5) GOVERNANCE RULES (MANDATORY)

- Любые новые “стилевые законы” должны быть совместимы с каноном (Change Control).
- Запрещено вводить стиль, который ломает уже закреплённые символы/тон без явной версии.

---

## 6) REQUIRED LINKS

- Global index: `../02__INDEX_ALL_ENGINES.md`
- Narrative family: `../02_DOMAIN_NARRATIVE_ENGINES/`
- Production family: `../08_KNOWLEDGE_PRODUCTION_ENGINES/`
- Change Control: `../00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md`

---

## 7) AUTHOR RULES (MANDATORY)

- У каждого движка обязателен mini-contract.
- У каждого движка обязателен блок Boundaries.
- Стиль всегда задаётся **контролируемо**: параметры + допустимые диапазоны.

---

OWNER: Universe Engine
LOCK: OPEN
