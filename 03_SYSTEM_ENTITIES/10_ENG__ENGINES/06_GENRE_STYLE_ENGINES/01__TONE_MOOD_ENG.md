# Tone & Mood Engine
FILE: 01__TONE_MOOD_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 06_GENRE_STYLE_ENGINES
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines tone and mood as controllable parameters for narration and scene perception

---

## PURPOSE

Разводит 2 штуки, которые постоянно путают:

- **TONE** = позиция/голос рассказчика (ирония, холод, нежность, сарказм)
- **MOOD** = эмоциональная погода сцены (тревога, уют, ужас, эйфория)

Этот движок задаёт:
- допустимый диапазон
- точки смены
- запреты на “тональные прыжки”

---

## INPUTS

- Scene/event spec
- Character lens (кто наблюдает)
- Stakes level
- Genre intent

---

## OUTPUTS

- Tone profile (primary + secondary)
- Mood profile (primary + intensity)
- Transition policy (как меняется)
- Anti-contradiction constraints

---

## TONE/MOOD PROFILE (CANON)

- TONE_PRIMARY (1)
- TONE_SECONDARY (0–2)
- MOOD_PRIMARY (1)
- MOOD_INTENSITY (0–10)
- DRIFT (slow/step/flip forbidden)
- TRANSITION TRIGGERS (что меняет настроение)
- DO / DON’T (what language/imagery allowed)

---

## PROCEDURE

1) Identify POV / lens
2) Select tone that matches lens + theme
3) Select mood that matches stakes + environment
4) Set intensity and drift rules
5) Define transition triggers:
   - reveal
   - loss
   - safety
   - proximity to threat
6) Add “tonal guardrails” (что запрещено)

---

## VALIDATION RULES

- TM1: Tone should not undermine stakes unless intended (irony as tool).
- TM2: Mood intensity must track danger/hope realistically.
- TM3: Transitions need triggers (no random mood swings).
- TM4: Tone and mood must not conflict (e.g., comedic tone inside horror peak unless designed as contrast).

---
OWNER: Universe Engine
STATUS: FIXED
