# ENG DOMAIN CHARACTER ENGINE — TEMPLATE
FILE: NN__<ENGINE_NAME>_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 03_DOMAIN_CHARACTER_ENGINES
CLASS: DOMAIN (L2)
ENGINE_ID: ENG.CHAR.NN.<ENGINE_NAME>
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
ROLE: <one-line purpose of this character engine>

---

## 0) PURPOSE (LAW)

Что делает движок:
- какую часть персонажной модели он строит/фиксирует
- какой главный артефакт он производит

---

## 1) OWNERSHIP (BOUNDARIES)

### OWNS
- <что именно принадлежит этому движку>

### DOES NOT OWN
- Сюжетные арки/структуры сцен (см. `../02_DOMAIN_NARRATIVE_ENGINES/`)
- Мир/законы/экономика (см. `../04_DOMAIN_WORLD_ENGINES/`)
- Монтаж/постпродакшн (см. `../08_KNOWLEDGE_PRODUCTION_ENGINES/`)

---

## 2) WHEN TO USE (TRIGGERS)

Используй когда:
- [ ] нужно определить/уточнить персонажа как сущность
- [ ] нужно согласовать мотивации/поведение/отношения
- [ ] нужно удержать голос персонажа в диалоге
- [ ] нужно описать рост/травму/эволюцию

Не используй когда:
- [ ] задача про монтажный тайминг или ритм
- [ ] задача чисто про законы мира без влияния на персонажа

---

## 3) MINI-CONTRACT (MANDATORY)

CONSUMES:
- <TYPE_1>
- <TYPE_2>
- <TYPE_3>

PRODUCES:
- <TYPE_1>
- <TYPE_2>
- <TYPE_3>

DEPENDS_ON:
- []  # или: [ENG.CORE.01.CORE_IDENTITY, ENG.WORLD.02.WORLD_LAW, ENG.NARR.02.STORY_STRUCTURE]

OUTPUT_TARGET:
- <куда складывается результат>

---

## 4) PROCESS (HOW IT WORKS)

1) Ingest seed + constraints
2) Build character model / map / guide
3) Validate against canon + world constraints
4) Emit character artifact
5) Provide checklist for downstream engines (dialogue/narrative)

---

## 5) QUALITY CHECKS

- [ ] Персонаж непротиворечив
- [ ] Мотивации реально ведут к действиям
- [ ] Нет дублей ownership с Narrative/World
- [ ] Голос/речь узнаваемы и стабильны (если релевантно)
- [ ] Эволюция объяснена (если релевантно)

---

## 6) FAILURE MODES

- Failure 1 → симптом → как чинить
- Failure 2 → симптом → как чинить

---

## 7) RAW LINK (MANDATORY)

🔗 RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/NN__<ENGINE_NAME>_ENG.md

---

OWNER: Universe Engine
LOCK: OPEN
