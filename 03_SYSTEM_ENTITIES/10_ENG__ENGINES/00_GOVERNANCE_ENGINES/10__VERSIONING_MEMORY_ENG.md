# Versioning & Memory Engine
FILE: 10__VERSIONING_MEMORY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines canonical versioning, release memory, and snapshot rules for ENG; standardizes semver, release notes, canon state capture, and links versions to audit/verdict/change artifacts

---

## PURPOSE

Этот движок отвечает за “память системы во времени”.

Он нужен, чтобы:
- было понятно, какая версия ENG сейчас “каноническая”
- можно было восстановить состояние системы на конкретный момент
- большие изменения не превращались в хаос
- изменения были связаны с Audit Log и Canon Verdict

---

## SCOPE (WHAT IT VERSIONS)

Versioning распространяется на:
- глобальный ENG INDEX
- governance rules (00/*)
- family READMEs
- engine files
- dependency definitions (DG snapshots)
- consistency reports (CR)
- решения (CV/DR)

---

## NON-GOALS

- не делает аудит качества (Consistency)
- не утверждает изменения (Canon Authority)
- не управляет workflow (Change Control)
Он задаёт “как считать версии” и “как фиксировать память”.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- approved canon verdicts (CV)
- audit entries (AL)
- change packets (CHG)
- consistency reports (CR)
- dependency graph snapshots (DG) when dependencies changed

### PRODUCES
- VERSION UPDATE rules applied (semver)
- RELEASE NOTE (RN) artifact
- CANON SNAPSHOT (CS) artifact (optional but recommended for major releases)
- memory pointers linking version -> AL/CV/CHG/CR/DG

### DEPENDS_ON
- 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md
- 00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md
- 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md
- 00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md
- 00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG.md

### OUTPUT_TARGET
- Used after approval to publish new canon version
- Required for MAJOR/MINOR updates and recommended even for PATCH

---

## VERSION STANDARD (SEMVER)

Формат: `MAJOR.MINOR.PATCH`

### PATCH
- исправления текста/формата без изменения смысла
- уточнения процедур
- no index structure change
- no contract change that affects downstream

### MINOR
- добавление новых движков в рамках существующей архитектуры
- расширение функционала без ломки контрактов
- добавление soft edges/handoffs

### MAJOR
- переименования/перенумерации
- смена уровней/классов
- изменение контрактов так, что downstream должен адаптироваться
- реструктуризация INDEX
- утверждение исключительных циклов
- изменение governance laws

---

## CANON VERSION OWNERSHIP

### Where version lives
- Each engine has local `VERSION:` field (file-level)
- Global ENG registry has:
  - `VERSION:` at top of `00__INDEX_ALL_ENGINES.md`
  - must reflect current “system version”

Правило:
- локальные версии могут отличаться (движки обновлялись точечно)
- но “system version” в INDEX фиксирует версию всего ENG слоя

---

## REQUIRED CANON ARTIFACT: RELEASE NOTE (RN)

### RELEASE_NOTE SCHEMA (CANON)

- RN_ID: RN-ENG-0001
- DATE:
- VERSION:
  - before:
  - after:
- CHANGE_TYPE:
  - PATCH | MINOR | MAJOR
- SUMMARY:
  - 5–12 bullets “что изменилось”
- BREAKING CHANGES (if MAJOR):
  - list
- NEW ENGINES (if any):
  - list
- CONTRACT CHANGES (if any):
  - list of engines + what changed
- INDEX CHANGES (if any):
  - what sections changed
- DEP_GRAPH:
  - DG reference (if changed)
- CONSISTENCY:
  - CR reference + verdict
- CANON VERDICT:
  - CV reference
- AUDIT:
  - AL reference(s)
- MIGRATION NOTES (if needed):
  - what to update downstream usage
- NOTES (optional):
  - max 7 bullets

---

## OPTIONAL BUT RECOMMENDED: CANON SNAPSHOT (CS)

Снимок “канон на дату” особенно полезен для MAJOR.

### CANON_SNAPSHOT SCHEMA (CANON)

- CS_ID: CS-ENG-0001
- DATE:
- VERSION:
- CONTENTS:
  - index version + hash/commit pointer (if used)
  - list of families included
  - list of engines included
- DEP_GRAPH:
  - DG reference
- NOTES:
  - “what this snapshot represents”
- VALIDATION:
  - CR verdict
  - lock status

---

## VERSION BUMP RULES (AUTOMATIC)

If any of these is true → MAJOR:
- renumbering
- family move/rename
- engine rename
- LEVEL/CLASS changes
- contract changes with downstream required updates
- governance law changes

Else if:
- new engines added without breaking old contracts → MINOR

Else:
- text/format fixes → PATCH

---

## PROCEDURE (HOW TO PUBLISH A VERSION)

1) Ensure change approved (CV) and logged (AL)
2) Determine bump type (PATCH/MINOR/MAJOR)
3) Update:
   - system VERSION in INDEX (global)
   - local VERSION in touched files
4) Generate Release Note (RN)
5) If MAJOR: generate Canon Snapshot (CS)
6) Link RN/CS to:
   - CV id
   - AL id(s)
   - CR/DG ids if applicable
7) Apply LOCK decisions where required

---

## MEMORY POINTERS (TRACEABILITY LAW)

Любая версия должна ссылаться минимум на:
- Canon Verdict (CV)
- Audit Log entry (AL)
- Release Note (RN)

Для изменений связей/контрактов:
- Dependency Graph snapshot (DG)

Для проверок целостности:
- Consistency Report (CR)

---

## FAILURE MODES

- обновили систему, но не обновили INDEX VERSION → “две реальности”
- нет RN → никто не понимает, что изменилось
- нет AL/CV refs → изменения не имеют законности
- MAJOR без migration notes → downstream ломается

---

OWNER: Universe Engine
LOCK: FIXED
CHANGE_GATE: GOVERNANCE_PIPELINE
