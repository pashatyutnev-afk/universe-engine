# Technology & Magic Engine
FILE: 08__TECHNOLOGY_MAGIC_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 04_DOMAIN_WORLD_ENGINES
LEVEL: L2
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines capability system (tech/magic), limits, costs, access control, and exploit-proofing

---

## PURPOSE

Фиксирует систему возможностей:
- что умеет тех/магия
- границы и стоимость
- доступ (кто может)
- риски и побочные эффекты
- защита от эксплойтов

---

## INPUTS

- World laws (особенно cost)
- Civilization profiles
- Resource model
- Narrative needs (какие “чудеса” нужны)

---

## OUTPUTS

- Capability Catalog
- Rule set (limits, costs)
- Access control model
- Failure modes (backfire)
- Exploit list + prevention rules

---

## CAPABILITY ENTRY (CANON)

- CAP_ID / NAME
- TYPE: tech / magic / hybrid
- WHAT IT DOES (операционно)
- LIMITS (что не может)
- COST (ресурс/время/риск/психика/соц цена)
- ACCESS (кто и почему)
- COUNTERS (чем остановить)
- SIDE EFFECTS

---

## PROCEDURE

1) Define 10–30 capabilities (по нужде)
2) For each:
   - limits + cost + counters
3) Define access control:
   - education, lineage, license, infrastructure, belief initiation
4) Define failure/backfire patterns
5) Define exploit prevention:
   - запреты на “бесконечные циклы”, “вечную энергию”, “всё лечит”

---

## VALIDATION RULES

- TM1: Любая способность имеет counter.
- TM2: Цена соразмерна силе.
- TM3: Доступ ограничен (иначе мир ломается).
- TM4: Способности не должны убивать конфликт (иначе плохой дизайн).

---

## FAILURE MODES

- “всем доступно всё”
- бессмертие/воскрешение без цены
- магия решает любую проблему

---

## INTEGRATION

- With WORLD_LAW_ENG: законы и стоимость
- With ECONOMY_RESOURCE_ENG: топливо возможностей
- With QA/VAL: проверка эксплойтов

---
OWNER: Universe Engine
STATUS: FIXED
