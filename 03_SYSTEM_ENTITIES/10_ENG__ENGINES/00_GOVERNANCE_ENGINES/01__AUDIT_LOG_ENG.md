# Audit Log Engine
FILE: 01__AUDIT_LOG_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0
ROLE: Canon audit memory — records every canon-relevant action/change as immutable log entries

---

## MINI-CONTRACT (MANDATORY)
CONSUMES:
- Change proposal (text / diff / intent)
- Decision approval result (approve/reject)
- Affected file list (canonical paths)
- Versioning reference (if bump required)

PRODUCES:
- Audit Entry ID (immutable)
- Canon audit record (timestamped)
- Linkable anchor for other docs (Versioning, Index, Dependency)

DEPENDS_ON:
- 02__CANON_AUTHORITY_ENG
- 04__CHANGE_CONTROL_ENG
- 10__VERSIONING_MEMORY_ENG

OUTPUT_TARGET:
- This file (Audit Log Registry)
- Linked from: Versioning Memory, Index updates, Dependency registry

---

## 0) PURPOSE (LAW)
Audit Log — это **не обсуждение**, а **протокол канона**.

Он нужен чтобы:
- фиксировать *когда / кто / что / почему* изменил канон
- давать ссылку-якорь на любую правку (для INDEX / VERSIONING / DEPENDENCY)
- не допускать “серых изменений” без следа

### ABSOLUTE RULE
> Любая каноническая правка без записи в Audit Log считается **non-canon**.

---

## 1) WHAT MUST BE LOGGED (MANDATORY)
Записывается **всегда**:

### 1.1 Canon composition/order changes
- добавление/удаление движков
- смена порядка в INDEX
- создание/удаление family папок
- изменения “законов” (law blocks)

### 1.2 Contract + dependency changes
- mini-contract изменения (CONSUMES/PRODUCES/DEPENDS_ON/OUTPUT_TARGET)
- любые зависимости или xref

### 1.3 Lock / status changes
- LOCK: OPEN → FIXED
- STATUS изменения, влияющие на канон

### 1.4 Governance decisions
- approve / reject / rollback / migration

---

## 2) ENTRY ID STANDARD (MANDATORY)
Формат ID:

`ENG-AUDIT-YYYYMMDD-XXXX`

Где:
- YYYYMMDD — дата
- XXXX — порядковый номер записи за этот день (0001, 0002…)

Пример:
`ENG-AUDIT-20260105-0001`

---

## 3) ENTRY FORMAT (MANDATORY)
Каждая запись строго так:

- ID:
- DATE: YYYY-MM-DD
- TIME: HH:MM (Asia/Almaty)
- ACTOR: (person/system)
- SCOPE: LAYER / FAMILY:<name> / ENGINE:<name>
- TYPE: CREATE / UPDATE / DELETE / REORDER / LOCK / STATUS / DEPENDENCY / FIX
- SEVERITY: C0 / C1 / C2 / C3 / C4
- DECISION: APPROVED / REJECTED / ROLLED_BACK
- VERSION: old → new (or “no bump”)
- SUMMARY: 1–2 строки
- DETAILS: 1–6 строк (что именно)
- WHY: 1 строка (зачем)
- FILES:
  - canonical paths list
- LINKS:
  - Index / Versioning / Dependency references (raw links allowed)

### Severity scale
- C0 — cosmetic, смысл не меняется
- C1 — minor canon add/clarify, совместимость ок
- C2 — medium change, затрагивает правила/контракты частично
- C3 — major change, нужна миграция/перепривязки
- C4 — emergency/rollback/safety critical

---

## 4) IMMUTABILITY LAW
- Запись после публикации **не редактируется**.
- Если ошибка — добавляется новая запись типа `FIX` с ссылкой на ID ошибки.
- Удаление записей запрещено.

---

## 5) CURRENT AUDIT LOG (ENTRIES)

### ENG-AUDIT-20260105-0001
- ID: ENG-AUDIT-20260105-0001
- DATE: 2026-01-05
- TIME: 19:00
- ACTOR: OWNER
- SCOPE: LAYER
- TYPE: UPDATE
- SEVERITY: C1
- DECISION: APPROVED
- VERSION: (init) → ENG@4.0
- SUMMARY: Created/standardized ENG global index as single source of truth
- DETAILS:
  - Added ROOT FILES section (realm + rules + index)
  - Normalized family listing format + raw links
  - Established existence rule for ENG engines
- WHY: Make canon navigable and enforce registry discipline
- FILES:
  - 03_SYSTEM_ENTITIES/10_ENG__ENGINES/02__INDEX_ALL_ENGINES.md
- LINKS:
  - Versioning: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/10__VERSIONING_MEMORY_ENG.md

---

OWNER: Universe Engine  
LOCK: FIXED
