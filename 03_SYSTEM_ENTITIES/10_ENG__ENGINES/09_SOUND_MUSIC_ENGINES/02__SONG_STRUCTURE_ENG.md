# Song Structure Engine
FILE: 02__SONG_STRUCTURE_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 09_SOUND_MUSIC_ENGINES
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines structure grammar (sections, transitions, payoff timing) for songs/cues

---

## PURPOSE

Структура = “скелет трека”.
Движок фиксирует:
- секции (intro/verse/chorus/bridge/outro)
- длительности и переходы
- где payoff (самый сильный момент)
- где разрядка и дыхание

---

## INPUTS

- Composition blueprint + tension map
- Platform format (short/long/cinematic)
- Hook plan
- Lyrics presence (yes/no)

---

## OUTPUTS

- Section map
- Transition rules
- Payoff placement rules
- Version templates (short cut / full)

---

## SECTION MAP (CANON)

- STRUCTURE TYPE (song/cue/montage/trailer):
- TOTAL LENGTH:
- SECTIONS:
  - S1 NAME / LENGTH / PURPOSE / ENERGY (0–10)
  - S2 ...
- HOOK APPEARANCES (timecodes):
- PAYOFF MOMENT (timecode + why):
- DROP/RESET MOMENT (timecode):
- TRANSITIONS (cut/riser/breakdown/match):
- OUTRO POLICY (hard stop/fade/tag):

---

## STRUCTURE TEMPLATES (DEFAULT)

- POP: Intro → Verse → Chorus → Verse → Chorus → Bridge → Chorus → Outro
- TRAILER: Intro → Build → Hit 1 → Build 2 → Hit 2 → Tail
- CUE (scene): Setup → Turn → Climax → Release

---

## VALIDATION RULES

- SS1: Payoff расположен осознанно (не случайно).
- SS2: Переходы не ломают читаемость hook.
- SS3: Длина секций поддерживает tension map.

---
OWNER: Universe Engine
STATUS: FIXED
