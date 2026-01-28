# CORE STATE ENGINE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/02__CORE_STATE_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 01_CORE_ENGINES
CLASS: CORE (L1)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ENG.CORE.STATE.001
OWNER: SYSTEM
ROLE: Defines canonical system state model and produces deterministic state snapshots + drift reports (OK/WARN/BLOCK) for safe canon work.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Core state standardized: state model, snapshot schema, drift taxonomy, severity gates, and audit hooks."
- REASON: "Stop silent drift after renames/deletes and prevent working on broken canon."
- IMPACT: "System becomes observable: you always know if canon is healthy before editing."
- CHANGE_ID: UE.CHG.2026-01-08.CORE.STATE.001

---

## 0) PURPOSE (LAW)

Core State Engine определяет **состояние системы сейчас** (не история) и делает его проверяемым.

Он:
- задаёт **SYS_STATE_MODEL** (что считается состоянием)
- выпускает **SYS_STATE_SNAPSHOT** (слепок “как есть сейчас”)
- выпускает **SYS_STATE_DRIFT_REPORT** (что расходится и насколько критично)

Система может развиваться безопасно только если состояние не BLOCK.

---

## 1) NON-GOALS (HARD)

Этот движок НЕ:
- не определяет идентичность (это `01__CORE_IDENTITY_ENG`)
- не определяет жизненный цикл объектов (это `03__CORE_LIFECYCLE_ENG`)
- не принимает governance-решения (это governance engines)
- не валидирует качество текста/фактов (это VAL/QA)
- не заменяет индексы: он только проверяет их согласованность и факт существования

---

## 2) MINI-CONTRACT (MANDATORY)

CONSUMES:
- SYS_IDENTITY (identity contract + signature keys baseline)
- CANON_INDEX_SET (list of canonical indexes/registries that define existence)
- REPO_TREE_SNAPSHOT (observed structure / paths)
- OPTIONAL_DB_MIRRORS (assistive registries if used; never authority)

PRODUCES:
- SYS_STATE_MODEL (SYSTEM_SPEC)
- SYS_STATE_SNAPSHOT (SYSTEM_SNAPSHOT)
- SYS_STATE_DRIFT_REPORT (SYSTEM_REPORT)
- STATE_RECORD (LOG_RECORD, audit-compatible)

DEPENDS_ON:
- 01_CORE_ENGINES/01__CORE_IDENTITY_ENG
- 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG
- 00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG
- 00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG
- 00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG (on dispute)

OUTPUT_TARGET:
MANDATORY:
- 00_INDEX/00__ROOT_INDEX.md (section: SYSTEM_STATE)
- 99_LOGS/LOG__AUDIT.md (STATE_RECORD + drift summary)

OPTIONAL:
- 08_DATABASES/DB__RELEASE_LOG.md (snapshot pointer / compatibility tag)
- 99_LOGS/LOG__CHANGES.md (if drift caused by change packages)

---

## 3) DEFINITIONS

- **System State** — наблюдаемое текущее каноническое положение системы, определяемое индексами и критическими артефактами.
- **Snapshot** — единый слепок состояния по фиксированной схеме.
- **Drift** — расхождение между каноном (indexes/laws/required structure) и наблюдаемым состоянием.
- **Severity** — OK | WARN | BLOCK (см. раздел 7).

---

## 4) STATE MODEL (CANONICAL)

### 4.1 State facets (minimum)
SYS_STATE_MODEL обязан покрывать:

STATE.CANON:
- CANON_ROOT
- existence-by-index baseline

STATE.STRUCTURE:
- layer base paths (exist + not mixed)

STATE.INDEXES:
- canonical indexes resolved and reachable

STATE.REGISTRIES:
- optional DB mirrors (if used)

STATE.ENTITIES:
- active system entity groups (ENG/ORC/SPC/CTL/VAL/QA/XREF)

STATE.KB/PRJ/AST:
- governance entrypoints existence (not their contents)

STATE.LOGS:
- audit log reachable (for traceability)

### 4.2 Source of truth
- Источник истины о существовании: **канонические индексы**.
- DB mirrors / списки / заметки — только assistive.

---

## 5) INPUTS (STRICT)

### Required
- SYS_IDENTITY: baseline invariants (single root, raw-only, existence-by-index)
- CANON_INDEX_SET: список индексов, управляющих существованием
- REPO_TREE_SNAPSHOT: факт структуры

### Optional
- OPTIONAL_DB_MIRRORS: только как справочник/ускоритель

### Forbidden
- “посторонние индексы”, не зарегистрированные каноном
- любые списки “в чатах” как источник существования

---

## 6) OUTPUT SCHEMAS (MINIMUM FORMS)

