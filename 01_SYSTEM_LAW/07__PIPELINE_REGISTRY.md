# PIPELINE REGISTRY — SYSTEM WORKFLOWS (CANON)
FILE: 01_SYSTEM_LAW/07__PIPELINE_REGISTRY.md

SCOPE: Universe Engine
LAYER: 01_SYSTEM_LAW
DOC_TYPE: REGISTRY
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.REG.PIPELINE.MASTER.007
OWNER: SYSTEM
ROLE: Canonical registry of pipelines (system workflows). Pipelines declare inputs/outputs by TYPE_UID and define validation gates.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Единый реестр пайплайнов: UID-first, I/O через TYPE_UID, шаги, gates, валидаторы, правила изменения"
- REASON: "Формализация процессов и устранение разночтений"
- IMPACT: "Standards, KB, artifact schemas, validation"

---

## 0) PRIME LAW (ABSOLUTE)
- Pipeline — это канонический workflow системы.
- Pipeline обязан объявлять входы/выходы через `TYPE_UID` (из Artifact Schema Registry).
- Pipeline обязателен там, где есть повторяемый процесс изменения/создания артефактов канона.

---

## 1) PIPELINE RECORD (MANDATORY FIELDS)
Каждый pipeline обязан иметь:

- `PIPE_UID` (UID пайплайна)
- `STATUS` (ACTIVE | DEPRECATED | DRAFT)
- `VERSION` (SemVer)
- `OWNER`
- `ROLE` (что делает)
- `INPUTS` (список TYPE_UID)
- `OUTPUTS` (список TYPE_UID)
- `STEPS` (нумерованный список шагов)
- `GATES` (минимальные проверки)
- `VALIDATION` (как проверяется: manual/CI/scripts)
- `LINKS` (XREF на законы/спеки/шаблоны)

---

## 2) MASTER PIPELINES (REGISTERED)

### P-001 — CANON CHANGE PIPELINE (Core)
- PIPE_UID: UE.PIPE.CANON.CHANGE.001
- STATUS: ACTIVE
- VERSION: 1.0.0
- OWNER: SYSTEM
- ROLE: Управляет любыми изменениями канона (proposal → gates → index updates → version bump → lock)

- INPUTS:
  - UE.ART.DOC.LAW.003
  - UE.ART.DOC.MASTER_INDEX.001
  - UE.ART.DOC.REGISTRY_TABLE.002
  - UE.ART.STD.SPEC.010
  - UE.ART.STD.MODULE.011
  - UE.ART.KB.REALM.020

- OUTPUTS:
  - UE.ART.DOC.LAW.003
  - UE.ART.DOC.MASTER_INDEX.001
  - UE.ART.DOC.REGISTRY_TABLE.002
  - UE.ART.STD.SPEC.010
  - UE.ART.STD.MODULE.011
  - UE.ART.KB.REALM.020

- STEPS:
  1) Identify scope & change type (PATCH/MINOR/MAJOR)
  2) Create change package (diff + impact + no-dup proof + migration if needed)
  3) Apply edits (content)
  4) Update indices/registries (existence + references)
  5) Version bump + Change Note update in touched canon docs
  6) Run validation gates
  7) Lock canon (ensure FIXED) and merge

- GATES:
  - Doc Control header present + single truth (no duplicated LOCK/OWNER/VERSION)
  - UID exists + unique
  - SemVer valid
  - Naming rules pass
  - Single SoT (no duplication)
  - Raw links valid (if used)

- VALIDATION:
  - manual review + CI linters (header/uid/naming/index link check)

- LINKS:
  - UE.LAW.CORE.000 (System Law Core)
  - UE.LAW.CANON.PROTOCOL.004
  - UE.LAW.VERSIONING.003
  - UE.LAW.NAMING.001
  - UE.LAW.UID.002

---

### P-002 — LAYER INDEX MAINTENANCE PIPELINE
- PIPE_UID: UE.PIPE.LAYER.INDEX.MAINT.002
- STATUS: ACTIVE
- VERSION: 1.0.0
- OWNER: SYSTEM
- ROLE: Поддержка master-index слоя (добавление/удаление/переименование файлов)

- INPUTS:
  - UE.ART.DOC.MASTER_INDEX.001

