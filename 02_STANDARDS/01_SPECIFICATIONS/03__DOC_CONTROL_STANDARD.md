# DOC CONTROL STANDARD (SoT) (CANON)
FILE: 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: SPEC
SPEC_TYPE: SoT
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.STD.SPEC.DOC_CONTROL.103
OWNER: SYSTEM
ROLE: Source-of-Truth specification for canonical document control: header schema, required keys, allowed enums, change notes, deprecation markers, and compliance rules across the Universe Engine.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Нормализован Doc Control SoT: единая шапка, обязательные поля, SemVer, deprecation, XREF/REL блоки, compliance правила"
- REASON: "Согласование с System Law и устранение разнобоя в метаданных"
- IMPACT: "All canon docs in all layers"

---

## 0) PURPOSE (LAW)
Этот документ — SoT-спека о том:
- как выглядит канонический Doc Control header,
- какие поля обязательны,
- какие значения разрешены (enums),
- как фиксировать изменения (Change Note),
- как помечать deprecation,
- как валидировать compliance.

---

## 1) AUTHORITY & XREF (UID-first)
Primary authority:
- `01_SYSTEM_LAW/00__SYSTEM_LAW.md`
- `01_SYSTEM_LAW/02__UID_RULES.md`
- `01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md`
- `01_SYSTEM_LAW/01__NAMING_RULES.md`
- `01_SYSTEM_LAW/06__CONSTRAINTS_REGISTRY.md`

XREF:
- XREF: UE.LAW.CORE.000 | governs | core authority | 01_SYSTEM_LAW/00__SYSTEM_LAW.md
- XREF: UE.LAW.UID.002 | defines | UID format/stability | 01_SYSTEM_LAW/02__UID_RULES.md
- XREF: UE.LAW.VERSIONING.003 | governs | SemVer + change policy | 01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md
- XREF: UE.LAW.NAMING.001 | governs | naming constraints | 01_SYSTEM_LAW/01__NAMING_RULES.md
- XREF: UE.REG.CONSTRAINTS.MASTER.006 | enforces | doc control constraints | 01_SYSTEM_LAW/06__CONSTRAINTS_REGISTRY.md

---

## 2) CANONICAL DOC HEADER (MANDATORY)
### 2.1 Header layout (top-of-file)
Header должен быть в начале файла, до основного содержания.

Минимальный канонический header:

- `FILE: <path>`
- `SCOPE: <system>`
- `LAYER: <layer>`
- `DOC_TYPE: <type>`
- `LEVEL: <L0/L1/L2/...>`
- `STATUS: <enum>`
- `LOCK: <enum>`
- `VERSION: <SemVer>`
- `UID: <UID>`
- `OWNER: <owner>`
- `ROLE: <one-line role>`

И затем блок:

`CHANGE_NOTE:`
- `DATE: YYYY-MM-DD`
- `TYPE: PATCH | MINOR | MAJOR`
- `SUMMARY: "..."` (one line)
- `REASON: "..."` (one line)
- `IMPACT: "..."` (one line)

### 2.2 Header is single source of truth (ABSOLUTE)
Запрещено:
- дублировать `OWNER/LOCK/VERSION/STATUS/UID` отдельно внизу документа
- иметь “вторую шапку” в конце

---

## 3) CONTROLLED ENUMS (VALID VALUES)
### 3.1 STATUS enum
- `ACTIVE` — действует
- `DEPRECATED` — устарел, но существует (must have deprecated pointer)
- `ARCHIVED` — сохранён как история (не используется)
- `DRAFT` — черновик (не канон, не регистрируется в master-index)

### 3.2 LOCK enum
- `FIXED` — каноничный, правки только по Canon Protocol
- `OPEN` — рабочий/черновик, не канон

### 3.3 LEVEL meanings
- `L0` — абсолютный корень системы (core maps, global law)
- `L1` — layer entrypoints, SoT specs, governance regs, master registries
- `L2+` — производные/подразделы/контент, подчинённый L1

---

## 4) DOC_TYPE ENUM (RECOMMENDED SET)
DOC_TYPE — контролируемый тип документа.

Минимальный набор:
- `LAW`
- `LAW_PROTOCOL`
- `SPEC` (SoT)
- `MODULE`
- `PROTOCOL`
- `TEMPLATE`
- `INDEX`
- `REGISTRY`
- `TERMS`
- `REQUIREMENTS`
- `GUIDE` (если нужен справочник, но не SoT)

---

## 5) OPTIONAL HEADER FIELDS (ALLOWED)
Разрешённые дополнительные поля (если применимо):
- `INDEX_TYPE: ...` (для INDEX)
- `SPEC_TYPE: SoT` (для SPEC)
- `DEPRECATED_BY: <UID>` (если STATUS=DEPRECATED)
- `CANON_TARGET: <path>` (для legacy alias pointers)
- `MIGRATION_PLAN: <short>` (если есть миграции)
- `XREF_BLOCK: PRESENT` (если есть XREF список ниже)
- `TAGS: ...` (только если тег-система определена)

---

## 6) DEPRECATION STANDARD
Если `STATUS: DEPRECATED`, документ обязан содержать в header:
- `DEPRECATED_BY: <UID_TARGET>`

И внутри документа (в начале содержания) минимум:
- краткое “why deprecated”
- куда мигрировать (path + UID)

---

## 7) XREF / REL BLOCK (STANDARDIZED SECTION)
Если документ имеет межслойные связи, он должен содержать раздел:

`## XREF (UID-first)`

Формат строк:
- `XREF: <UID_TARGET> | <REL_TYPE> | <WHY> | <PATH(optional)>`

Рекомендуемые `REL_TYPE`:
- `defines`, `governs`, `depends_on`, `extends`, `implements`, `references`, `deprecated_by`

---

## 8) COMPLIANCE RULES (WHEN DOC IS CANON)
Документ считается каноническим, если одновременно:
1) `LOCK: FIXED` и `STATUS` не DRAFT
2) зарегистрирован в master-index своего слоя
3) имеет полный Doc Control header
4) имеет уникальный UID
5) имеет SemVer version
6) соблюдает Naming Rules (или approved exception)
7) не нарушает Constraints Registry

Если любой пункт не выполнен:
- документ NON-CANON или INVALID до исправления.

---

## 9) MIGRATION NOTES (CURRENT REPO)
S0:
- привести все документы (особенно L1) к этому header формату
- заменить старые “OWNER/LOCK: FIXED” внизу на корректный header

S1:
- унифицировать DOC_TYPE/SPEC_TYPE поля во всех слоях

---

## FINAL RULE (LOCK)
Doc Control — SoT для всех канонических документов Universe Engine.
Любая правка обязательных полей/enum = MAJOR по умолчанию.
--- END.
