# Speech Naturalization Engine
FILE: 08__SPEECH_NATURALIZATION_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 03_DOMAIN_CHARACTER_ENGINES
LEVEL: L2
STATUS: ACTIVE
VERSION: 1.0
ROLE: Makes character speech natural, distinct, context-appropriate, and consistent

---

## PURPOSE

Натурализует речь:
- естественные конструкции
- различимость голосов
- соответствие контексту (стресс/статус/культура)
- устойчивость манеры речи во времени

---

## INPUTS

- Dialogue plan
- Character background (education, region, status)
- Stress level in scene
- Relationship context (power, trust)

---

## OUTPUTS

- Voice Profile (каноника голоса)
- Speech rules (что персонаж делает/не делает)
- Stress modifiers
- Consistency checklist

---

## CANONICAL VOICE PROFILE

- VOCAB RANGE: простой/средний/сложный
- SENTENCE SHAPE: короткие/длинные/обрывки
- RHYTHM: быстрый/ровный/медленный
- HEDGING: “может”, “типа”, “вроде” (есть/нет)
- DIRECTNESS: прямой/косвенный
- EMOTION LEAKS: как “протекают” эмоции
- IDIOMS: 3–10 характерных оборотов
- TABOO WORDS / TOP WORDS
- UNDER STRESS: что меняется

---

## PROCEDURE

1) Build voice profile from background + behavior
2) Apply scene modifiers:
   - stress ↑ → фразы короче, ошибки, повтор
   - power ↑ → меньше объяснений, больше приказов
3) Enforce distinctness:
   - минимум 3 отличия от другого персонажа
4) Run consistency check:
   - не “выпал ли” голос

---

## VALIDATION RULES

- S1: Голоса должны быть различимы без тегов “сказал он”.
- S2: Под стрессом речь меняется предсказуемо.
- S3: Статус влияет на манеру (не обязательно на лексику, но на форму).
- S4: Натуральность > красота.

---

## FAILURE MODES

- “все говорят одинаково”
- слишком литературно в бытовых сценах
- неестественные монологи

---

## INTEGRATION

- With DIALOGUE_ENG: план → текст
- With PSYCHOLOGY_ENG: стресс-реакции → речь
- With CONTINUITY_ENG: знания → что можно сказать

---
OWNER: Universe Engine
STATUS: FIXED
