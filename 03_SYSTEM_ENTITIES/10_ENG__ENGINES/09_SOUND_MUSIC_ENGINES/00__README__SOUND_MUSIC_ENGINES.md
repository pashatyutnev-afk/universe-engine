# SOUND & MUSIC ENGINES — Realm
FILE: 00__README__SOUND_MUSIC_ENGINES.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 09_SOUND_MUSIC_ENGINES
CLASS: PRODUCTION (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Realm file for deep music/audio creation engines (composition, structure, harmony, melody, rhythm, lyrics, arrangement, vocal performance, sound design, music-to-scene, mix/master); complements production-layer audio rules in KNOWLEDGE_PRODUCTION_ENGINES

---

## WHAT THIS FAMILY IS

**SOUND_MUSIC_ENGINES** — это “глубокий музыкальный слой”.
Он отвечает не за монтажную синхру и базовый продакшн, а за:

- композицию (музыкальные идеи и формы)
- структуру трека/песни
- гармонию/аккорды
- мелодию/хук
- ритм/грув
- рифму/размер (если вокал)
- текст (лирический слой)
- аранжировку/инструментовку
- вокальную подачу/перформанс
- саунд-дизайн (как звуковая ткань/тембры/FX)
- привязку музыки к сцене (эмоции/арка/монтаж)
- микс/мастер (финальная техническая форма)

Это семейство делает **музыкальные артефакты**, которые можно:
- повторить по спецификации
- масштабировать сериями/альбомом/саундтреком
- сохранять стиль мира/проекта

---

## WHY IT EXISTS

Потому что “звук продакшна” ≠ “музыка как система”.

Если держать музыку только на уровне:
- “поставь трек сюда”
- “сделай громкость так”
то получится случайность, а не узнаваемый саунд.

Эта папка фиксирует:
- **логические правила музыки**
- **управление стилем**
- **воспроизводимость**
- **переиспользуемые шаблоны**

---

## CRITICAL SEPARATION (LAW)

### 08_KNOWLEDGE_PRODUCTION_ENGINES/08__SOUND_MUSIC_ENG.md = PRODUCTION LAYER
Там:
- sound palette (категории звуков)
- ambience layers
- music placement rules
- sync markers
- loudness/clarity
- mix targets “как в монтажке”
- правила “диалог читаем, FX не душит”

### 09_SOUND_MUSIC_ENGINES = DEEP MUSIC LAYER
Тут:
- композиция/гармония/мелодия/ритм
- аранж/вокал/саунд-дизайн как материал
- music-to-scene на уровне смысла
- микс/мастер как финальный продукт

> Rule: если вопрос “куда поставить” — это 08.  
> если вопрос “что за музыка и почему она такая” — это 09.

---

## INPUT / OUTPUT

### Inputs
- Scene/arc emotional targets (from narrative/character engines)
- Genre/style locks (from genre/style engines)
- Platform constraints (runtime, loudness targets)
- Production rhythm map (from Editing engine)
- Reference tracks / “do not” list (optional)

### Outputs
- Music specs (themes, motifs, structure, harmony)
- Prompt packs / midi/notation notes (engine-agnostic)
- Arrangement plans
- Vocal performance notes
- Sound design palette (deep)
- Mix/Master targets for final deliverable
- Consistency bibles for soundtrack

---

## FAMILY-WIDE CANON TERMS

### THEME
Музыкальная идея персонажа/места/силы.

### MOTIF
Короткий узнаваемый элемент (интервал, ритм, тембр).

### HOOK
Главный “крючок” трека (мелодический/ритмический/тембровый).

### GROOVE
Чувство движения (не только bpm, а “кач”).

### ARRANGEMENT
Кто играет что и когда, слойность, динамика.

### MIX / MASTER
Финальная техническая форма: баланс, динамика, громкость, переводимость.

### STYLE CONSISTENCY
Когда 3 трека подряд звучат “как одна вселенная”.

---

## FAMILY CONTENTS (CANON ORDER)

01 — Music Composition Engine  
02 — Song Structure Engine  
03 — Harmony / Chord Engine  
04 — Melody / Hook Engine  
05 — Rhythm / Groove Engine  
06 — Rhyme / Meter Engine  
07 — Lyrics Engine  
08 — Arrangement / Instrumentation Engine  
09 — Vocal Performance Engine  
10 — Sound Design Engine  
11 — Music Style Consistency Engine  
12 — Music To Scene Engine  
13 — Mix / Master Engine  

---

## FAMILY-WIDE VALIDATION (GATES)

- SM1: Музыка служит смыслу (scene/arc), а не “просто красиво”.
- SM2: Есть повторяемость по спецификации (не случайность).
- SM3: Стиль фиксирован (Style Consistency обязателен при серии/альбоме).
- SM4: Музыкальные решения согласованы с монтажным ритмом (Editing engine) и placement-правилами (08 audio layer).
- SM5: Финал переводим и технически чист (mix/master targets).

---

## GOVERNANCE NOTE

Любая смена:
- терминов
- порядка движков
- правил разделения 08/09
проходит governance pipeline:
- Change Control
- Canon Authority
- Versioning & Memory
- Audit Log

---

OWNER: Universe Engine
STATUS: FIXED
