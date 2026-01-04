# Dependency Registry Engine
FILE: 06__DEPENDENCY_REGISTRY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: ACTIVE
VERSION: 2.0
ROLE: Canonical dependency + handoff law for all ENG engines; defines allowed link types, required mini-contract fields, and produces reproducible dependency graph artifacts

---

## PURPOSE

Этот движок вводит “закон связей” для ENG:
- чтобы все зависимые цепочки были **явными**
- чтобы outputs одного движка были корректным input для другого
- чтобы не было скрытых пересечений ролей
- чтобы INDEX был дорожной картой не только по списку, но и по **интеграции**

---

## SCOPE (WHAT IT CONTROLS)

Dependency Registry контролирует:
- типы связей между движками (link types)
- формат записи зависимости (edge schema)
- требования к mini-contract (CONSUMES/PRODUCES/DEPENDS_ON/OUTPUT_TARGET)
- требования к HANDOFF блоку
- политику циклов (cycle policy)
- формат артефакта dependency graph (DEP_GRAPH)

---

## NON-GOALS (WHAT IT DOES NOT DO)

- не утверждает канон (Canon Authority)
- не управляет изменениями (Change Control)
- не оценивает качество текста (Consistency Engine)
- не заменяет доменную логику (Narrative/World/Character)

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- engine mini-contract blocks from all families
- handoff blocks from all engines
- change packets that modify dependencies
- index references (for canonical addressing)

### PRODUCES
- DEP_GRAPH artifact (canonical dependency graph snapshot)
- DEP_EDGES registry entries (edge list)
- CYCLE REPORT (if cycles exist)
- REQUIRED FIXES list when contract mismatch found

### DEPENDS_ON
- 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md
- 00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md
- 00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md
- 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md

### OUTPUT_TARGET
- System-wide governance: used before LOCKing any change set
- Attached to Consistency Report and referenced in Audit Log

---

## CANON ADDRESSING (ENGINE IDENTIFIERS)

Любая ссылка на движок в системе должна быть в одном формате:

- ENGINE_ID: `ENG::<FAMILY>::<NN>::<ENGINE_NAME>`
  - example: `ENG::00_GOVERNANCE_ENGINES::06::DEPENDENCY_REGISTRY`

- CANON_PATH: `03_SYSTEM_ENTITIES/10_ENG__ENGINES/<FAMILY>/<FILE>`

В тексте допускается сокращение:
- `00/06` означает `00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG.md`

---

## REQUIRED FIELDS IN EVERY ENGINE (LAW)

Каждый ENG движок обязан содержать:

### 1) MINI-CONTRACT (MANDATORY)
- CONSUMES
- PRODUCES
- DEPENDS_ON
- OUTPUT_TARGET

### 2) HANDOFF (MANDATORY WHEN APPLICABLE)
Если движок PRODUCES артефакт, который кто-то CONSUMES —
должен быть описан HANDOFF.

Если движок не отдаёт ничего downstream — HANDOFF допускается пустым,
но mini-contract всё равно обязателен.

---

## LINK TYPES (CANON)

### A) DEPENDS_ON (HARD)
Жёсткая зависимость. Без upstream артефакта этот движок не может работать.
- strictness: HARD
- implies: consumer must cite upstream in handoff mapping

### B) FEEDS_INTO (SOFT)
Выход движка используется downstream, но без него downstream может работать “в режиме деградации”.
- strictness: SOFT

### C) HANDOFF_TO (SOFT/HARD)
Явная передача артефакта (файла/спека/карты) в downstream.
- strictness: can be HARD or SOFT (declared per edge)

### D) OVERLAP_RISK (SOFT)
Риск пересечения ролей. Требует boundary clarification.
- always SOFT but treated as CRITICAL by Consistency unless resolved

### E) CONFLICTS_WITH (HARD)
Правила противоречат. Требуется решение через governance.
- strictness: HARD
- triggers: Change Control + Canon Authority

### F) SUBSUMES (HARD)
Один движок является “надстройкой”, включающей другой как подмодуль.
- used rarely; requires explicit approval

---

## DEPENDENCY EDGE SCHEMA (CANON)

Каждая связь между движками описывается так:

