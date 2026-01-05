# ENG PRODUCTION FORMAT ENGINE — TEMPLATE
FILE: NN__<ENGINE_NAME>_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 07_PRODUCTION_FORMAT_ENGINES
CLASS: PRODUCTION (L3)
ENGINE_ID: ENG.FORMAT.NN.<ENGINE_NAME>
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
ROLE: <one-line purpose of this format engine>

---

## 0) PURPOSE (LAW)

Этот движок определяет/адаптирует формат выпуска:
- какие правила упаковки материала применяются
- какие артефакты должен выдать формат
- какие ограничения формат накладывает на story/style/production

---

## 1) OWNERSHIP (BOUNDARIES)

### OWNS
- <что именно решает движок в рамках формата>

### DOES NOT OWN
- Story structure laws (02_DOMAIN_NARRATIVE_ENGINES)
- Event mechanics (05_EXPRESSION_ENGINES)
- Style language (06_GENRE_STYLE_ENGINES)
- Production execution (08_KNOWLEDGE_PRODUCTION_ENGINES)
- Deep music (09_SOUND_MUSIC_ENGINES)

---

## 2) WHEN TO USE (TRIGGERS)

Используй когда:
- [ ] нужно выбрать формат выпуска проекта
- [ ] нужно адаптировать историю под другой формат
- [ ] нужен “скелет артефактов” под платформу
- [ ] нужно зафиксировать требования к длительности/объёму/структуре выпуска

---

## 3) MINI-CONTRACT (MANDATORY)

CONSUMES:
- <PROJECT_INTENT>
- <AUDIENCE_TARGET>
- <NARRATIVE_MATERIAL>

PRODUCES:
- <FORMAT_SPEC>
- <BLUEPRINT/STRUCTURE_DOC>

DEPENDS_ON:
- []  # допускаются read-only зависимости на narrative/style

OUTPUT_TARGET:
- `04_PROJECTS/<project>/01_PRODUCTION/FORMAT/`

---

## 4) FORMAT PARAMETERS (CONTROL SURFACE)

Пример параметров (подставь свои):
- platform: book / series / short / youtube / game
- duration_or_volume: pages | minutes | episodes_count
- structure: chapters | episodes | beats | loops
- density: low/med/high (плотность событий/информации)
- hook_requirement: none/soft/hard (для short/youtube)
- continuity_mode: serial/episodic/hybrid
- output_bundle: какие документы обязаны быть выданы

---

## 5) PROCESS (HOW IT WORKS)

1) Read intent + platform + constraints
2) Choose format baseline (canonical)
3) Adapt narrative material into format container
4) Emit FORMAT_SPEC + blueprint(s)
5) Emit risks/impacts for governance

---

## 6) QUALITY CHECKS

- [ ] Формат соответствует цели и платформе
- [ ] Артефакты формата полные (FORMAT_SPEC + blueprint)
- [ ] Нет конфликта с каноном narrative
- [ ] Явно описаны ограничения и компромиссы
- [ ] Указаны downstream последствия для production

---

## 7) FAILURE MODES

- Failure 1 → симптом → как чинить
- Failure 2 → симптом → как чинить

---

## 8) RAW LINK (MANDATORY)

🔗 RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/07_PRODUCTION_FORMAT_ENGINES/NN__<ENGINE_NAME>_ENG.md

---

OWNER: Universe Engine
LOCK: OPEN
