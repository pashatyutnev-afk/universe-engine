# ENG SOUND & MUSIC ENGINE — TEMPLATE
FILE: NN__<ENGINE_NAME>_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 09_SOUND_MUSIC_ENGINES
CLASS: SOUND (L3)
ENGINE_ID: ENG.SOUND.NN.<ENGINE_NAME>
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
ROLE: <one-line purpose of this deep music engine>

---

## 0) PURPOSE (LAW)

Этот движок создаёт музыкальный артефакт(ы) как часть Deep Music слоя:
- композиционная функция (что музыка делает)
- музыкальная форма (как устроено)
- воспроизводимый результат (sheets/spec/stems)

---

## 1) OWNERSHIP (BOUNDARIES)

### OWNS
- <что именно создаёт движок в музыке: motif/harmony/lyrics/arrangement/vocals/etc>

### DOES NOT OWN
- Production audio sync/placement/clarity → `08_KNOWLEDGE_PRODUCTION_ENGINES/08__SOUND_MUSIC_ENG.md`
- Narrative structure decisions → `02_DOMAIN_NARRATIVE_ENGINES/*`
- Authorial style definitions → `06_GENRE_STYLE_ENGINES/*`

---

## 2) WHEN TO USE (TRIGGERS)

Используй когда:
- [ ] нужно создать/обновить музыкальную палитру/мотивы
- [ ] нужно собрать структуру/гармонию/мелодии
- [ ] нужно написать текст/вокальную линию
- [ ] нужно собрать аранжировку
- [ ] нужно обеспечить консистентность
- [ ] нужно привязать музыку к сценам
- [ ] нужно финализировать миксом/мастером

---

## 3) MINI-CONTRACT (MANDATORY)

CONSUMES:
- <MUSICAL_REFERENCES>
- <FORMAT_SPEC>
- <PRODUCTION_CONSTRAINTS>
- <NARRATIVE_MATERIAL (READ-ONLY)>
- <STYLE_PROFILE (READ-ONLY)>

PRODUCES:
- <SHEET/SPEC/GUIDE>
- <STEMS/EXPORTS/MAPS>

DEPENDS_ON:
- []  # при необходимости перечисли другие движки 09_* (или boundary refs)

OUTPUT_TARGET:
- `04_PROJECTS/<project>/02_MUSIC/`

---

## 4) CONTROL SURFACE (PARAMETERS)

Пример параметров:
- deliverable_mode: sketch | draft | production | final
- target_use: theme | cue | montage | song | trailer
- duration: (sec/min)
- tempo_bpm: (range or fixed)
- key_center: (optional)
- mood_profile: (tags)
- instrumentation_palette: (list)
- vocal_mode: none | lead | choir | adlibs
- consistency_profile: strict | flexible

---

## 5) PROCESS (HOW IT WORKS)

1) Read constraints + narrative/style (read-only)
2) Define musical goal (function)
3) Generate core material (motif/harmony/melody/rhythm/lyrics)
4) Arrange + orchestrate
5) Produce exports (stems/sheets/spec)
6) QA + versioning notes

---

## 6) QUALITY CHECKS

- [ ] Цель музыки определена (function)
- [ ] Есть мотив/палитра (или осознанное отсутствие)
- [ ] Структура соответствует назначению
- [ ] Консистентность соблюдена (если часть пакета)
- [ ] Артефакты воспроизводимы (sheets/spec + stems)
- [ ] Нет нарушения границ (production sound не захвачен)

---

## 7) FAILURE MODES

- Failure 1 → симптом → как чинить
- Failure 2 → симптом → как чинить

---

## 8) RAW LINK (MANDATORY)

🔗 RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/NN__<ENGINE_NAME>_ENG.md

---

OWNER: Universe Engine
LOCK: OPEN
