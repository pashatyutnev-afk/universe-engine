# VERSIONING & MEMORY ENGINE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/10__VERSIONING_MEMORY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
LAYER: 03_SYSTEM_ENTITIES
FAMILY: 00_GOVERNANCE_ENGINES
DOC_TYPE: ENGINE
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0.0
UID: <UE.ENG.GOV.VERSIONING_MEMORY.001>
OWNER: SYSTEM
ROLE: Enforce version bumps + canonical change notes + system memory records (audit, changelog, release) for every canonical modification
LOCK: FIXED

---

## 0) PURPOSE (LAW)

Этот движок отвечает за 3 вещи:

1) **Versioning** — когда и как повышать VERSION у любого канонического документа/сущности.
2) **Change Note** — как фиксировать изменение внутри самого файла (единый формат).
3) **Memory** — где хранится “память системы” о правках:
   - аудит (факт)
   - изменения (смысл)
   - релизы (упаковка/версии)

Цель:
- чтобы система оставалась воспроизводимой
- чтобы не было “тихих правок”
- чтобы можно было откатить/понять/собрать историю

Non-goals:
- не принимает решение “можно/нельзя” (это Canon Authority + Risk Safety)
- не применяет изменения (это Change Control)
- не валидирует консистентность всего репо (это Consistency)

---

## 1) DEFINITIONS (STRICT)

### 1.1 VERSION format
`MAJOR.MINOR.PATCH`

- PATCH: мелкие правки без изменения смысла интерфейсов/контрактов (опечатки, ясность, ссылки, мелкая структура)
- MINOR: добавления/расширения без поломки обратной совместимости (новые секции, новые поля, новые правила без ломки старых)
- MAJOR: ломающее изменение (переименование сущностей, смена контрактов, изменение протокола/правил так, что старое поведение не сохраняется)

### 1.2 MEMORY objects (system memory)
Системная “память” = **канонические записи** о том:
- что изменено
- почему изменено
- что затронуто
- где это зафиксировано

### 1.3 Logs separation (do not mix)
- **Audit** = “факт произошёл” (когда/что/кем)
- **Changes** = “смысл изменения” (почему/что именно/какие последствия)
- **Release** = “упакованный набор изменений” (версия системы/слоя, сводка)

---

## 2) MINI-CONTRACT (MANDATORY)

CONSUMES:
- <ARTIFACT: CHANGE_PROPOSAL>
- <ARTIFACT: CHANGE_SET>                  # list of file diffs
- <ARTIFACT: CANON_DECISION>              # from Canon Authority
- <ARTIFACT: RISK_SAFETY_REPORT>          # from Risk Safety
- <ARTIFACT: AFFECTED_FILES_LIST>

PRODUCES:
- <ARTIFACT: VERSION_BUMP_PLAN>           # which files bump which level
- <ARTIFACT: CHANGE_NOTE_BLOCKS>          # standardized blocks to paste into files
- <ARTIFACT: AUDIT_RECORD>                # one record line/entry
- <ARTIFACT: CHANGELOG_RECORD>            # one semantic entry
- <ARTIFACT: RELEASE_LOG_RECORD?>         # optional if packaged into release
- <ARTIFACT: MEMORY_PACKAGE>              # bundle pointer: where all records live

DEPENDS_ON:
- [00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG]
- [00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG]
- [00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG]
- [00_GOVERNANCE_ENGINES/09__RISK_SAFETY_ENG]

OUTPUT_TARGET:
- `99_LOGS/LOG__AUDIT.md`
- `99_LOGS/LOG__CHANGES.md`
- `08_DATABASES/DB__RELEASE_LOG.md` (optional, when changes are packaged)
- `08_DATABASES/DB__DOC_REGISTRY.md` (when doc registry requires update)

---

## 3) VERSION BUMP LAW (HARD)

### 3.1 Default rule
Любая правка канонического файла обязана:
- обновить `VERSION`
- добавить `CHANGE_NOTE` по стандарту
- создать memory entries (audit + changes)

Если правка была “только ссылка/опечатка” — всё равно PATCH.

### 3.2 Index & Law sensitivity
Для документов типа INDEX / LAW:
- любые изменения структуры, authority-order, existence rules = минимум MINOR
- смена протокола канона/сути закона = MAJOR

### 3.3 Contract breaking rule (MAJOR trigger)
Если меняется хоть одно из:
- mini-contract поля/семантика (CONSUMES/PRODUCES/DEPENDS_ON/OUTPUT_TARGET)
- правила “existence”
- UID rules / naming rules
- storage map, на который завязаны проекты/базы
→ это MAJOR (или как минимум MINOR при расширении без ломки; решение подтверждается Canon Authority)

---

## 4) CHANGE NOTE STANDARD (MANDATORY)

### 4.1 Change note block (single truth, inside file)
Каждый канонический файл обязан иметь **один** блок `CHANGE_NOTE` (в шапке файла либо сразу под шапкой).

FORMAT (strict):

CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR
- SUMMARY: "<one-line what changed>"
- REASON: "<one-line why>"
- IMPACT: "<one-line what it affects>"
- CHANGE_ID: <UE.CHG.YYYY-MM-DD.NNN>

Rules:
- Один CHANGE_NOTE блок на один “change event”.
- Если в один день несколько правок — увеличивается NNN (001..).
- Нельзя писать “misc” или “small fixes” без смысла.

