# Melody & Hook Engine
FILE: 04__MELODY_HOOK_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 09_SOUND_MUSIC_ENGINES
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Designs hooks and melodic language (contour, phrasing, repetition rules) for memorability and canon identity

---

## PURPOSE

Hook = узнаваемость.
Движок фиксирует:
- тип hook (melody/rhythm/timbre)
- контур мелодии и фразы
- правила повторов/вариаций
- диапазон, дыхание, паузы

---

## INPUTS

- Composition blueprint
- Harmony palette
- Rhythm palette (если есть)
- Style lock

---

## OUTPUTS

- Hook spec (primary/secondary)
- Melodic rules
- Variation rules
- “Do not” list for melody

---

## HOOK SPEC (CANON)

- HOOK TYPE (melody/rhythm/timbre):
- CORE IDENTIFIER (описание: “вверх на X”, “синкопа”, “тембр”):
- PHRASE LENGTH (bars/seconds):
- REPETITION RULE (how often):
- VARIATION RULES (3 ways: invert/stretch/simplify):
- REGISTER RANGE (low/mid/high):
- ORNAMENT POLICY (none/light/heavy):
- FORBIDDEN (list):

---

## VALIDATION RULES

- MH1: Hook узнаваем минимум в 3 вариантах.
- MH2: Повторы не утомляют (есть вариации).
- MH3: Мелодия не ломает стиль/гармонию.

---
OWNER: Universe Engine
STATUS: FIXED
