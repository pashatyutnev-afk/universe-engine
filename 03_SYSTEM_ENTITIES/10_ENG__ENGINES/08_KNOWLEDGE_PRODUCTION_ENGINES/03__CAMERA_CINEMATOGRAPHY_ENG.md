# Camera & Cinematography Engine
FILE: 03__CAMERA_CINEMATOGRAPHY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 08_KNOWLEDGE_PRODUCTION_ENGINES
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Plans camera language (lenses, movement, shot grammar, emotional distance)

---

## PURPOSE

Камера — это психология.
Движок задаёт:
- грамматику планов (wide/medium/close)
- линзы (wide/normal/tele)
- движения (static/pan/dolly/handheld)
- “эмоциональную дистанцию” к персонажу

---

## INPUTS

- Scene beats (что меняется)
- Emotional target
- Environment geometry
- Style locks
- Format constraints

---

## OUTPUTS

- Shot list (camera specs)
- Lens & movement presets
- “Camera rules” для проекта

---

## SHOT SPEC (CANON)

For each shot:
- SHOT ID
- PURPOSE (что показывает)
- FRAMING (WS/MS/CU/ECU)
- LENS (wide/normal/tele + feel)
- CAMERA HEIGHT (low/eye/high)
- ANGLE (straight/tilt/dutch)
- MOVEMENT (static/pan/dolly/handheld)
- FOCUS (who/what)
- TRANSITION IN/OUT (cut/match/whip)
- NOTE (emotion)

---

## VALIDATION RULES

- CC1: Камера всегда служит смыслу, не “красоте ради красоты”.
- CC2: Есть повторяемый язык камеры (не хаос).
- CC3: Ритм смены планов согласован с монтажом (см. Editing engine).

---
OWNER: Universe Engine
STATUS: FIXED
