# CORE ENGINES — Realm
FILE: 00__README__CORE_ENGINES.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 01_CORE_ENGINES
CLASS: CORE (L1)
LEVEL: L1
STATUS: ACTIVE
VERSION: 2.0
ROLE: Realm file for CORE engines that define system identity, state, and lifecycle; provides shared terms, boundaries, and contract expectations for all downstream families

---

## WHAT THIS FAMILY IS

**CORE_ENGINES** — это фундамент ENG слоя.
Это не “про сюжет” и не “про продакшн”.
Это про то, **что такое система**, в каком она состоянии и как она живёт во времени.

CORE задаёт:
- идентичность (кто мы / какая вселенная / какие цели)
- состояние (что сейчас активно, что зафиксировано, что в разработке)
- жизненный цикл (как рождается/меняется/фиксируется канон)

---

## WHY IT EXISTS

Без CORE:
- невозможно понять “к какой версии канона относится документ”
- разные части системы начинают жить в разных реальностях
- не ясны статусы, владельцы, границы и режимы работы

CORE — это “паспорт + состояние + история жизни” для ENG.

---

## FAMILY BOUNDARY (IMPORTANT)

CORE НЕ делает:
- Governance процесс (это 00_GOVERNANCE_ENGINES)
- Домены (нарратив/персонажи/мир)
- Продакшн/медиа

CORE делает:
- определения идентичности/состояния/жизненного цикла как **данные**
- стандарты “что считается активным” и “как жить в статусах”

---

## FAMILY-WIDE CANON TERMS

### SYSTEM IDENTITY
Набор полей, которые определяют “что это за система”:
- имя/код системы
- миссия
- scope
- принципы
- источники истины (index, governance)

### SYSTEM STATE
Текущее состояние системы:
- текущая версия
- активные семейства
- активные правила/locks
- открытые waivers/risks
- текущая стадия разработки

### LIFECYCLE
Жизненный цикл канона:
- draft → active → fixed → deprecated → archived
(точные статусы — внутри Core Lifecycle Engine)

---

## CORE OUTPUTS (WHAT DOWNSTREAM EXPECTS)

Downstream семейства ожидают от CORE:
- стабильный identity profile (чтобы ссылки и терминология не “плавали”)
- понятный system state (что сейчас актуально)
- понятный lifecycle (как правильно вводить/фиксировать/выводить элементы)

---

## REQUIRED FIELDS POLICY (MINIMAL CORE CONTRACT)

Любая сущность ENG (семейство/движок) должна иметь:
- SCOPE
- ENTITY_GROUP
- FAMILY
- CLASS (если применимо)
- LEVEL
- STATUS
- VERSION
- ROLE
- OWNER
- LOCK (если зафиксировано)

CORE задаёт значение этих полей как “правильный стандарт”.

---

## FAMILY CONTENTS

01 — Core Identity Engine  
02 — Core State Engine  
03 — Core Lifecycle Engine  

---

## FAMILY-WIDE VALIDATION

- C1: Identity поля не противоречат INDEX и governance.
- C2: State описывает актуальную версию и активные статусы.
- C3: Lifecycle определяет, как сущности переходят между статусами без хаоса.

---

OWNER: Universe Engine
LOCK: FIXED
