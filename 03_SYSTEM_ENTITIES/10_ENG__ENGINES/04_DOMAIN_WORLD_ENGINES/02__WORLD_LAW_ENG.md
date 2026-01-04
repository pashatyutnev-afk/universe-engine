# World Law Engine
FILE: 02__WORLD_LAW_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 04_DOMAIN_WORLD_ENGINES
LEVEL: L2
STATUS: ACTIVE
VERSION: 1.0
ROLE: Establishes laws, constraints, invariants, and cost mechanics (physics/social/magic/tech)

---

## PURPOSE

Фиксирует **законы мира**:
- что всегда истинно (invariants)
- что невозможно
- что возможно, но с ценой
- как работает “сила” (тех/магия/вера/власть)

---

## INPUTS

- Genre realism level
- Core premise
- Tech/magic assumptions
- Desired conflict types

---

## OUTPUTS

- World Laws List (10–30 пунктов)
- Cost System (таблица “получить → заплатить”)
- Exception rules (редко и строго)
- Exploit prevention notes (как не сломать мир)

---

## CANONICAL WORLD LAW ENTRY

- LAW_ID
- STATEMENT: кратко
- DOMAIN: (physics / society / magic / tech / belief)
- SCOPE: local / global / layer-specific
- COST: цена (если применимо)
- ENFORCEMENT: кто/что обеспечивает
- EXCEPTIONS: есть ли, и цена

---

## PROCEDURE

1) Define invariants (ядро)
2) Define constraints (запреты)
3) Define cost mechanics for powers
4) Define enforcement (почему закон держится)
5) Define exceptions (минимум)
6) Add “anti-cheat” notes (что ломает канон)

---

## VALIDATION RULES

- WL1: Любая сила должна иметь цену.
- WL2: Исключения не могут быть “по желанию автора”.
- WL3: Законы должны быть тестируемы сценами.
- WL4: Enforcement обязан существовать (иначе закон фикция).

---

## FAILURE MODES

- магия/тех как чит
- “законы” без применения
- исключения ради удобства

---

## INTEGRATION

- With TECHNOLOGY_MAGIC_ENG: конкретизация сил
- With MYTHOLOGY_BELIEF_ENG: вера как закон/механизм
- With QA/VAL: проверка нарушений

---
OWNER: Universe Engine
STATUS: FIXED