- OUTPUTS:
  - UE.ART.DOC.MASTER_INDEX.001

- STEPS:
  1) Detect file add/move/rename within layer
  2) Update master-index entries (number match, correct paths, raw links)
  3) Ensure single entrypoint index per layer
  4) Update affected registries (if any)
  5) Version bump + Change Note
  6) Validate gates

- GATES:
  - Index number matches file number
  - No duplicate entries / no duplicate raw links
  - Raw links resolve (if present)
  - Naming rules pass

- VALIDATION:
  - CI (index parser + HTTP link check)

- LINKS:
  - UE.LAW.NAMING.001
  - UE.LAW.VERSIONING.003
  - UE.LAW.CANON.PROTOCOL.004

---

### P-003 — KB REALM CANONIZATION PIPELINE
- PIPE_UID: UE.PIPE.KB.REALM.CANONIZE.003
- STATUS: ACTIVE
- VERSION: 1.0.0
- OWNER: SYSTEM
- ROLE: Приведение KB realm документов к канону (шапка/UID/структура/регистрация)

- INPUTS:
  - UE.ART.KB.REALM.020
  - UE.ART.DOC.MASTER_INDEX.001

- OUTPUTS:
  - UE.ART.KB.REALM.020
  - UE.ART.DOC.MASTER_INDEX.001

- STEPS:
  1) Add Doc Control header (STATUS/LOCK/VERSION/UID/OWNER/ROLE)
  2) Assign UID (per UID Rules)
  3) Normalize naming (per Naming Rules) or declare controlled exception
  4) Ensure realm registered in KB master-index
  5) Add minimal internal structure (Purpose + sections)
  6) Version bump + Change Note
  7) Validate gates

- GATES:
  - UID present + unique
  - SemVer valid
  - Naming compliance OR approved exception
  - Registered in KB master-index
  - No number collision in KB folder

- VALIDATION:
  - manual + CI header/naming checks

- LINKS:
  - UE.LAW.UID.002
  - UE.LAW.NAMING.001
  - UE.LAW.VERSIONING.003
  - UE.IDX.KB.MASTER.000 (KB master index UID)

---

### P-004 — ARTIFACT SCHEMA REGISTRATION PIPELINE
- PIPE_UID: UE.PIPE.ART.SCHEMA.REGISTER.004
- STATUS: ACTIVE
- VERSION: 1.0.0
- OWNER: SYSTEM
- ROLE: Добавление/изменение схемы артефакта в реестр (TYPE_UID, type key, source doc, validation)

- INPUTS:
  - UE.ART.DOC.REGISTRY_TABLE.002

- OUTPUTS:
  - UE.ART.DOC.REGISTRY_TABLE.002

- STEPS:
  1) Define schema: fields + rules + intended validation
  2) Assign TYPE_UID and (optional) TYPE_KEY
  3) Link SOURCE_DOC (spec/template that defines it)
  4) Add/Update record in Artifact Schema Registry
  5) Version bump (MINOR/MAJOR depending on compatibility)
  6) Validate gates

- GATES:
  - TYPE_UID unique
  - SemVer valid
  - Source doc exists and is canon
  - Type key format valid (if used)

- VALIDATION:
  - CI + review

- LINKS:
  - UE.REG.ARTIFACT.SCHEMA.MASTER.005
  - UE.LAW.UID.002
  - UE.LAW.VERSIONING.003
  - UE.LAW.CANON.PROTOCOL.004

---

## 3) CHANGE RULES (PIPELINES)
- Добавление нового pipeline — MINOR.
- Изменение шагов/гейтов, не ломающих совместимость — MINOR.
- Изменение входов/выходов или контрактов пайплайна — MAJOR + migration plan.
- Удаление пайплайна запрещено без DEPRECATED → ARCHIVED.

---

## 4) VALIDATION REQUIREMENTS (MUST PASS)
- PIPE_UID уникален
- STATUS валиден
- VERSION SemVer валиден
- INPUTS/OUTPUTS используют только TYPE_UID (не local ids)
- ссылки на законы/реестры корректны

---

## FINAL RULE (LOCK)
Этот registry определяет канонические пайплайны Universe Engine.
Любая правка — изменение канона и проходит Canon Protocol.
--- END.
