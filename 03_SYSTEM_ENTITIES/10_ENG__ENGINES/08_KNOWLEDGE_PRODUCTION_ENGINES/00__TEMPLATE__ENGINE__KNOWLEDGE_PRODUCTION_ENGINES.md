# ENG KNOWLEDGE PRODUCTION ENGINE — TEMPLATE
FILE: NN__<ENGINE_NAME>_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 08_KNOWLEDGE_PRODUCTION_ENGINES
CLASS: PRODUCTION (L3)
ENGINE_ID: ENG.PROD.NN.<ENGINE_NAME>
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
ROLE: <one-line purpose of this production engine>

---

## 0) PURPOSE (LAW)

Этот движок производит production-артефакт(ы) для медиа:
- превращает входной материал (read-only канон) в план/гайд/спеки
- задаёт воспроизводимые правила исполнения
- выдаёт проверяемый результат для пайплайна

---

## 1) OWNERSHIP (BOUNDARIES)

### OWNS
- <что именно решает движок в рамках production исполнения>

### DOES NOT OWN
- Story laws / narrative decisions (02_DOMAIN_NARRATIVE_ENGINES)
- Event mechanics (05_EXPRESSION_ENGINES)
- Authorial style language (06_GENRE_STYLE_ENGINES)
- Deep music composition/mix/master (09_SOUND_MUSIC_ENGINES)

---

## 2) WHEN TO USE (TRIGGERS)

Используй когда:
- [ ] нужен production-план/гайд/спеки по сценам
- [ ] нужно подготовить промпты/параметры для генерации
- [ ] нужно стандартизировать исполнение (чтобы было повторяемо)
- [ ] надо выпустить asset pack под формат

---

## 3) MINI-CONTRACT (MANDATORY)

CONSUMES:
- <ASSET_REQUIREMENTS>
- <PRODUCTION_CONSTRAINTS>
- <NARRATIVE_MATERIAL (READ-ONLY)>
- <STYLE_PROFILE (READ-ONLY)>

PRODUCES:
- <PLAN/SPEC/GUIDE>
- <ASSET_PACK or PROMPT_SPEC>

DEPENDS_ON:
- []  # допускаются read-only зависимости на narrative/style/format

OUTPUT_TARGET:
- `04_PROJECTS/<project>/01_PRODUCTION/ASSETS/` (или уточни папку: VISUAL/EDIT/AUDIO)

---

## 4) CONTROL SURFACE (PARAMETERS)

Пример параметров (подставь свои):
- output_type: guide | plan | prompt_spec | asset_pack
- quality_level: draft | production | final
- scene_scope: all | selected_scenes | shot_range
- consistency_mode: strict | flexible
- toolchain: (какие инструменты/генераторы используются)
- deliverables: список обязательных выходов

---

## 5) PROCESS (HOW IT WORKS)

1) Read requirements + constraints
2) Pull read-only canon inputs (narrative/style/format)
3) Build production spec/plan
4) Generate prompts / asset checklist
5) Emit outputs + QA checks

---

## 6) QUALITY CHECKS

- [ ] Есть чёткие deliverables (что именно выдаём)
- [ ] Read-only канон не переписан и не искажён
- [ ] Спеки воспроизводимы (не “на глаз”)
- [ ] Совместимо с форматом выпуска
- [ ] Есть критерии готовности (Definition of Done)

---

## 7) FAILURE MODES

- Failure 1 → симптом → как чинить
- Failure 2 → симптом → как чинить

---

## 8) RAW LINK (MANDATORY)

🔗 RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/NN__<ENGINE_NAME>_ENG.md

---

OWNER: Universe Engine
LOCK: OPEN
