# Pattern Extraction Engine
FILE: 02__PATTERN_EXTRACTION_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 10_META_EVOLUTION_ENGINES
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Extracts recurring patterns from logs, artifacts, decisions, and outcomes to identify leverage points and failure modes

---

## PURPOSE

Паттерны — это повторяемые закономерности, на которых можно строить систему.
Движок:
- находит повторяющиеся причины успеха/провалов
- выявляет “точки рычага” (что даёт максимум эффекта)
- строит библиотеку паттернов и анти-паттернов
- создаёт триггеры раннего обнаружения ошибок

---

## INPUTS

- Learning records
- Runs / artifacts history
- Metrics and outcomes
- Decisions and constraints history

---

## OUTPUTS

- Pattern library (patterns + anti-patterns)
- Leverage map (high-impact moves)
- Early warning triggers
- Hypotheses for optimization engine

---

## PATTERN CARD (CANON)

- PATTERN ID
- TYPE (success/failure/neutral)
- DESCRIPTION (what repeats)
- CONDITIONS (when it appears)
- SIGNALS (how to detect)
- IMPACT (low/med/high)
- ROOT CAUSE HYPOTHESIS
- RECOMMENDED RESPONSE (what to do)
- COUNTER-CASES (when not true)
- CONFIDENCE (low/med/high)

---

## PROCEDURE

1) Aggregate data by similar contexts
2) Cluster repeated outcomes
3) Identify conditions that correlate strongly
4) Write pattern cards + signals
5) Propose triggers and responses
6) Validate patterns with spot checks (false positives)

---

## VALIDATION RULES

- PE1: Паттерн имеет детектируемые сигналы.
- PE2: Есть условия появления (не абстракция).
- PE3: Есть практическая реакция (что делать).
- PE4: Указаны контр-кейсы (чтобы не переобобщать).

---
OWNER: Universe Engine
STATUS: FIXED
