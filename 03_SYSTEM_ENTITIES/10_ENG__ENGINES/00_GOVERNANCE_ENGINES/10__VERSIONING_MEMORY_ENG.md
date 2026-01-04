# Versioning & Memory Engine
FILE: 10__VERSIONING_MEMORY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines versioning strategy, release snapshots, and long-term memory of canonical states (audit/decision/change → release)

---

## PURPOSE

Этот движок делает систему **воспроизводимой во времени**:
- вводит понятие версий/релизов канона
- фиксирует “снимки” состояния (release snapshots)
- связывает изменения с audit и decision
- задаёт compatibility/migration правила для breaking изменений

---

## NON-GOALS

- не утверждает канон (это Canon Authority)
- не управляет изменениями по шагам (это Change Control)
- не проверяет целостность после изменений (это Consistency)

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- audit events (AL)
- decision records (DR)
- change packets (CHG)
- index states (registry snapshots)
- compatibility/migration notes (если есть)

### PRODUCES
- Release Note (RN) — обязательный артефакт релиза
- Snapshot Reference (SR) — ссылка на фиксированный снимок (commit/tag/ref)
- Compatibility Notes (CN)
- Migration Guide (MG) — если MAJOR/breaking
- Rollback Plan (RB) — если MAJOR

### DEPENDS_ON
- 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md
- 00_GOVERNANCE_ENGINES/07__DECISION_APPROVAL_ENG.md
- 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md
- 00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md
- 00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md

### OUTPUT_TARGET
- Release packets for canon milestones
- Reference used by all indexes/standards when claiming “as of version X”

---

## DEFINITIONS (CANON)

- **Canon Version** — версия канона (структура + индексы + ключевые правила).
- **Release Snapshot** — фиксированный снимок состояния (commit/tag/ref).
- **Milestone** — значимый этап (например, завершён слой ENG).
- **Compatibility** — совместимость форматов/правил между версиями.
- **Changelog** — список изменений между версиями.

---

## VERSIONING STRATEGY (CANONICAL)

Модель SemVer:
- **MAJOR**: ломаем форматы/пути/иерархии (breaking)
- **MINOR**: добавляем сущности/семейства без ломки старого
- **PATCH**: правки без изменения контрактов

Пример: `1.2.3`

---

## CANON ARTIFACTS (SCHEMAS)

### RELEASE_NOTE (RN)
- RN_ID:
- DATE:
- VERSION:
- SNAPSHOT_REF:
- CHANGE_SUMMARY (3–10 bullets):
- INCLUDED_CHG (list of CHG_ID):
- INCLUDED_DR (list of DR_ID):
- REQUIRED_MIGRATION: yes/no
- MIGRATION_REF (if any):
- COMPATIBILITY_NOTES:
- KNOWN_RISKS (if any, RR refs):
- CONSISTENCY_STATUS: PASS/FAIL
- OWNER:

### SNAPSHOT_REFERENCE (SR)
- SR_ID:
- VERSION:
- REF_TYPE: commit | tag | branch_ref
- REF_VALUE:
- INDEX_ANCHORS:
  - list of canonical indexes/standards that define this release

---

## RULES (LOCKED)

- V1: Нельзя выпускать MAJOR без MG (migration guide) и RB (rollback plan).
- V2: Релиз обязан фиксировать “точки истины”: какие индексы/законы определяют систему.
- V3: Любые изменения форматов должны иметь CN (compatibility note).
- V4: История не стирается: только supersede (заменить), но не delete.

---

## INTEGRATION

- Audit Log фиксирует факты изменений → Versioning связывает их в релизы.
- Decision Approval фиксирует причины → Versioning включает DR refs в RN.
- Risk Safety требует rails для крупных релизов → Versioning тянет RR refs.
- Consistency обязателен PASS перед релизом.

---

## FINAL (LOCK)

OWNER: Universe Engine  
LOCK: FIXED
