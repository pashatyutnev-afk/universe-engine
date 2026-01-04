# Music Style Consistency Engine
FILE: 11__MUSIC_STYLE_CONSISTENCY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 09_SOUND_MUSIC_ENGINES
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Creates style locks and QA gates to keep multiple tracks coherent (palette, harmony, groove, mix signature, do/don't)

---

## PURPOSE

Консистентность = “все треки одной вселенной”.
Движок:
- фиксирует style locks (тембры/гармония/ритм/микс)
- создаёт do/don’t
- определяет QA тесты на узнаваемость
- задаёт “границы инноваций” (как можно экспериментировать)

---

## INPUTS

- Project references + genre target
- Previous canon tracks (if any)
- Harmony/rhythm/arrangement specs
- Platform needs

---

## OUTPUTS

- Style lock bible
- Do/Don’t list
- Allowed variation space
- QA checklist + acceptance gates

---

## STYLE LOCK BIBLE (CANON)

- TEMPO RANGE
- HARMONY MODE + VOCABULARY
- GROOVE ARCHETYPES (approved list)
- INSTRUMENT PALETTE (approved families)
- SIGNATURE FX (limited list)
- MIX SIGNATURE (space, width, dynamics feel)
- VOCAL STYLE (if any)
- FORBIDDEN ELEMENTS
- ALLOWED EXPERIMENTS (boundaries)

---

## QA GATES

- 3-TRACK TEST: три трека подряд звучат как один проект?
- HOOK READABILITY: hook слышен на тихой громкости?
- PALETTE CONSISTENCY: тембры не “другой жанр”?
- MIX SIGNATURE: пространство и динамика похожи?

---

## VALIDATION RULES

- MSC1: Новая работа проходит 3-track test.
- MSC2: Любое отклонение помечено как intentional + причина.
- MSC3: Запреты не нарушены.

---
OWNER: Universe Engine
STATUS: FIXED
