# Rhyme & Meter Engine
FILE: 06__RHYME_METER_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 09_SOUND_MUSIC_ENGINES
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines the system for rhyme schemes, meter, stress patterns, and flow constraints (lyrics-ready, platform-agnostic)

---

## PURPOSE

Это “математика текста”.
Движок фиксирует:
- схему рифмовки
- размер/метр и ударения
- плотность слогов
- правила флоу (читка/пение)

---

## INPUTS

- Language target
- Style lock (жанр текста)
- BPM/meter (из Rhythm engine)
- Vocal constraints (range, articulation)
- Emotional target

---

## OUTPUTS

- Rhyme scheme spec
- Meter spec (stress map)
- Flow constraints
- “Do not” list for lyrics rhythm

---

## RHYME & METER SPEC (CANON)

- SCHEME (AABB/ABAB/AAAA/mixed):
- RHYME TYPE (full/slant/internal/multis):
- LINE LENGTH (syllables range):
- STRESS MAP (where stresses fall):
- FLOW DENSITY (low/med/high):
- PAUSE POLICY (caesura/breath points):
- ENDINGS POLICY (open/closed):
- FORBIDDEN (overcomplexity, forced rhymes, etc):

---

## VALIDATION RULES

- RM1: Текст ложится в ритм без ломки дикции.
- RM2: Рифмы не выглядят “натянутыми”.
- RM3: Метрика поддерживает эмоцию (не механика ради механики).

---
OWNER: Universe Engine
STATUS: FIXED
