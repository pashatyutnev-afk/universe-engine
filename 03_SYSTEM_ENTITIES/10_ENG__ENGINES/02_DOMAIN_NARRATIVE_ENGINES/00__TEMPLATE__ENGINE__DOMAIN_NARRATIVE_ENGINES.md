# ENG DOMAIN NARRATIVE ENGINE — TEMPLATE
FILE: NN__<ENGINE_NAME>_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
CLASS: DOMAIN (L2)
ENGINE_ID: ENG.NARR.NN.<ENGINE_NAME>
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
ROLE: <one-line purpose of this narrative engine>

---

## 0) PURPOSE (LAW)

Что делает движок:
- какую часть сюжетной машины он строит/фиксирует
- какой артефакт он “главный” производит

---

## 1) OWNERSHIP (BOUNDARIES)

### OWNS
- <что именно принадлежит этому движку>

### DOES NOT OWN
- <что НЕ его (чтобы не было дублей)>

Cross-boundary links (если надо):
- Editing rhythm: `../08_KNOWLEDGE_PRODUCTION_ENGINES/07__EDITING_MONTAGE_ENG.md`
- Characters: `../03_DOMAIN_CHARACTER_ENGINES/`
- World: `../04_DOMAIN_WORLD_ENGINES/`

---

## 2) WHEN TO USE (TRIGGERS)

Используй когда:
- [ ] условие 1
- [ ] условие 2
- [ ] условие 3

Не используй когда:
- [ ] задача относится к монтажу/постпродукции
- [ ] задача — чисто про персонажную психологию без сюжетной функции

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
- []  # или: [ENG.CORE.01.CORE_IDENTITY, ENG.WORLD.02.WORLD_LAW]

OUTPUT_TARGET:
- <куда складывается результат>

---

## 4) PROCESS (HOW IT WORKS)

1) Ingest inputs (seed + constraints)
2) Build structure / logic / plan
3) Validate against constraints (world/core/canon)
4) Emit narrative artifact
5) Provide checklist for downstream engines

---

## 5) QUALITY CHECKS

- [ ] Причинно-следственная связность
- [ ] Нет дыр
- [ ] Нет дублей ownership с соседними движками
- [ ] Continuity не нарушена
- [ ] Тема/смысл поддерживается (если релевантно)

---

## 6) FAILURE MODES

- Failure 1 → симптом → как чинить
- Failure 2 → симптом → как чинить

---

## 7) RAW LINK (MANDATORY)

🔗 RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/NN__<ENGINE_NAME>_ENG.md

---

OWNER: Universe Engine
LOCK: OPEN
