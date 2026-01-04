# Relationship Engine
FILE: 06__RELATIONSHIP_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 03_DOMAIN_CHARACTER_ENGINES
LEVEL: L2
STATUS: ACTIVE
VERSION: 1.0
ROLE: Builds relationship graph, power dynamics, trust economy, and relational arcs

---

## PURPOSE

Отношения — отдельный двигатель сюжета.
Этот engine строит:
- граф связей
- динамику власти/зависимости
- экономику доверия
- точки напряжения и разрыва
- арки отношений (сближение/отчуждение)

---

## INPUTS

- Character set
- Character motives/values
- Shared history facts (если есть)
- Scene events affecting ties

---

## OUTPUTS

- Relationship Graph (nodes/edges)
- Edge profile per pair
- Tension map
- Relational arc plan

---

## EDGE PROFILE (CANON)

- REL_TYPE: (ally / family / rivals / lovers / mentor / debt)
- TRUST: 0..100
- POWER BALANCE: (A> B / equal / B> A) + why
- DEPENDENCY: (who needs whom and for what)
- SECRET/LEVERAGE: (что держит)
- CONFLICT VECTOR: (ценности/цели/рана/внешнее давление)
- LOVE/CARE (если релевантно) + how it shows
- BREAK CONDITIONS: что ломает
- REPAIR CONDITIONS: что чинит

---

## PROCEDURE

1) Build graph
2) For each key edge:
   - define trust baseline
   - define power and dependency
   - define conflict vector
3) Place relationship beats:
   - betrayal, test, sacrifice, confession, boundary
4) Update rules:
   - после сцены trust/power must change or confirm

---

## VALIDATION RULES

- R1: Отношения меняются от событий (state delta).
- R2: Доверие нельзя вернуть без цены.
- R3: Власть должна иметь источник (ресурс/страх/любовь/инфо).
- R4: “Лучшие друзья” без тестов — фейк.

---

## FAILURE MODES

- отношения стоят на месте
- конфликт без причин
- доверие скачет без событий

---

## INTEGRATION

- With DIALOGUE_ENG: диалог как поле боя отношений
- With CONTINUITY_ENG: кто что знает и как это влияет
- With DRAMATIC_ARC_ENG: relational peaks/valleys

---
OWNER: Universe Engine
STATUS: FIXED
