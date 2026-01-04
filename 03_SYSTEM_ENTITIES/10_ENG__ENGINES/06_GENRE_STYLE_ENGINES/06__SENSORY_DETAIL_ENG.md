# Sensory Detail Engine
FILE: 06__SENSORY_DETAIL_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 06_GENRE_STYLE_ENGINES
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Selects sensory anchors (sound, smell, touch, light) to make scenes vivid and consistent

---

## PURPOSE

Сенсорика — это “доказательство реальности” сцены.
Движок:
- выбирает 2–5 якорей на сцену
- делает их согласованными с тоном/атмосферой
- избегает перегруза
- держит “фирменные” ощущения мира

---

## INPUTS

- Location atmosphere stack
- Tone/mood directive
- Action beats
- World ecology/tech constraints

---

## OUTPUTS

- Sensory anchor list (2–5)
- Priority ordering (что важнее)
- Do/Don’t sensory notes
- Consistency notes (что уже использовали)

---

## SENSORY ANCHOR (CANON)

For each anchor:
- SENSE: sound/smell/touch/temperature/light/taste
- DETAIL: конкретика
- FUNCTION: что делает (угроза/уют/отчуждение)
- PLACEMENT: где в сцене (start/peak/after)
- REPEAT TAG: можно ли повторять

---

## PROCEDURE

1) Choose 1 dominant sense (главный)
2) Choose 1–4 support senses
3) Bind each detail to function (не просто “красиво”)
4) Place anchors across beats:
   - start (вход)
   - peak (усиление)
   - aftermath (послевкусие)
5) Run overload check:
   - если >5 — режем

---

## VALIDATION RULES

- SD1: Сенсорика должна быть конкретной, не “приятный запах”.
- SD2: Каждый якорь должен усиливать тон/атмосферу.
- SD3: Не перегружать — лучше 3 сильных, чем 12 слабых.

---
OWNER: Universe Engine
STATUS: FIXED
