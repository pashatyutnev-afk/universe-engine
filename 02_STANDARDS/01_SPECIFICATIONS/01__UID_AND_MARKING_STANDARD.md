# UID & MARKING STANDARD (SoT) (CANON)
FILE: 02_STANDARDS/01_SPECIFICATIONS/01__UID_AND_MARKING_STANDARD.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: SPEC
SPEC_TYPE: SoT
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.STD.SPEC.UID_MARKING.101
OWNER: SYSTEM
ROLE: Source-of-Truth specification for system identification and canonical marking across Universe Engine layers (UID usage, doc headers, marking modules boundaries).

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Нормализован SoT UID & Marking: UID-first, правила маркировки, связка SoT↔modules, запрет дублей"
- REASON: "Согласование со слоями LAW и устранение противоречий/дублирования"
- IMPACT: "All layers, indices, KB governance, modules in 06_MARKING_STANDARDS"

---

## 0) PURPOSE (LAW)
Этот документ — SoT-спека для:
- использования UID как системного языка идентификации,
- обязательной маркировки (header marking) канонических документов,
- правил “что такое module маркировки” и как он связан с SoT.

Эта спека НЕ заменяет законы `01_SYSTEM_LAW`, а применяет их к стандартам и маркировке.

---

## 1) AUTHORITY & REFERENCES (XREF)
Primary authority:
- `01_SYSTEM_LAW/00__SYSTEM_LAW.md` (Core Law)
- `01_SYSTEM_LAW/02__UID_RULES.md`
- `01_SYSTEM_LAW/01__NAMING_RULES.md`
- `01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md`
- `01_SYSTEM_LAW/04__CANON_PROTOCOL.md`

XREF (UID-first):
- XREF: UE.LAW.CORE.000 | governs | core authority and existence rules | 01_SYSTEM_LAW/00__SYSTEM_LAW.md
- XREF: UE.LAW.UID.002 | defines | UID format and stability | 01_SYSTEM_LAW/02__UID_RULES.md
- XREF: UE.LAW.NAMING.001 | governs | naming constraints | 01_SYSTEM_LAW/01__NAMING_RULES.md
- XREF: UE.LAW.VERSIONING.003 | governs | semver + change policy | 01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md
- XREF: UE.LAW.CANON.PROTOCOL.004 | governs | canon change process | 01_SYSTEM_LAW/04__CANON_PROTOCOL.md

---

## 2) DEFINITIONS (TERMS)
- **UID** — единственный канонический идентификатор системы (см. UID Rules).
- **Marking** — маркировка документа/артефакта через шапку и стандартизированные поля.
- **Doc Control Header** — обязательная “шапка” канонического документа.
- **SoT Spec** — спецификация, которая определяет “как должно быть” (единственная истина).
- **Module** — документ детализации, который расширяет SoT, но не является SoT.

---

## 3) UID IS PRIMARY (ABSOLUTE)
### 3.1 UID обязателен
Любой канонический документ обязан иметь `UID` в шапке.

### 3.2 UID неизменяем
UID нельзя менять без Canon Protocol и версии MAJOR (если это breaking).

### 3.3 UID используется в XREF/REL
Любая межслойная ссылка использует UID как primary (local id не годится как единственный идентификатор).

---

## 4) DOC CONTROL HEADER (MARKING) — MINIMUM STANDARD
Каждый канонический документ обязан иметь в начале файла header с минимумом:

- `FILE`
- `SCOPE`
- `LAYER`
- `DOC_TYPE`
- `LEVEL`
- `STATUS`
- `LOCK`
- `VERSION`
- `UID`
- `OWNER`
- `ROLE`
- `CHANGE_NOTE` (последнее изменение)

### 4.1 Single truth rule
Запрещено дублировать `OWNER/LOCK/VERSION/STATUS` внизу документа отдельными строками.
Одна истина — в header.

### 4.2 Status & Lock meaning
- `STATUS: ACTIVE` — документ применим
- `STATUS: DEPRECATED` — документ устарел, но существует
- `LOCK: FIXED` — каноничный документ, правки только по Canon Protocol
- `LOCK: OPEN` — черновик, не канон (не регистрируется в master-index)

---

## 5) MARKING MODULES BOUNDARY (SoT vs Modules)
### 5.1 SoT defines, modules detail
- SoT документ определяет правило/контракт (что обязательно).
- Modules дают детализацию/варианты применения (как именно оформлять маркеры), но:
  - не вводят вторую истину,
  - не противоречат SoT,
  - обязаны ссылаться на SoT.

### 5.2 Prohibited duplication
Запрещено:
- копировать целые разделы SoT в module “как будто это SoT”
- иметь два документа, которые оба называют себя SoT по одной теме

---

## 6) REQUIRED MARKING SET (CANON KEYS)
Набор ключей маркировки обязателен для канонических документов:

### 6.1 Identity keys
- `UID` (system identity)
- `FILE` (path identity)

### 6.2 Control keys
- `STATUS`
- `LOCK`
- `VERSION` (SemVer)

### 6.3 Context keys
- `SCOPE`
- `LAYER`
- `DOC_TYPE`
- `LEVEL`
- `OWNER`
- `ROLE`

### 6.4 Change keys
- `CHANGE_NOTE` (последнее изменение)

---

## 7) VALIDATION (COMPLIANCE)
Документ считается compliant, если:
- header содержит все обязательные ключи
- UID валиден и уникален
- VERSION SemVer валиден
- LOCK/STATUS не дублируются и не конфликтуют
- документ зарегистрирован в master-index своего слоя

---

## 8) INTERFACE TO MARKING MODULES (06_MARKING_STANDARDS)
Модули маркировки должны:
- иметь Doc Control header и UID
- содержать XREF на этот SoT:
  - `XREF: UE.STD.SPEC.UID_MARKING.101 | extends | module details for marking | <path>`
- не вводить новые обязательные header keys без MAJOR изменения SoT

---

## 9) MIGRATION NOTES (CURRENT REPO)
S0:
- Привести все канонические документы к header/UID/SemVer.
- Устранить коллизии `00__*` в корне `02_STANDARDS/` (уже начато через alias-подход).

S1:
- Нормализовать протоколы/темплейты, которые не соответствуют `NN__...md`, или зафиксировать исключения.

---

## FINAL RULE (LOCK)
Эта спека — единственная истина по стандарту UID & Marking внутри слоя STANDARDS.
Любая правка обязательных ключей/контрактов = изменение канона (Canon Protocol).
--- END.
