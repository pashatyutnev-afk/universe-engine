# Optimization Engine
FILE: 03__OPTIMIZATION_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 10_META_EVOLUTION_ENGINES
CLASS: META (L4)
LEVEL: L4
STATUS: ACTIVE
VERSION: 1.0
ROLE: Optimizes system performance (clarity, speed, compatibility, reproducibility) via measurable targets; creates optimization backlog, patches, dependency impact notes, and rollback-safe releases

---

## PURPOSE

Оптимизация — это:
- меньше времени на выпуск
- меньше ошибок
- больше ясности
- меньше дрейфа
- больше воспроизводимости

Но **только измеримо** и **совместимо**.

---

## INPUTS

- metrics (time-to-output, error rate, QA fails)
- LER incidents
- pattern cards (PC/APC)
- dependency graphs (00_GOV/06)

---

## OUTPUTS

- OPTIMIZATION BACKLOG ITEM (OBI)
- PATCH SPEC (PSP)
- IMPACT NOTE (IN)
- MIGRATION PLAN (MP) if needed
- ROLLBACK PLAN (RP)
- POST-CHANGE REPORT (PCR)

---

## REQUIRED ARTIFACT: OPTIMIZATION BACKLOG ITEM (OBI)

OBI SCHEMA (CANON):
- OBI_ID:
- TARGET:
  - clarity / speed / compatibility / quality
- METRIC:
  - what we measure
- BASELINE:
- GOAL:
- SCOPE:
  - which families/engines affected
- CHANGE TYPE:
  - refactor / template / index / rule / pipeline
- DEPENDENCY IMPACT (summary):
- RISK:
- ROLLBACK:
- STATUS:
  - proposed / approved / applied / reverted

---

## PROCEDURE

1) Define metric + baseline
2) Create OBI with goal
3) Create patch spec + impact note
4) Governance approval (ME1)
5) Apply patch
6) Validate: did metric improve without breaking compatibility
7) Publish PCR (post-change report)

---

## VALIDATION RULES

- OPT1: No optimization without metric.
- OPT2: No optimization without dependency impact note.
- OPT3: Every change is reversible.
- OPT4: If improvement is not real → revert.

---

OWNER: Universe Engine
STATUS: FIXED
