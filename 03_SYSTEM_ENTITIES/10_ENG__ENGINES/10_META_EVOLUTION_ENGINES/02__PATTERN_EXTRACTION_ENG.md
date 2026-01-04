# Pattern Extraction Engine
FILE: 02__PATTERN_EXTRACTION_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 10_META_EVOLUTION_ENGINES
CLASS: META (L4)
LEVEL: L4
STATUS: ACTIVE
VERSION: 1.0
ROLE: Extracts reusable patterns from projects/engines/QA incidents; converts them into named pattern cards, standards, and templates with applicability rules and anti-pattern warnings

---

## PURPOSE

Доставать повторяемое:
- успешные схемы
- типичные ошибки
- универсальные структуры

И превращать это в “карточки паттернов”, которые можно применять снова.

---

## INPUTS

- LER (Learning records)
- successful outputs (canon artifacts)
- QA drift reports
- repeated questions/confusions

---

## OUTPUTS

- PATTERN CARD (PC)
- ANTI-PATTERN CARD (APC)
- TEMPLATE UPDATE PROPOSAL (TUP)
- STANDARD UPDATE NOTE (SUN)

---

## REQUIRED ARTIFACT: PATTERN CARD (PC)

PC SCHEMA (CANON):
- PC_ID:
- NAME:
- CATEGORY:
  - narrative / character / world / production / governance / meta
- PROBLEM:
- CONTEXT:
  - where it applies
- SOLUTION (steps):
- INPUTS REQUIRED:
- OUTPUTS PRODUCED:
- CHECKS:
  - what must be true
- EXAMPLES (links):
- DO NOT USE WHEN:
- VERSION:
- STATUS:
  - draft / canon / deprecated

Rule:
- Pattern is not a vibe — it’s a repeatable procedure.

---

## REQUIRED ARTIFACT: ANTI-PATTERN CARD (APC)

APC SCHEMA (CANON):
- APC_ID:
- NAME:
- SYMPTOMS:
- WHY IT HAPPENS:
- DAMAGE:
- FIX:
- PREVENTION RULE:
- STATUS:

Rule:
- Anti-patterns save больше времени, чем новые идеи.

---

## PROCEDURE

1) Select dataset (LER + good outputs)
2) Find repeats (same symptom or same success)
3) Name the pattern
4) Write PC/APC with applicability boundaries
5) Propose template/standard updates (TUP/SUN)
6) Governance approval
7) Publish pattern into standards/templates

---

## VALIDATION RULES

- PE1: Pattern has boundaries (where it applies / where it doesn’t).
- PE2: Pattern is actionable steps, not philosophy.
- PE3: Pattern has checks and anti-pattern warnings.
- PE4: Pattern improves reproducibility or clarity measurably.

---

OWNER: Universe Engine
STATUS: FIXED
