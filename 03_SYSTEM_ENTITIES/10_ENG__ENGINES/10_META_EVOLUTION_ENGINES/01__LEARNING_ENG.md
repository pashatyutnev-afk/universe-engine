# Learning Engine
FILE: 01__LEARNING_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 10_META_EVOLUTION_ENGINES
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Converts experience (runs, feedback, outcomes) into retained rules, playbooks, and reusable knowledge

---

## PURPOSE

Обучение — это превращение опыта в капитал.
Движок делает:
- сбор сигналов (что случилось)
- оценку результата (хорошо/плохо и почему)
- извлечение уроков
- запись в канонические “правила/плейбуки”
- отсев шумов и ложных выводов

---

## INPUTS

- Run logs (что делали)
- Outcome (результат)
- Feedback (человек/метрики)
- Context (условия)
- Constraints (ресурсы/сроки)

---

## OUTPUTS

- Learned rules (heuristics)
- Updated playbooks
- “Do/Don’t” updates
- Confidence score per lesson
- Open questions list (что не ясно)

---

## LEARNING RECORD (CANON)

- LEARNING ID
- SOURCE (which runs / events)
- CONTEXT SUMMARY
- SIGNALS (what observed)
- OUTCOME (what happened)
- LESSON (one sentence)
- ACTIONABLE RULE (what to do next time)
- SCOPE (where it applies)
- CONFIDENCE (low/med/high + why)
- COUNTER-EXAMPLES (when it fails)
- NEXT TEST (how to validate)

---

## PROCEDURE

1) Collect signals & outcome
2) Separate correlation vs causation assumptions
3) Write lesson as testable rule
4) Add counter-examples and scope
5) Assign confidence
6) Schedule next validation test

---

## VALIDATION RULES

- L1: Урок формулируется как правило, которое можно применить.
- L2: Есть область применимости (scope) и ограничения.
- L3: Есть план проверки (иначе это “мнение”).
- L4: Урок не дублирует старые — либо усиливает, либо заменяет.

---
OWNER: Universe Engine
STATUS: FIXED
