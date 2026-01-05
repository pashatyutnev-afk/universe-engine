# ENG DOMAIN WORLD ENGINE — TEMPLATE
FILE: NN__<ENGINE_NAME>_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 04_DOMAIN_WORLD_ENGINES
CLASS: DOMAIN (L2)
ENGINE_ID: ENG.WORLD.NN.<ENGINE_NAME>
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
ROLE: <one-line purpose of this world engine>

---

## 0) PURPOSE (LAW)

Что делает движок:
- какую часть мира он строит/фиксирует
- какие ограничения/возможности вводит
- какой итоговый артефакт выдаёт

---

## 1) OWNERSHIP (BOUNDARIES)

### OWNS
- <что именно принадлежит этому движку>

### DOES NOT OWN
- Сцены/арки/ритм истории (см. `../02_DOMAIN_NARRATIVE_ENGINES/`)
- Мотивации/психология/диалоги (см. `../03_DOMAIN_CHARACTER_ENGINES/`)
- Продакшн/арт/монтаж/генерация (см. `../08_KNOWLEDGE_PRODUCTION_ENGINES/`)

---

## 2) WHEN TO USE (TRIGGERS)

Используй когда:
- [ ] нужно определить границы мира / что возможно
- [ ] нужно зафиксировать правила (законы) и их цену
- [ ] нужно построить эпохи/историю мира
- [ ] нужно спроектировать цивилизацию/власть/экономику/тех-стек
- [ ] нужно объяснить верования/мифы и влияние на общество
- [ ] нужно учесть экологию/риски/устойчивость

Не используй когда:
- [ ] задача про драматургическое напряжение без изменения мировых правил
- [ ] задача про голос персонажа или сценическое действие

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
- []  # или: [ENG.CORE.01.CORE_IDENTITY, ENG.GOV.04.CHANGE_CONTROL]

OUTPUT_TARGET:
- <куда складывается результат>

---

## 4) PROCESS (HOW IT WORKS)

1) Ingest seed + canon facts + constraints
2) Build / refine world model segment
3) Define rules + boundaries + costs
4) Validate against canon + other world subsystems
5) Emit world artifact + notes for downstream (narrative/character)

---

## 5) QUALITY CHECKS

- [ ] Правила мира не противоречат сами себе
- [ ] У каждого правила есть цена/ограничения/последствия
- [ ] Нет дублей ownership с Narrative/Character
- [ ] Выходной артефакт пригоден как “constraint input” для других движков
- [ ] Изменения канона готовы к фиксации через governance

---

## 6) FAILURE MODES

- Failure 1 → симптом → как чинить
- Failure 2 → симптом → как чинить

---

## 7) RAW LINK (MANDATORY)

🔗 RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/NN__<ENGINE_NAME>_ENG.md

---

OWNER: Universe Engine
LOCK: OPEN