- EDGE_ID: DE-0001
- FROM: <ENGINE_ID>
- TO: <ENGINE_ID>
- TYPE: DEPENDS_ON | FEEDS_INTO | HANDOFF_TO | OVERLAP_RISK | CONFLICTS_WITH | SUBSUMES
- STRICTNESS: HARD | SOFT
- ARTIFACT: what is handed off (name)
- ARTIFACT_FORMAT: spec/card/graph/checklist/template/etc
- MAPPING: "FROM.PRODUCES -> TO.CONSUMES" one line
- RATIONALE: one sentence
- NOTES: optional

---

## HANDOFF BLOCK STANDARD (CANON)

В каждом движке, если есть downstream usage, вставляется:

### HANDOFF (MANDATORY)
- PRODUCED_ARTIFACTS:
  - <artifact_name> — <short description> — <format>
- CONSUMERS:
  - <engine_id or family/nn> — consumes: <artifact_name> — strictness
- DELIVERY:
  - where stored (path or project folder standard)
- ACCEPTANCE:
  - how consumer validates artifact

---

## CANON ARTIFACT: DEP_GRAPH (SYSTEM SNAPSHOT)

Dependency Registry обязан уметь отдавать “снимок графа” (текстом):

### DEP_GRAPH (CANON FORMAT)
- GRAPH_ID: DG-ENG-0001
- DATE:
- SCOPE:
  - full ENG | families list | change packet scope
- NODE_COUNT:
- EDGE_COUNT:
- EDGES:
  - list of DEP_EDGES (edge schema above)
- CYCLES:
  - none | list (see cycle report)
- NOTES:
  - major risks / required fixes

Этот артефакт прикладывается к:
- Consistency Report
- Change Control packet (если правка меняет связи)

---

## CYCLE POLICY (DEFAULT FORBIDDEN)

### Default rule
Циклы запрещены.

### Allowed cycles (rare)
Разрешены только если:
- цикл описан как **governance mediated**
- есть явный “разрыв” через gate:
  - approve/review/lock/audit
- указан “источник истины” (single source of truth)
- Canon Authority это разрешила

### Cycle report format
- CYCLE_ID: CY-0001
- NODES: list
- WHY_EXISTS:
- BREAK_MECHANISM:
- RISK:
- APPROVAL:

---

## CONTRACT MISMATCH RULES (AUTOMATIC FAIL CONDITIONS)

Если обнаружено:
- TO engine CONSUMES artifact, которого не PRODUCES upstream
- FROM engine PRODUCES artifact, но нет downstream consumer (если заявлено как mandatory)
- DEPENDS_ON отсутствует, но handoff явно обязателен

→ это минимум S1 (critical), иногда S0 (blocker), и должно быть исправлено.

---

## CORE SYSTEM INTEGRATION (EXPECTED LINKS)

Чтобы ENG работал как конвейер, минимальные связи должны существовать:

### Governance backbone (always)
- All engines — DEPENDS_ON → 00/04 Change Control (process)
- All engines — FEEDS_INTO → 00/05 Consistency (audits)
- All engine families — FEEDS_INTO → 00/01 Audit Log (record)
- INDEX — HANDOFF_TO → Consistency + Dependency Registry (registry scans)

### Domain → Expression (logic flow)
- 02 Domain Narrative — FEEDS_INTO → 05 Expression
  - Narrative Logic → Cause-Effect / Event

### Domain → Production (artifact flow)
- Domain outputs — FEEDS_INTO → 07 Production Format (adaptation)
- 07 Production Format — FEEDS_INTO → 08 Knowledge Production (media specs)
- 08 Knowledge Production — HANDOFF_TO → 09 Sound/Music (deep) when needed

(Это не означает “все на всех”, но означает: связи должны быть описаны там, где реально используется.)

---

## PROCEDURE (HOW TO USE THIS ENGINE)

1) Для каждого движка заполнить mini-contract (обязательные поля)
2) Если есть downstream — заполнить HANDOFF блок
3) Сформировать DEP_EDGES:
   - из DEPENDS_ON
   - из явных handoff consumers
4) Проверить циклы
5) Выдать DEP_GRAPH snapshot
6) Если правка меняет связи — оформить через Change Control

---

## VALIDATION CHECKLIST (AUDIT)

- DR1: mini-contract есть в каждом движке
- DR2: handoff описан там, где outputs используются downstream
- DR3: DEPENDS_ON соответствует реальным входам
- DR4: нет циклов без governance break
- DR5: overlap risk помечен и имеет OWNER/решение
- DR6: contract mismatch отсутствует (produces/consumes совпадают)

---

OWNER: Universe Engine
LOCK: FIXED
CHANGE_GATE: GOVERNANCE_PIPELINE
