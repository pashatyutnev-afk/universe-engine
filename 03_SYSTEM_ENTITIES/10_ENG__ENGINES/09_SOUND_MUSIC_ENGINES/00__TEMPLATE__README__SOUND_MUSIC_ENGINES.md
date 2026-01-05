# ENG SOUND & MUSIC ENGINES — REALM (FAMILY README)
FILE: 00__README__SOUND_MUSIC_ENGINES.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 09_SOUND_MUSIC_ENGINES
CLASS: SOUND (L3)
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
ROLE: Realm rules + boundaries + interfaces for deep music creation (composition → production → mix/master → scene integration)

---

## 0) PURPOSE (REALM LAW)

Эта FAMILY отвечает за **глубокую музыку (Deep Music)** как самостоятельный слой производства:
- композиция и музыкальные идеи
- структура трека/песни
- гармония/аккорды
- мелодии/хуки
- ритм/грув
- рифма/метр (для текста)
- текст песни
- аранжировка/инструментовка
- вокальное исполнение
- саунд-дизайн как музыкальная субстанция
- консистентность музыкального стиля
- привязка музыки к сценам (музыкальная драматургия)
- финальный микс/мастер

Главное отличие: здесь создаётся **музыка как произведение**, а не “производственный звук для сцены”.

---

## 1) OWNERSHIP (BOUNDARIES)

### THIS FAMILY OWNS
- Musical composition system (themes, motifs, hooks)
- Harmonic language (chords, progression, tension/release in music)
- Arrangement + instrumentation decisions
- Lyrics as musical layer (prosody, rhyme/meter, phrasing)
- Vocal performance direction (interpretation, articulation, dynamics)
- Music-focused sound design (textures, synth design, musical FX)
- Mix/Master specs as music finalization
- Music-to-scene mapping (leitmotifs, cue placement, emotional timing)

### THIS FAMILY DOES NOT OWN
- Production audio layer (sync/design/placement/clarity for picture)
  → `08_KNOWLEDGE_PRODUCTION_ENGINES/08__SOUND_MUSIC_ENG.md`
- Editing rhythm rules (screen-time pacing)
  → `08_KNOWLEDGE_PRODUCTION_ENGINES/07__EDITING_MONTAGE_ENG.md`
- Narrative structure/arcs/scenes as story mechanics
  → `02_DOMAIN_NARRATIVE_ENGINES/*`
- Authorial tone/atmosphere/symbolism definitions (как литературный стиль)
  → `06_GENRE_STYLE_ENGINES/*`
- Dialogue content / character psychology
  → `03_DOMAIN_CHARACTER_ENGINES/*`

---

## 2) CRITICAL BOUNDARIES (ANTI-DUPLICATION)

### Production Audio vs Deep Music (HARD RULE)
- **Production audio** = звук “для кадра”: синхрон, чистота, размещение, минимальный дизайн под сцену.
  → `08_KNOWLEDGE_PRODUCTION_ENGINES/08__SOUND_MUSIC_ENG.md`
- **Deep music** = музыка как произведение: композиция, гармония, аранжировка, вокал, микс/мастер.
  → `09_SOUND_MUSIC_ENGINES/*`

### Sound Design Placement
- В этой FAMILY: sound design как **музыкальный материал** (тембры, текстуры, синт).
- В production layer: sound design как **сцено-ориентированный** слой (SFX/ambience placement).

---

## 3) CANON ORDER (MANDATORY)

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

## 4) MUSIC INTERFACES (INPUT/OUTPUT TYPES)

### INPUT TYPES (typical)
- NARRATIVE_MATERIAL (read-only): сцены/эпохи/драмы/смысл
- STYLE_PROFILE (read-only): тон/атмосфера/жанр
- CHARACTER_THEMES (read-only): кто/что получает лейтмотивы
- FORMAT_SPEC: длительность, темп, назначение (intro, theme, cue, montage)
- MUSICAL_REFERENCES: референсы/палитра/ограничения
- PRODUCTION_CONSTRAINTS: инструменты, вокалист, сроки, бюджет

### OUTPUT TYPES (typical)
- THEME_BANK / MOTIF_LIBRARY
- CHORD_PROGRESSIONS / HARMONY_SHEET
- MELODY_HOOK_SET
- RHYTHM_GROOVE_PATTERNS
- LYRIC_DRAFTS / FINAL_LYRICS
- ARRANGEMENT_SPECS / INSTRUMENTATION_PLAN
- VOCAL_DIRECTION_SHEET
- SOUND_DESIGN_PATCHES / TEXTURE_LIBRARY
- MUSIC_STYLE_GUIDE (consistency)
- CUE_SHEET / MUSIC_TO_SCENE_MAP
- MIX_SPEC / MASTER_SPEC
- FINAL_STEMS / FINAL_MASTERS (artifact output)

OUTPUT_TARGET (recommended):
- `04_PROJECTS/<project>/02_MUSIC/`
  - `00_STYLE_GUIDES/`
  - `01_COMPOSITION/`
  - `02_ARRANGEMENT/`
  - `03_VOCALS/`
  - `04_SOUND_DESIGN/`
  - `05_MIX_MASTER/`
  - `06_CUE_SHEETS/`
  - `07_EXPORTS/`

---

## 5) QUALITY STANDARD (MUSIC)

Минимальные критерии:
- композиционная цель ясна (что должна делать музыка)
- есть мотив/тема или палитра (не “случайный трек”)
- структура соответствует назначению (cue/песня/theme)
- consistency соблюдается (если это серия/пак)
- deliverables воспроизводимы и версионируемы (stems, specs, sheets)

---

## 6) GOVERNANCE RULES (MANDATORY)

- Музыкальные решения, влияющие на канон (лейтмотивы цивилизаций/персонажей/эпох),
  фиксируются как изменение канона и проходят governance pipeline.
- Версионирование обязано сохранять: мотивы, темп/тональность, назначение, стемы.

---

## 7) REQUIRED LINKS

- Global index: `../02__INDEX_ALL_ENGINES.md`
- Production sound boundary: `../08_KNOWLEDGE_PRODUCTION_ENGINES/08__SOUND_MUSIC_ENG.md`
- Narrative rhythm: `../02_DOMAIN_NARRATIVE_ENGINES/05__PACING_RHYTHM_ENG.md`
- Change Control: `../00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md`

---

## 8) AUTHOR RULES (MANDATORY)

- Каждый движок обязан иметь mini-contract.
- Каждый движок обязан выдавать проверяемый артефакт: sheet/spec/guide/stems/map.
- Все входы из narrative/style/world — read-only (движки не переписывают канон).

---

OWNER: Universe Engine
LOCK: OPEN
