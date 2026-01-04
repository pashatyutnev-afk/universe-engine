# Video Generation Engine
FILE: 06__VIDEO_GENERATION_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 08_KNOWLEDGE_PRODUCTION_ENGINES
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Creates reproducible video generation specs (shots, motion, continuity, audio sync hooks)

---

## PURPOSE

Видео — это движение + непрерывность.
Движок фиксирует:
- список шотов
- параметры движения
- continuity constraints
- требования к переходам
- точки синхры со звуком

---

## INPUTS

- Shot list (camera engine)
- Style + lighting locks
- Duration targets
- Platform constraints (fps, codec if needed)

---

## OUTPUTS

- Video generation spec
- Shot-by-shot prompts (если генерация)
- Continuity rules
- Motion constraints

---

## VIDEO SPEC (CANON)

Global:
- DURATION
- FPS TARGET
- ASPECT
- STYLE LOCKS
- CONTINUITY LOCKS (герой/одежда/предметы/погода)
- MOTION FEEL (smooth/handheld/etc)

Per shot:
- SHOT ID
- LENGTH
- CAMERA MOVEMENT
- SUBJECT MOTION
- BACKGROUND MOTION
- TRANSITION OUT
- SYNC MARKERS (beat points)

---

## VALIDATION RULES

- VG1: Continuity фиксируется (иначе видео “плывёт”).
- VG2: Движение мотивировано сценой.
- VG3: Переходы поддерживают монтажный ритм.

---
OWNER: Universe Engine
STATUS: FIXED
