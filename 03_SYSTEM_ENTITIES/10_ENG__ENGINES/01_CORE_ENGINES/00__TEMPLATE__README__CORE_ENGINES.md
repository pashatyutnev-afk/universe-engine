# ENG CORE ENGINES — REALM (FAMILY README)
FILE: 00__README__CORE_ENGINES.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 01_CORE_ENGINES
CLASS: CORE (L1)
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
ROLE: Realm rules + boundaries + interfaces for Core engine family

---

## 0) PURPOSE (REALM LAW)

Эта FAMILY задаёт **базовую идентичность и жизненный цикл системы**.
Core — это “кто мы / где мы / что сейчас происходит / что живо”.

Core отвечает за:
- идентичность системы и её “я”
- состояние системы в текущий момент
- жизненный цикл (создание → активность → деградация → смерть/архив)
- минимальные опорные типы, которые используют все остальные семейства

---

## 1) SCOPE (WHAT THIS FAMILY OWNS)

### THIS FAMILY OWNS
- System identity definition (имя, назначение, границы, ядро “Я”)
- Current state model (что сейчас активно, какие режимы включены)
- Lifecycle rules (инициализация, переходы, завершение, архив)
- Core invariants (что **никогда** нельзя ломать)

### THIS FAMILY DOES NOT OWN
- Governance rules (это `00_GOVERNANCE_ENGINES`)
- Domain content (нарратив/персонажи/мир)
- Production workflows (визуал/монтаж/звук)
- Validators/QA/Controllers (другие entity groups)

---

## 2) CANON ORDER (MANDATORY)

Внутри `01_CORE_ENGINES` порядок строгий:

01 — Core Identity Engine  
02 — Core State Engine  
03 — Core Lifecycle Engine  

---

## 3) INTERFACES (INPUT/OUTPUT TYPES)

### CORE INPUT TYPES (typical)
- IDENTITY_SEED
- SYSTEM_CONTEXT
- STATE_SNAPSHOT
- STATE_CHANGE_REQUEST
- LIFECYCLE_EVENT
- INVARIANT_CHECK_REQUEST

### CORE OUTPUT TYPES (typical)
- CORE_IDENTITY_PROFILE
- CORE_STATE_SNAPSHOT
- STATE_TRANSITION_RECORD
- LIFECYCLE_MAP
- INVARIANTS_LIST

OUTPUT_TARGET (recommended):
- `01_CORE_ENGINES/*` (ядро)
- а также system-level registries (если такие есть в проекте)

---

## 4) CORE INVARIANTS (ABSOLUTE)

Core должен гарантировать:
- единая “точка истины” о текущем состоянии
- понятный жизненный цикл и допустимые переходы
- совместимость с governance pipeline (любой core-change = change-control)

---

## 5) DEPENDENCY RULES

- Core engines могут зависеть только от Governance (если нужен pipeline).
- Domain/Production engines могут зависеть от Core.
- Запрещено: Core зависит от Domain/Production.

---

## 6) REQUIRED LINKS

- INDEX (global): `../02__INDEX_ALL_ENGINES.md`
- Governance pipeline: `../00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md`
- Canon authority: `../00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md`

---

## 7) RULES FOR AUTHORS (MANDATORY)

- Каждый core engine обязан иметь mini-contract.
- Core engine обязан явно перечислить invariants, которые он держит.
- В конце файла — только `LOCK`, без повторного `STATUS`.

---

OWNER: Universe Engine
LOCK: OPEN