### 4.2 For INDEX files
INDEX обязан дополнительно указывать:
- что добавлено/удалено из existence registry
- какие raw-links поменялись
- какие сущности стали non-canon/ignored

---

## 5) MEMORY RECORDS (WHERE + FORMAT)

### 5.1 Audit record (fact)
Target: `99_LOGS/LOG__AUDIT.md`

Minimal fields:
- DATE_TIME (or DATE if time not tracked)
- CHANGE_ID
- WHO (owner/system/user)
- WHAT (file path)
- ACTION (ADD|EDIT|MOVE|RENAME|DEPRECATE|DELETE)
- CANON_STATUS (CANON|NON-CANON)
- POINTER (commit/ref if exists)

### 5.2 Changes record (meaning)
Target: `99_LOGS/LOG__CHANGES.md`

Fields:
- DATE
- CHANGE_ID
- SCOPE (layers/families)
- SUMMARY
- DETAILS (2–6 bullets max)
- IMPACT
- MIGRATION (if any)
- RELATED (uids/paths)

### 5.3 Release record (packaging, optional)
Target: `08_DATABASES/DB__RELEASE_LOG.md`

Fields:
- RELEASE_ID (UE.REL.YYYY-MM-DD.NNN)
- DATE
- VERSION (system or layer)
- INCLUDED_CHANGE_IDS
- SUMMARY
- NOTES

---

## 6) ACTION → REQUIRED MEMORY SET (HARD)

### 6.1 EDIT canonical file
Required:
- VERSION bump
- CHANGE_NOTE inside file
- Audit record
- Changes record

### 6.2 ADD new canonical file
Required:
- registered in canonical INDEX first (existence rule)
- initial VERSION = 1.0.0 (unless DRAFT)
- Audit + Changes records
- Doc registry update if applicable

### 6.3 MOVE / RENAME
Required:
- MIGRATION_MAP (old→new)
- update all affected indexes (raw-links)
- Audit + Changes records
- bump versions for all touched indexes/files
- if UID tied to identity: UID stays same (unless replaced)

### 6.4 DEPRECATE
Required:
- mark STATUS: DEPRECATED
- provide replacement pointer
- Audit + Changes
- (optional) release record if deprecation part of release

### 6.5 DELETE
Allowed only if NON-CANON (not present in indexes) OR explicitly deprecated with policy.
Required:
- Audit + Changes
- justification why safe

---

## 7) VERSIONING PLAN GENERATION (ENGINE PROCEDURE)

Steps:
1) Take AFFECTED_FILES_LIST.
2) Classify each file by type: LAW | INDEX | ENGINE | TEMPLATE | DB | PROJECT.
3) Determine bump level:
   - PATCH default
   - MINOR if new sections/entities/registries were added
   - MAJOR if contract/protocol/identity changed
4) Emit VERSION_BUMP_PLAN:
   - file -> bump -> new version
5) Emit CHANGE_NOTE_BLOCKS for each file.
6) Emit memory records set (audit + changes + optional release).

---

## 8) COMPATIBILITY RULES (DO NOT VIOLATE)

- Must comply with `01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md`
- Must comply with `01_SYSTEM_LAW/04__CANON_PROTOCOL.md`
- Must not contradict Existence Rule of any layer indexes
- Must not create “double truth” logs: audit/changelog/release are separate roles

---

## 9) OUTPUT TEMPLATES (READY TO PASTE)

### 9.1 CHANGE_ID format
`UE.CHG.YYYY-MM-DD.NNN`

### 9.2 CHANGE_NOTE template
CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR
- SUMMARY: "<...>"
- REASON: "<...>"
- IMPACT: "<...>"
- CHANGE_ID: UE.CHG.YYYY-MM-DD.NNN

### 9.3 AUDIT record template (one line)
- DATE: YYYY-MM-DD
  TIME: HH:MM
  CHANGE_ID: UE.CHG.YYYY-MM-DD.NNN
  WHO: <...>
  ACTION: <ADD|EDIT|MOVE|RENAME|DEPRECATE|DELETE>
  FILE: <path>
  CANON: <CANON|NON-CANON>
  REF: <commit/ref?>

### 9.4 CHANGES record template
- DATE: YYYY-MM-DD
  CHANGE_ID: UE.CHG.YYYY-MM-DD.NNN
  SCOPE: <layers/families>
  SUMMARY: <...>
  DETAILS:
    - <...>
    - <...>
  IMPACT: <...>
  MIGRATION: <none|map pointer>
  RELATED: <UIDs/paths>

---

## 10) REL / XREF (UID-FIRST)

REL:
- REL: SUPPORTS | TARGET_UID: <UE.ENG.GOV.AUDIT_LOG.001> | WHY: versioning requires audit record
- REL: SUPPORTS | TARGET_UID: <UE.ENG.GOV.CHANGE_CONTROL.001> | WHY: change execution must include memory package
- REL: SUPPORTS | TARGET_UID: <UE.ENG.GOV.CANON_AUTHORITY.001> | WHY: canon decisions must be persisted in memory
- REL: SUPPORTS | TARGET_UID: <UE.ENG.GOV.RISK_SAFETY.001> | WHY: unsafe changes must be traceable and blocked
- REL: SUPPORTS | TARGET_UID: <UE.ENG.GOV.CONSISTENCY.001> | WHY: post-change validation recorded in change log

--- END.
