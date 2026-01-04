# Music To Scene Engine
FILE: 12__MUSIC_TO_SCENE_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 09_SOUND_MUSIC_ENGINES
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Maps music to narrative/scene beats (hit points, tension map sync, cue design, transitions) and outputs a reproducible cue sheet

---

## PURPOSE

Музыка к сцене = “точность попаданий”.
Движок:
- строит tension map сцены
- назначает hit points (повороты, раскрытия, удары)
- описывает cue по секундам/тактом
- задаёт правила входа/выхода музыки

---

## INPUTS

- Scene beats + timing (если есть)
- Editing rhythm (cut points)
- Emotional target + arc
- Style locks

---

## OUTPUTS

- Cue sheet (timeline)
- Hit points list
- Entry/exit rules
- Dialogue-safe rules (if dialogue)

---

## CUE SHEET (CANON)

- SCENE ID / NAME
- PURPOSE (what music does)
- DURATION (sec)
- TEMPO / METER (or free)
- TENSION MAP (0–10 over time)
- HIT POINTS:
  - TIME
  - EVENT
  - MUSICAL ACTION (hit/drop/modulation/stop)
- THEMES USED (motifs)
- ENTRY RULE (how it starts)
- EXIT RULE (how it ends)
- DIALOGUE POLICY (if present)

---

## PROCEDURE

1) Extract beats and timing
2) Build tension map
3) Define hit points and what they trigger
4) Choose themes/motifs (if applicable)
5) Plan entry/exit and transitions
6) Validate against edit rhythm and clarity

---

## VALIDATION RULES

- MTS1: Музыка попадает в ключевые повороты.
- MTS2: Она не спорит с монтажом (ритм совместим).
- MTS3: Диалог/смысл не маскируется.
- MTS4: Cue sheet воспроизводим (другой человек сделает по нему).

---
OWNER: Universe Engine
STATUS: FIXED
