# ENG EXPRESSION ENGINE — TEMPLATE
FILE: NN__<ENGINE_NAME>_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 05_EXPRESSION_ENGINES
CLASS: EXPRESSION (L3)
ENGINE_ID: ENG.EXPR.NN.<ENGINE_NAME>
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
ROLE: <one-line purpose of this expression engine>

---

## 0) PURPOSE (LAW)

Что делает движок:
- какую механику событий он строит
- какие правила вводит (и какие границы)
- какой артефакт выдаёт

---

## 1) OWNERSHIP (BOUNDARIES)

### OWNS
- <что именно этот движок делает в механике событий>

### DOES NOT OWN
- Theme/Meaning (см. Narrative)
- Story-time pacing (см. Narrative)
- Characters психология/мотивация/речь (см. Character family)
- World laws/экономика/технологии (см. World family)
- Screen-time editing rhythm (см. Production family)

---

## 2) WHEN TO USE (TRIGGERS)

Используй когда:
- [ ] нужно породить события или уточнить что “является событием”
- [ ] нужно связать события причинностью
- [ ] нужно собрать конфликт как механизм
- [ ] нужно поставить поворотные точки
- [ ] нужно определить кульминацию и/или развязку
- [ ] нужно ввести системный шок
- [ ] нужно расписать порядок и тайминг событий
- [ ] нужно ввести контролируемый хаос/случайность

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
- []  # или: [ENG.NAR.01.NARRATIVE_LOGIC, ENG.WORLD.02.WORLD_LAW]

OUTPUT_TARGET:
- <куда складывается результат>

---

## 4) PROCESS (HOW IT WORKS)

1) Ingest seed + constraints + current states
2) Generate / refine event candidates
3) Build causal links / conflict dynamics
4) Mark turning points / climax / resolution hooks
5) Emit artifact(s) + constraints for downstream (scenes/pacing)

---

## 5) QUALITY CHECKS

- [ ] Причинность непротиворечива
- [ ] События меняют состояние (не “пустые”)
- [ ] Конфликт определён через силы/интересы/ставки
- [ ] Turning points реально меняют траекторию
- [ ] Climax/Resolution закрывают петли, а не создают мусор
- [ ] Randomness ограничен и объяснён

---

## 6) FAILURE MODES

- Failure 1 → симптом → как чинить
- Failure 2 → симптом → как чинить

---

## 7) RAW LINK (MANDATORY)

🔗 RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/05_EXPRESSION_ENGINES/NN__<ENGINE_NAME>_ENG.md

---

OWNER: Universe Engine
LOCK: OPEN
