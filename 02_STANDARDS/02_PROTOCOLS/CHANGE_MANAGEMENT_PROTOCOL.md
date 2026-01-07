# CHANGE MANAGEMENT PROTOCOL (STANDARDS) (CANON)
FILE: 02_STANDARDS/02_PROTOCOLS/CHANGE_MANAGEMENT_PROTOCOL.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: PROTOCOL
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.STD.PROTOCOL.CHANGE_MGMT.200
OWNER: SYSTEM
ROLE: Operational protocol for changing documents in 02_STANDARDS (specs/modules/templates/terms). Defines the standards-layer change flow, required change package contents, and gates before canon lock.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Нормализован change protocol для STANDARDS: change package, gates, index/registry updates, SemVer bump, deprecation flow"
- REASON: "Нужен единый процесс правок стандартов без хаоса и дублей"
- IMPACT: "All changes within 02_STANDARDS"

---

## XREF (UID-first)
XREF: UE.LAW.CANON.PROTOCOL.004 | implements | standards layer follows global canon protocol | 01_SYSTEM_LAW/04__CANON_PROTOCOL.md
XREF: UE.LAW.VERSIONING.003 | depends_on | SemVer + change policy | 01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md
XREF: UE.STD.SPEC.DOC_CONTROL.103 | depends_on | doc header + change note format | 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
XREF: UE.STD.SPEC.DOC_REGISTRY.107 | depends_on | registry rules + compliance | 02_STANDARDS/01_SPECIFICATIONS/07__DOC_REGISTRY_STANDARD.md
XREF: UE.STD.SPEC.REL_XREF.104 | depends_on | UID-first links | 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md

---

## 0) PURPOSE
Этот протокол определяет операционный поток изменения стандартов в `02_STANDARDS`:
- как инициировать изменение,
- что должно быть в change package,
- какие гейты обязаны пройти,
- какие индексы/реестры надо обновлять,
- как делать deprecation, чтобы не ломать канон.

---

## 1) SCOPE (WHAT THIS PROTOCOL COVERS)
### 1.1 In scope
- SoT specs (`01_SPECIFICATIONS/*`)
- modules (`06_MARKING_STANDARDS/*`)
- protocols (`02_PROTOCOLS/*`)
- templates (`03_TECHNICAL/*` + templates in specs)
- terms (`04_TERMS_DEFINITIONS/*`)
- requirements (`05_REQUIREMENTS_TZ/*`)
- standards registries / indexes (`00__INDEX__STANDARDS.md`, `01__DOC_REGISTRY.md`, etc.)

### 1.2 Out of scope
- изменения `01_SYSTEM_LAW/*` (они идут через System Law процессы)
- изменения KB контента (они идут через KB governance)

---

## 2) CHANGE TYPES (CONTROLLED)
- `PATCH` — правка формулировок, опечаток, ссылок, уточнение без изменения контракта
- `MINOR` — добавление возможностей/правил без breaking (совместимо)
- `MAJOR` — breaking change: изменение обязательных полей, enum, контрактов, структуры

---

## 3) REQUIRED CHANGE PACKAGE (MUST)
Любая правка стандарта обязана иметь пакет изменений (может быть текстом в PR/issue, но по структуре обязателен):

### 3.1 Package fields
- CHANGE_ID: `<stable id or date-based id>`
- TARGET_DOCS: список UID документов, которые меняем
- CHANGE_TYPE: PATCH|MINOR|MAJOR
- SUMMARY: one-line
- REASON: one-line
- IMPACT: что ломается/что меняется
- MIGRATION_PLAN: (обязателен для MAJOR)
- ANTI_DUP_CHECK: почему это не создаёт второй SoT

### 3.2 Required diffs
- “before/after” по ключевым разделам
- список файлов, которые надо обновить вслед за изменением (indexes/registries/modules)

---

## 4) STANDARD CHANGE FLOW (MANDATORY STEPS)
### STEP 1 — Identify scope
- определить, это SoT / module / protocol / template / terms
- проверить, нет ли уже SoT по этому смыслу (anti-dup)

### STEP 2 — Prepare change package
- собрать пакет (раздел 3)
- определить SemVer bump

### STEP 3 — Apply edits
- правки в целевых документах
- обновить `CHANGE_NOTE` в каждом изменённом документе
- не дублировать OWNER/LOCK/VERSION вне header

### STEP 4 — Update indices and registries
Обязательные обновления:
- `02_STANDARDS/00__INDEX__STANDARDS.md` (если менялся состав/пути)
- `02_STANDARDS/01__DOC_REGISTRY.md` (если менялся состав/UID/комплаенс)
- любые под-индексы, если они существуют и зарегистрированы

### STEP 5 — Validation gates
Пройти все гейты (раздел 5).

### STEP 6 — Lock canon
- убедиться, что финальные документы имеют `LOCK: FIXED`
- изменения считаются каноном только после прохождения гейтов и фиксации версии

---

## 5) VALIDATION GATES (MUST PASS)
### G-1 Header compliance
- Doc Control header присутствует
- UID есть и валиден
- VERSION SemVer валиден

### G-2 UID integrity
- UID не дублируется
- UID не менялся без явной причины + MAJOR (если breaking identity)

### G-3 Naming compliance
- file naming соответствует Naming Rules
- коллизий `NN*` в папке нет

### G-4 Existence rule compliance
- документы зарегистрированы в `00__INDEX__STANDARDS.md`
- legacy файлы (если есть) — только как alias pointers

### G-5 Anti-dup
- один смысл → один SoT
- modules “extends SoT”, а не дублируют

### G-6 Link integrity (if used)
- XREF uses UID-first
- пути/ссылки корректны (при наличии)

---

## 6) DEPRECATION FLOW (MANDATORY WHEN REPLACING)
Если новый стандарт заменяет старый:

1) Старый документ:
   - `STATUS: DEPRECATED`
   - `DEPRECATED_BY: <UID_NEW>`
   - добавить XREF: `deprecated_by`

2) Новый документ:
   - должен явно указать, что заменяет (XREF `supersedes` допустим только при MAJOR)

3) Master-index:
   - старый остаётся в индексе как DEPRECATED (пока не ARCHIVED)
   - новый добавляется как ACTIVE

---

## 7) MODULE POLICY (SoT ↔ Modules)
Если изменение касается module:
- module обязан иметь XREF `extends` на SoT
- module не может вводить новые обязательные поля SoT
- если нужно изменить контракт — меняется SoT (MINOR/MAJOR), а module обновляется вслед

---

## 8) EMERGENCY FIX (PATCH HOTFIX)
Допускается экстренный PATCH без полного пакета, но минимум:
- что сломано
- почему срочно
- какие файлы затронуты
- обязательные гейты G-1..G-4 всё равно проходят

---

## FINAL RULE (LOCK)
Этот протокол обязателен для любых изменений в `02_STANDARDS`.
Любая правка протокола = изменение канона и проходит Canon Protocol.
--- END.
