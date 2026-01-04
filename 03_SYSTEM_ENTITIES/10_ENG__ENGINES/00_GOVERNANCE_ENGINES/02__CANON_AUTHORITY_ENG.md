# Canon Authority Engine
FILE: 02__CANON_AUTHORITY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines canon authority, decision rights, and what counts as “truth” for the system

---

## MINI-CONTRACT (MANDATORY)
CONSUMES:
- Change proposal (intent + scope + diff)
- Conflict report (contradictions, duplicates, unclear ownership)
- Audit references (existing decision IDs)
- Index/Registry references (what object is affected)

PRODUCES:
- Authority decision (approve/reject/rollback/request-rework)
- Decision class + severity (C0–C4)
- Canon owner assignment (who owns what)
- “Source of truth” resolution rule for conflicts
- Mandatory next steps (Audit + Change Control + Versioning)

DEPENDS_ON:
- 01__AUDIT_LOG_ENG
- 03__RULE_HIERARCHY_ENG
- 04__CHANGE_CONTROL_ENG
- 10__VERSIONING_MEMORY_ENG

OUTPUT_TARGET:
- Governance decisions (recorded as audit entries)
- Rule enforcement in indexes/registries
- Canon ownership map for families/engines

---

## 0) PURPOSE (LAW)
Canon Authority Engine отвечает на 3 вопроса:

1) **Кто** имеет право менять канон?
2) **Что** является истиной, если источники конфликтуют?
3) **Как** принимаются решения и как они фиксируются?

### ABSOLUTE RULE
> Любая каноническая правка без авторитетного решения + Audit Log записи — **non-canon**.

---

## 1) DEFINITIONS (TERMS)
- **Canon**: официальный, обязательный слой истины системы.
- **Non-canon**: существует физически (файл/идея), но не имеет силы.
- **Authority**: право принимать решения о составе, порядке и законах.
- **Owner**: лицо/роль, отвечающее за конкретную область (family/engine).

---

## 2) CANON SOURCES OF TRUTH (ORDER)
Если есть конфликт, побеждает источник выше по иерархии:

1) **INDEX / REGISTRY LAW** (реестры состава и порядка)
2) **RULES** (правила слоя / семейства)
3) **ENGINE CONTRACTS** (mini-contract + boundaries)
4) **README/REALM** (терминология/границы)
5) **Artifacts** (черновики, заметки, идеи)

### CONFLICT RULE
> Если ниже-уровневый текст противоречит выше-уровневому — он считается ошибочным и требует исправления.

---

## 3) AUTHORITY MODEL (WHO DECIDES)
### 3.1 Single Canon Owner (default)
По умолчанию канон имеет одного владельца:
- **OWNER: Universe Engine** (владелец канона)

Его решение = финальное.

### 3.2 Delegated Owners (optional)
Владелец канона может назначить владельцев по областям:

- OWNER (Layer): ENG layer overall
- OWNER (Family): конкретное семейство (например, 02_DOMAIN_NARRATIVE_ENGINES)
- OWNER (Engine): конкретный движок

#### Delegation law
- Делегирование должно быть записано в Audit Log.
- Делегированный owner может менять только свою область и только по pipeline.

---

## 4) DECISION TYPES (MANDATORY)
Каждое решение помечается типом:

- **APPROVE**: изменение принято в канон
- **REJECT**: изменение отклонено (и остаётся non-canon)
- **REQUEST_REWORK**: вернуть на доработку без принятия
- **ROLLBACK**: откат к предыдущему состоянию канона
- **FREEZE**: временно зафиксировать область (LOCK: FIXED) до разбирательства
- **ASSIGN_OWNER**: назначить владельца области/файла

---

## 5) SEVERITY (C0–C4) + REQUIRED PROCESS
- **C0**: косметика (без изменения смысла)
  - Audit: optional (рекомендовано)
  - Version bump: no
- **C1**: небольшое уточнение/добавление без ломания связей
  - Audit: mandatory
  - Version bump: optional
- **C2**: изменение правил/контрактов в одной области
  - Audit: mandatory
  - Versioning: recommended
  - Dependency registry: if dependencies touched
- **C3**: крупная правка, меняет порядок/состав/границы
  - Audit: mandatory
  - Versioning: mandatory
  - Change Control: mandatory
  - Migration notes: mandatory
- **C4**: авария/безопасность/откат/критический конфликт
  - Audit: mandatory (immediate)
  - Freeze allowed
  - Post-mortem entry required

---

## 6) REQUIRED PIPELINE (GOVERNANCE COMPATIBILITY)
Любое каноническое изменение проходит:

1) **Change Control** (proposal → scope → decision)
2) **Canon Authority** (approve/reject)
3) **Audit Log** (immutable record)
4) **Versioning Memory** (если нужна версия/миграция)
5) **Dependency Registry** (если затронуты зависимости)
6) **Index update** (если изменился состав/порядок)

### PIPELINE RULE
> Если любой шаг пропущен — изменение считается non-canon до исправления.

---

## 7) OWNERSHIP RULES (ANTI-CHAOS)
### 7.1 Orphan rule
Если у области нет владельца:
- Владелец = **Universe Engine** по умолчанию.

### 7.2 Ownership conflict rule
Если два владельца конфликтуют:
- решает **Canon Owner** (Layer owner).

### 7.3 Scope boundary rule
Owner не имеет права:
- менять чужие семейства/движки без решения Canon Owner
- нарушать boundaries (анти-дублирование) без C3 решения

---

## 8) CANON CHANGE PERMISSION MATRIX
Кто что может:

### Layer Owner (ENG)
- может менять: любые ENG файлы, правила, индекс, владельцев
- финальная власть в ENG слое

### Family Owner
- может менять: файлы внутри семейства, README family, contracts
- не может: менять глобальный INDEX порядок семейств без Layer Owner

### Engine Owner
- может менять: конкретный движок (текст/контракт/пример)
- не может: менять зависимости и границы без фиксации в dependency registry

---

## 9) EMERGENCY MODE (C4)
Если найден критический косяк (ломает канон/порождает цикл/дублирование):
- допускается **FREEZE** области (LOCK: FIXED)
- делается **ROLLBACK** или **FIX** через Audit
- затем обязательно: post-mortem запись (что сломалось и почему)

---

## 10) REQUIRED OUTPUTS (WHAT MUST APPEAR IN DECISION)
Каждое решение обязано иметь:

- Decision type
- Severity (C0–C4)
- Affected files (canonical paths)
- Required next steps (audit/versioning/dependency/index)
- Owner confirmation (кто отвечает за выполнение)

---

## 11) CANON SIGNATURE RULE
В конце любого принятого изменения (через Audit) должно быть явно понятно:
- кто утвердил
- какая версия/уровень
- где запись в Audit

Минимально — ссылка/ID audit entry.

---

OWNER: Universe Engine  
LOCK: FIXED
