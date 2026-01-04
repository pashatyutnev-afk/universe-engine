# Arrangement & Instrumentation Engine
FILE: 08__ARRANGEMENT_INSTRUMENTATION_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 09_SOUND_MUSIC_ENGINES
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Converts composition into arrangement (roles, layers, instrumentation, density/dynamics, stems plan)

---

## PURPOSE

Аранжировка = “кто что делает” в треке.
Движок фиксирует:
- роли слоёв (drums/bass/harmony/lead/fx)
- плотность и динамику во времени
- инструменты/тембры (в рамках мира)
- стемы для выпуска

---

## INPUTS

- Composition + structure
- Harmony + rhythm + hook
- Sound design language (если уже есть)
- Platform constraints (dialogue-safe, etc)

---

## OUTPUTS

- Arrangement spec
- Instrumentation map
- Density/dynamics map
- Stems list + naming rules

---

## ARRANGEMENT SPEC (CANON)

- ROLE STACK (priority order):
- INSTRUMENTATION (allowed set):
- LAYER POLICY (how many at once):
- DENSITY MAP (low/med/high by sections):
- DYNAMICS MAP (soft->big):
- COUNTERMELODY POLICY:
- TEXTURE TYPES (pad/drone/arp/pulse):
- STEMS LIST + NAMING:
- FORBIDDEN INSTRUMENTS/SOUNDS:

---

## VALIDATION RULES

- AI1: Hook слышен (не утонул).
- AI2: Плотность не мешает сцене/диалогу.
- AI3: Стемы позволяют гибко собрать версии.

---
OWNER: Universe Engine
STATUS: FIXED
