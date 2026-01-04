# Creative Mutation Engine
FILE: 04__CREATIVE_MUTATION_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 10_META_EVOLUTION_ENGINES
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Generates novel variants (mutations) of solutions/artifacts while keeping constraints; outputs mutation sets and evaluation plans

---

## PURPOSE

Мутации — это controlled chaos, чтобы находить прорывы.
Движок:
- генерирует новые варианты решений (неочевидные)
- сохраняет ограничения (канон/стиль/ресурсы)
- делает “набор мутаций” и план проверки
- отделяет эксперименты от канона

---

## INPUTS

- Current baseline (что есть)
- Constraints (must keep)
- Forbidden list (must avoid)
- Target improvements (what to boost)
- Risk tolerance (how wild allowed)

---

## OUTPUTS

- Mutation set (variants)
- Mutation rationale (why each might work)
- Evaluation plan (how to test)
- Safe-to-try shortlist
- “Do not canonize before test” stamp

---

## MUTATION SET (CANON)

Global:
- BASELINE ID
- TARGET IMPROVEMENT
- MUTATION BUDGET (how many + how wild)
- CONSTRAINTS (must keep)
- FORBIDDEN (must avoid)

Per mutation:
- MUTATION ID
- MUTATION TYPE (structure/style/process/tooling)
- DESCRIPTION (what changes)
- WHY IT MAY WORK
- RISK LEVEL (low/med/high)
- TEST METHOD
- STOP CONDITION (when to abandon)

---

## PROCEDURE

1) Define baseline + constraints
2) Choose mutation budget and risk tolerance
3) Generate variant set across mutation types
4) Tag risks and test methods
5) Shortlist safe-to-try
6) Run tests and feed back to Learning engine

---

## VALIDATION RULES

- CM1: Мутации не нарушают must-keep constraints.
- CM2: У каждой мутации есть гипотеза (почему может сработать).
- CM3: Тест-план обязателен.
- CM4: До проверки мутации не становятся “каноном”.

---
OWNER: Universe Engine
STATUS: FIXED
