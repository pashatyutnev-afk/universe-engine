# DECISION APPROVAL ENGINE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/07__DECISION_APPROVAL_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
LAYER: 03_SYSTEM_ENTITIES
FAMILY: 00_GOVERNANCE_ENGINES
DOC_TYPE: ENGINE
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0.0
UID: <UE.ENG.GOV.DECISION_APPROVAL.001>
OWNER: SYSTEM
ROLE: Canonical decision-making + approval rules (who can approve what, required quorum, veto, emergency path)
LOCK: FIXED

---

## 0) PURPOSE (LAW)

Этот движок — **про принятие решений** в системе.

Он определяет:
- какие решения вообще бывают (Decision Types)
- кто имеет право апрува (Roles / Authority)
- какой нужен минимум согласований (Quorum)
- можно ли вето и кем (Veto)
- как оформлять решение в виде артефакта (Decision Record)
- как работает emergency path (когда нужно быстро)

Главный смысл:
> Любая правка канона, которая требует решения, не считается принятой,
> пока не существует Decision Record по стандарту этого движка.

---

## 1) BOUNDARY (ANTI-DUPLICATION)

Owned here:
- типы решений и их строгость
- правила апрува/кворума/вето/эскалации
- формат Decision Record
- правила “без решения — не канон”

Not owned here:
- аудит всех событий (Audit Log Engine)
- управление изменениями и пакетами (Change Control Engine)
- определение того, что является каноном (Canon Authority Engine)
- проверка согласованности ссылок/реестров (Consistency Engine)

---

## 2) MINI-CONTRACT (MANDATORY)

CONSUMES:
- <ARTIFACT: CHANGE_PACKAGE>                 # пакет изменений (если есть)
- <ARTIFACT: CANON_CHANGE_REQUEST>           # запрос на изменение канона (если отдельно)
- <ARTIFACT: CONFLICT_REPORT?>               # отчёт о конфликтах/рисках (optional)
- <ARTIFACT: PROPOSED_DECISION>              # предложение решения (text)

PRODUCES:
- <ARTIFACT: DECISION_RECORD>                # каноническая запись решения
- <ARTIFACT: APPROVAL_STATUS>                # APPROVED/REJECTED/NEEDS_REVIEW
- <ARTIFACT: WAIVER_RECORD?>                 # исключение (если разрешено)
- <ARTIFACT: ESCALATION_NOTE?>               # эскалация (если тупик)

DEPENDS_ON:
- [00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG]   # что считается каноном
- [00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG]    # как изменения упаковываются
- [00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG]         # все решения должны логироваться

OUTPUT_TARGET:
- `99_LOGS/LOG__AUDIT.md` (log ref)
- `99_LOGS/LOG__CHANGES.md` (optional)
- `03_SYSTEM_ENTITIES/00_REG__REGISTRIES/REG__DECISIONS.md` (recommended registry, if used)

---

## 3) DECISION TYPES (STRICT SET)

Allowed DECISION_TYPE:

### D0 — Trivial / Editorial
- опечатки, форматирование, чистка не-смысловых вещей
- не меняет правила, структуру, индексы, статусы, UID-логику

### D1 — Canon Patch
- правка существующего файла без изменения архитектуры
- обновление текста, уточнение формулировок
- не меняет порядок реестров/индексов и не вводит новые сущности

### D2 — Canon Structural Change
- изменение индекса/реестра (добавить/удалить/перенумеровать)
- переезды/переименования, которые меняют навигацию
- изменение правил стандартов, которые затрагивают другие слои

### D3 — Law Change
- изменение SYSTEM LAW
- изменение порядка authority / existence rule
- любые правки, которые влияют на “как работает система”

### D4 — Emergency Decision
- срочное исключение для восстановления целостности
- допускает временную “дыру”, но обязано иметь план закрытия

Rule:
- Если сомневаешься — выбирай более строгий тип (выше номер).

---

## 4) ROLES + AUTHORITY (MINIMUM MODEL)

Минимальные роли (v1):

- ROLE: SYSTEM_OWNER
  - финальное слово по D3/D4
- ROLE: GOVERNANCE_OWNER
  - ведёт пайплайн, может апрувить D2
- ROLE: STANDARDS_OWNER
  - апрувит изменения стандартов/шаблонов
- ROLE: MAINTAINER
  - может апрувить D0/D1 в пределах зоны ответственности

Rule:
- роль может быть “виртуальной” (владелец системы один), но в Decision Record она всё равно указывается.

