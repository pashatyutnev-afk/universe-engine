# ENG GENRE/STYLE ENGINE — TEMPLATE
FILE: NN__<ENGINE_NAME>_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 06_GENRE_STYLE_ENGINES
CLASS: STYLE (L3)
ENGINE_ID: ENG.STYLE.NN.<ENGINE_NAME>
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
ROLE: <one-line purpose of this style engine>

---

## 0) PURPOSE (LAW)

Что этот движок делает:
- какой именно аспект “ощущения” управляет
- какие параметры задаёт
- как выглядит выходной стиль-артефакт

---

## 1) OWNERSHIP (BOUNDARIES)

### OWNS
- <что именно регулирует этот движок>

### DOES NOT OWN
- Story structure / narrative arcs (02_DOMAIN_NARRATIVE_ENGINES)
- Event mechanics / conflict causality (05_EXPRESSION_ENGINES)
- Character psychology / motivation / dialogue (03_DOMAIN_CHARACTER_ENGINES)
- World facts / laws / history (04_DOMAIN_WORLD_ENGINES)
- Production implementation (08_KNOWLEDGE_PRODUCTION_ENGINES)
- Deep music craft (09_SOUND_MUSIC_ENGINES)

---

## 2) WHEN TO USE (TRIGGERS)

Используй когда:
- [ ] нужно унифицировать тон/настроение по проекту
- [ ] сцена “не чувствуется” и надо задать атмосферу
- [ ] надо усилить эмоциональный след (resonance)
- [ ] надо закрепить символы/образы и не расползтись
- [ ] надо построить метафорический язык проекта
- [ ] надо добавить сенсорику без перегруза

---

## 3) MINI-CONTRACT (MANDATORY)

CONSUMES:
- <TYPE_1>
- <TYPE_2>

PRODUCES:
- <TYPE_1>
- <TYPE_2>

DEPENDS_ON:
- []  # или: [ENG.NAR.10.THEME_MEANING] (read-only), [ENG.WORLD.10.ENVIRONMENT_ECOLOGY] (optional)

OUTPUT_TARGET:
- <куда складывается результат>

---

## 4) STYLE PARAMETERS (CONTROL SURFACE)

Опиши параметры, которыми можно управлять (пример):
- intensity: low/med/high
- warmth: cold/neutral/warm
- darkness: light/neutral/dark
- tempo-feel: slow/neutral/fast (НЕ screen-time монтаж!)
- texture: clean/gritty/organic/metallic
- symbolism_density: sparse/normal/dense
- sensory_density: sparse/normal/dense

---

## 5) PROCESS (HOW IT WORKS)

1) Read context + constraints
2) Select baseline style profile
3) Apply modifiers for scene/arc
4) Emit style artifact(s) + guardrails (что нельзя)

---

## 6) QUALITY CHECKS

- [ ] Не дублирует narrative/world/production
- [ ] Стиль консистентен с предыдущими артефактами
- [ ] Символы не противоречат уже закреплённым
- [ ] Сенсорика усиливает, а не превращает в “перегруз”
- [ ] Параметры управляемы и повторяемы

---

## 7) FAILURE MODES

- Failure 1 → симптом → как чинить
- Failure 2 → симптом → как чинить

---

## 8) RAW LINK (MANDATORY)

🔗 RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/06_GENRE_STYLE_ENGINES/NN__<ENGINE_NAME>_ENG.md

---

OWNER: Universe Engine
LOCK: OPEN
