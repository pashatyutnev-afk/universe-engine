# Civilization Engine
FILE: 04__CIVILIZATION_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 04_DOMAIN_WORLD_ENGINES
LEVEL: L2
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines civilizations as survival machines: values, institutions, tech, culture, and vulnerabilities

---

## PURPOSE

Моделирует цивилизации как **машины выживания**:
- ценности и миф
- институты (кто решает)
- экономика/ресурсы (если есть)
- технология/магия
- социальные правила
- слабости и точки распада

---

## INPUTS

- World laws and structure
- Timeline epochs
- Key conflicts
- Environment constraints

---

## OUTPUTS

- Civilization Profiles
- Institutional map
- Vulnerability list
- Inter-civ relations hooks

---

## CANONICAL CIV PROFILE

- NAME / ID
- CORE MYTH (во что верят о себе)
- CORE VALUE (что свято)
- GOVERNANCE (как принимают решения)
- POWER BASE (на чём держится сила)
- ECON/RESOURCE BASE (если применимо)
- TECH/MAGIC LEVEL + signature
- SOCIAL ORDER (классы/касты/сети)
- TABOOS + CRIMES
- VULNERABILITIES (3–6)
- EXPANSION LOGIC (зачем растут)
- COLLAPSE LOGIC (как падают)

---

## PROCEDURE

1) Define myth + value
2) Define institutions and power base
3) Define constraints from environment
4) Define vulnerabilities and collapse mode
5) Define external relations hooks:
   - trade, war, ideology, migration

---

## VALIDATION RULES

- C1: У цивилизации должен быть источник силы и цена этой силы.
- C2: Институты должны объяснять решения, а не “король захотел”.
- C3: Уязвимости обязаны быть эксплуатируемы конфликтом.
- C4: Цивилизация должна меняться от эпох.

---

## FAILURE MODES

- цивилизация как “одна идея”
- нет институтов → нет логики решений
- нет слабостей → нереалистично

---

## INTEGRATION

- With GEOPOLITICS_ENG: карты влияния
- With MYTHOLOGY_BELIEF_ENG: миф как операционная сила
- With CONFLICT_POWER_ENG: войны, революции, экспансия

---
OWNER: Universe Engine
STATUS: FIXED