---

## 5) APPROVAL RULES (STRICT)

### 5.1 Required approvals by type
- D0: 1 approval (MAINTAINER)
- D1: 1 approval (MAINTAINER) + audit record
- D2: 2 approvals minimum (GOVERNANCE_OWNER + STANDARDS_OWNER OR SYSTEM_OWNER)
- D3: SYSTEM_OWNER required (cannot be delegated)
- D4: SYSTEM_OWNER required + must include MIGRATION_PLAN + EXPIRY_DATE

### 5.2 Veto
- VETO allowed only for:
  - SYSTEM_OWNER (always)
  - GOVERNANCE_OWNER (only D2 and below)

### 5.3 Quorum
- если апрувов меньше минимума — статус НЕ APPROVED
- “молчание = согласие” запрещено

---

## 6) DECISION RECORD FORMAT (MANDATORY)

Decision Record — это минимальный артефакт, который должен существовать.

### 6.1 Minimal format (required)
- DECISION_ID: <UE.DEC.YYYY-MM-DD.NNN>
- DATE: YYYY-MM-DD
- DECISION_TYPE: D0|D1|D2|D3|D4
- SCOPE: <short scope>  # e.g. "ENG / Governance"
- SUBJECT: <what is being decided>
- CONTEXT: <why it exists>
- OPTIONS: [A, B, C]     # short
- DECISION: <chosen option>
- IMPACT: <what changes>
- APPROVERS:
  - <ROLE>: <name/handle>
- STATUS: APPROVED|REJECTED|NEEDS_REVIEW
- LINKS:
  - CHANGE_PACKAGE: <ref or path or "none">
  - AFFECTED_FILES: [<paths>]
- NOTES: <optional>

### 6.2 Emergency required fields
If DECISION_TYPE = D4:
- EXPIRY_DATE: YYYY-MM-DD
- MIGRATION_PLAN: <how we revert/normalize>
- RISK_ACCEPTANCE: <what risk accepted>

Rule:
- Если D4 без EXPIRY_DATE/MIGRATION_PLAN — решение невалидно.

---

## 7) ENFORCEMENT RULES (HARD)

- R1: Canon structural changes require Decision Record  
  Любые изменения индексов/реестров/переименований (D2+) → Decision Record обязателен.

- R2: No decision — no canon  
  Если изменения в репо произошли, но решения нет → считается “unapproved state” до исправления.

- R3: Decision must be auditable  
  Любой Decision Record обязан иметь запись в Audit Log (ссылкой/ID).

- R4: Conflicts must cite Rule Hierarchy  
  Если решение связано с конфликтом правил → в CONTEXT указать, какой закон/иерархия применялась.

---

## 8) WORKFLOW (HOW IT RUNS)

### 8.1 Standard flow
1) Change Control собирает пакет
2) Canon Authority определяет: нужен ли апрув и какого типа
3) Decision Approval создаёт Decision Record
4) Audit Log фиксирует событие
5) Consistency проверяет, что решение и изменения согласованы

### 8.2 Deadlock / escalation
Если нет согласия:
- STATUS = NEEDS_REVIEW
- создаётся ESCALATION_NOTE (optional)
- финальная точка: SYSTEM_OWNER

---

## 9) OUTPUT EXAMPLES

### 9.1 D2 example (index reorder)
- DECISION_TYPE: D2
- SUBJECT: "Reorder ENG families + rename templates"
- APPROVERS: GOVERNANCE_OWNER + SYSTEM_OWNER
- AFFECTED_FILES: [03_SYSTEM_ENTITIES/10_ENG__ENGINES/02__INDEX_ALL_ENGINES.md, ...]

### 9.2 D4 example (emergency)
- DECISION_TYPE: D4
- SUBJECT: "Temporary allow missing UID in 3 files to unblock merge"
- EXPIRY_DATE: set
- MIGRATION_PLAN: "Backfill UID + run consistency audit"

---

## 10) REL / XREF (UID-FIRST)

REL:
- REL: SUPPORTS | TARGET_UID: <UE.ENG.GOV.CHANGE_CONTROL.001> | WHY: approvals bind to change packages
- REL: SUPPORTS | TARGET_UID: <UE.ENG.GOV.CANON_AUTHORITY.001> | WHY: canon status needs decision
- REL: REQUIRES | TARGET_UID: <UE.ENG.GOV.AUDIT_LOG.001> | WHY: decisions must be logged

--- END.
