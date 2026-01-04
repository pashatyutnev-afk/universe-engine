# CORE ENGINES — Realm
FILE: 00__README__CORE_ENGINES.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 01_CORE_ENGINES
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0
ROLE: Realm file for CORE engines (foundation contracts for all entities)

---

## WHAT THIS FAMILY IS

**CORE ENGINES** — это фундаментальные контракты системы.
Они описывают **базовые свойства любой сущности**: кто она (Identity), в каком состоянии она находится (State), и как она живёт во времени (Lifecycle).

Если CORE сломан или не определён — весь остальной слой (ENG/ORC/SPC/CTL/VAL/QA/Projects) становится хаосом.

---

## WHY IT EXISTS

CORE нужен чтобы:
- у каждой сущности был **единый паспорт** (ID/TYPE/PATH/VERSION/OWNER)
- у каждой сущности было **единое состояние** (draft/active/deprecated и т.д.)
- у каждой сущности был **единый жизненный цикл** (создание → утверждение → поддержка → миграция → архив)

---

## FAMILY CONTENTS

### 01 — Core Identity Engine
Определяет: что такое “сущность” в системе и как выглядит её канонический паспорт.

### 02 — Core State Engine
Определяет: допустимые состояния, переходы и правила обновления статуса.

### 03 — Core Lifecycle Engine
Определяет: жизненный цикл сущностей как процесс с гейтами, проверками и миграциями.

---

## REQUIRED INVARIANTS (CORE LAW)

- C0: У любой сущности есть Identity.
- C1: У любой сущности есть State.
- C2: Любая эволюция State происходит через Lifecycle.
- C3: Любые массовые изменения должны быть трассируемы (Audit) и управляемы (Change Control).

---

## HOW OTHER SYSTEMS USE CORE

- ENG Engines: обязаны описывать свои inputs/outputs и ссылаться на Identity/State.
- ORC Orchestrators: строят пайплайны, используя state gates.
- CTL Controllers: блокируют изменения, которые нарушают core contracts.
- VAL Validators: валидируют Identity/State/Transitions.
- QA Quality: проверяет качество документа и соответствие стандартам.
- Projects: используют CORE как основу для сущностей персонажей/локаций/событий и т.д.

---

## CHANGE POLICY

CORE считается защищённой зоной:
- любые изменения форматов CORE требуют Decision Approval (если меняется контракт)
- любые изменения должны сопровождаться migration notes
- обратная совместимость предпочтительна, либо обязателен XREF mapping

---
OWNER: Universe Engine
STATUS: FIXED