### 6.1 SYS_STATE_SNAPSHOT (SYSTEM_SNAPSHOT)
MUST:
- TIMESTAMP
- CANON_ROOT
- SEVERITY: OK|WARN|BLOCK
- ACTIVE_LAYERS: [list]
- CANON_INDEX_SET: [list]
- CRITICAL_ARTIFACTS: (status summary)
- DRIFT_COUNT: N
- BLOCKERS: [list] (if any)

### 6.2 SYS_STATE_DRIFT_REPORT (SYSTEM_REPORT)
MUST:
- TIMESTAMP
- SEVERITY
- DRIFTS: [records]
- FIX_ACTIONS: [ordered list]
- ESCALATION: NONE | CONSISTENCY | CANON_AUTHORITY

### 6.3 STATE_RECORD (LOG_RECORD, audit-compatible)
MUST:
- DATE
- SNAPSHOT_REF (path/anchor)
- SEVERITY
- DRIFT_SUMMARY
- NOTES (optional)

---

## 7) DRIFT TAXONOMY (STANDARD)

D1 (BLOCK) — Broken canon index reference  
Индекс ссылается на несуществующий файл.

D2 (WARN) — Orphan file detected  
Файл существует на диске, но не зарегистрирован в каноническом индексе.
(Это не ломает канон, но создаёт мусор/риск путаницы.)

D3 (BLOCK) — Duplicate canon entrypoint claim  
Два документа в одном scope заявляют “единственную точку истины”.

D4 (BLOCK) — Illegal STATUS/LOCK values  
STATUS/LOCK не из allowed set.

D5 (WARN→BLOCK) — Registry/DB mirror divergence  
DB mirror расходится с каноном.
BLOCK если mirror используется как зависимость пайплайна (нельзя).

D6 (BLOCK) — Layer role mixing  
Документ закона/стандарта/индекса находится в неправильном слое или пытается менять роль слоя.

---

## 8) SEVERITY RULES (OK/WARN/BLOCK)

OK:
- D1..D6 отсутствуют, критические индексы резолвятся

WARN:
- только WARN-дрифты (D2, D5-soft) и нет блокеров

BLOCK:
- любой BLOCK-дрифт присутствует (D1/D3/D4/D6 или D5-hard)

Rule:
- При BLOCK любые канон-изменения запрещены до фикса.
- При WARN изменения допустимы, но drift должен быть отмечен в audit.

---

## 9) PIPELINE (DETERMINISTIC)

### Step 1 — Resolve identity baseline
- подтвердить CANON_ROOT и invariants (из Identity Engine)

### Step 2 — Resolve canonical indexes
- пройти CANON_INDEX_SET и проверить существование целей
- выявить D1, D3

### Step 3 — Check metadata legality
- STATUS/LOCK allowed set
- single-truth metadata (no duplicates)
- выявить D4

### Step 4 — Structure sanity
- слои на местах, роли не смешаны
- выявить D6

### Step 5 — Optional mirror checks
- если DB mirrors включены — сверить как assistive
- выявить D5

### Step 6 — Emit snapshot + drift report
- присвоить severity
- сформировать FIX_ACTIONS

### Step 7 — Record in audit
- STATE_RECORD в LOG__AUDIT
- если BLOCK: escalation to Consistency (или Canon Authority при споре)

---

## 10) S0 BLOCKERS (STOP CONDITIONS)

S0-1: индекс ссылается на несуществующий файл (D1)
S0-2: два “single source of truth” в одном scope (D3)
S0-3: illegal STATUS/LOCK (D4)
S0-4: смешаны роли слоёв (D6)
S0-5: работа по канону продолжается при BLOCK (policy breach)

---

## 11) FIX ACTIONS (STANDARD PLAYBOOK)

Если D1:
- исправить ссылки в каноническом индексе (путь/raw)
- если файл переехал: зафиксировать migration mapping (memory)

Если D2:
- либо зарегистрировать в индексе (если нужен)
- либо удалить как non-canon мусор

Если D3:
- определить canonical authority документ
- второй документ перевести в pointer/alias или удалить
- зафиксировать решение

Если D4:
- привести STATUS/LOCK к allowed set
- удалить дубли метаданных (шапка = единственная истина)

Если D6:
- вернуть документ в правильный слой/роль
- обновить индексы и зафиксировать change package

---

## 12) EXAMPLES (MINIMUM)

Example A (OK):
- все индексы резолвятся
- DRIFTS: []
- SEVERITY: OK

Example B (BLOCK):
- индекс ссылается на удалённый файл
- DRIFTS: [D1]
- SEVERITY: BLOCK
- FIX_ACTIONS: update index + migration mapping + audit entry

---

## 13) REFERENCES (RAW ONLY)

CORE:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/01__CORE_IDENTITY_ENG.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/03__CORE_LIFECYCLE_ENG.md

ROOT:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/00_INDEX/00__ROOT_INDEX.md

GOVERNANCE:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md

STANDARDS / LAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/04__CANON_PROTOCOL.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md

--- END.
