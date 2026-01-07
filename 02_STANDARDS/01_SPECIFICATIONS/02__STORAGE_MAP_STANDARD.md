# STORAGE MAP STANDARD (SoT) (CANON)
FILE: 02_STANDARDS/01_SPECIFICATIONS/02__STORAGE_MAP_STANDARD.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: SPEC
SPEC_TYPE: SoT
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.STD.SPEC.STORAGE_MAP.102
OWNER: SYSTEM
ROLE: Source-of-Truth specification for canonical storage layout: layer folders, subfolders, entrypoint indexes, and placement rules for artifacts.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Нормализован Storage Map SoT: слои/папки/entrypoints, правила размещения, запрет коллизий, связка с индексами"
- REASON: "Согласование с System Law и устранение путаницы 'где что лежит'"
- IMPACT: "All layers, master-index navigation, KB governance, pipelines"

---

## 0) PURPOSE (LAW)
Этот документ — SoT-спека о том:
- какие корневые папки составляют Universe Engine,
- что означает “слой” (layer) как единица структуры,
- где обязаны лежать entrypoints (master-index),
- как размещать документы/реестры/модули/шаблоны,
- какие коллизии структуры запрещены.

---

## 1) AUTHORITY & XREF (UID-first)
Primary authority:
- `01_SYSTEM_LAW/00__SYSTEM_LAW.md`
- `01_SYSTEM_LAW/01__NAMING_RULES.md`
- `01_SYSTEM_LAW/02__UID_RULES.md`
- `01_SYSTEM_LAW/06__CONSTRAINTS_REGISTRY.md`

XREF:
- XREF: UE.LAW.CORE.000 | governs | existence/authority | 01_SYSTEM_LAW/00__SYSTEM_LAW.md
- XREF: UE.LAW.NAMING.001 | governs | naming patterns | 01_SYSTEM_LAW/01__NAMING_RULES.md
- XREF: UE.LAW.UID.002 | defines | UID rules | 01_SYSTEM_LAW/02__UID_RULES.md
- XREF: UE.REG.CONSTRAINTS.MASTER.006 | enforces | hard constraints | 01_SYSTEM_LAW/06__CONSTRAINTS_REGISTRY.md

---

## 2) CANONICAL ROOT STRUCTURE (LAYERS)
Universe Engine хранится в корне репозитория как набор слоёв.

### 2.1 Root layers (minimum set)
- `01_SYSTEM_LAW/` — ядро законов (L0/L1)
- `02_STANDARDS/` — стандарты, спеки, протоколы, шаблоны (SoT)
- `04_KNOWLEDGE_BASE/` — знания (governance + realms + passports)

### 2.2 Optional / planned layers (allowed when indexed)
Следующие слои допускаются, но считаются каноничными только после появления master-index и регистрации:
- `03_<...>/` — зарезервировано (например production systems, assets, etc.)
- `05_<...>/` — outputs/builds/export
- `06_<...>/` — logs/audit
(конкретизация — через Canon Protocol)

---

## 3) ENTRYPOINT RULE (MASTER INDEX)
### 3.1 Один entrypoint на слой (ABSOLUTE)
Каждый слой обязан иметь ровно один master-index (L1), обычно:
- `00__INDEX__<LAYER>.md`

Пример:
- `01_SYSTEM_LAW/00__INDEX__SYSTEM_LAW.md`
- `02_STANDARDS/00__INDEX__STANDARDS.md`
- `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`

### 3.2 Запрет альтернативных индексов
Alt/legacy index не может быть каноном.
Допускается только как NON-CANON alias pointer (короткий указатель на канон).

---

## 4) PLACEMENT RULES (WHERE THINGS LIVE)
### 4.1 What goes into 01_SYSTEM_LAW
Только системные законы/реестры системы (authority, naming, uid, versioning, canon protocol, schema registry, constraints, pipelines).

Запрещено:
- контент мира
- “спеки мира”
- KB контент

### 4.2 What goes into 02_STANDARDS
- SoT specs (как должно быть)
- Modules (детализация SoT)
- Protocols (операционка для стандартов)
- Templates (формы документов/артефактов)
- Terms (глоссарий)
- Requirements/TZ (если это стандартизированное ТЗ)

### 4.3 What goes into 04_KNOWLEDGE_BASE
- governance (правила KB, карты, типы сущностей, шаблоны паспортов)
- realms (доменные знания)
- passports (описания сущностей)

---

## 5) SUBFOLDER CONVENTIONS (STANDARDIZED)
Это рекомендуемые подпапки внутри слоя (если слой их использует).  
Внутри одного слоя допускаются свои подсистемы, но их структура должна быть зарегистрирована в master-index.

### 5.1 Standards subfolders (canonical)
- `00_CANON/` — обзор/канон стандарта слоя (reference)
- `01_SPECIFICATIONS/` — SoT спеки
- `02_PROTOCOLS/` — протоколы
- `03_TECHNICAL/` — шаблоны/формы
- `04_TERMS_DEFINITIONS/` — глоссарий/термины
- `05_REQUIREMENTS_TZ/` — требования/ТЗ
- `06_MARKING_STANDARDS/` — модули маркировки (детализация)

### 5.2 KB subfolders (canonical)
- `00_KB_GOVERNANCE/` — правила/карты/реестры KB (не контент)
- `01..08 realms` — либо файлами, либо папками (решается governance, но должно быть единообразно)

---

## 6) NUMBERING & COLLISION RULES (HARD)
### 6.1 No collisions in folder (ABSOLUTE)
В одной папке запрещено иметь два канонических файла с одинаковым префиксом `NN*`.

Пример конфликта (нельзя):
- `02_CHARACTER_CRAFT.md`
- `02__KB_TAGS.md`

Решение:
- перенумеровать один файл
- вынести в подпапку
- или объявить controlled exception (через Naming Rules + Canon Protocol)

### 6.2 Root-level `00__*` collisions
Если `00__INDEX__...` уже существует в папке слоя, то другие `00__*` в той же папке не могут быть каноном.
Они должны:
- быть переименованы на `01__...`, `02__...` и т.д.,
- или стать NON-CANON alias pointers.

---

## 7) RAW LINK POLICY (REFERENCE ONLY)
Raw-ссылки в индексах допустимы как reference, но канон определяется:
- путём (FILE) + регистрацией в master-index
- UID в шапке

Если raw-ссылка ломается, но файл существует — чинится ссылка (PATCH/MINOR), а не “перепридумывается” структура.

---

## 8) OUTPUT / BUILD STORAGE (IF USED)
Если система производит выходные сборки/экспорты, рекомендуется:
- хранить их отдельно от SoT/KB, в выделенном слое (например `05_OUTPUT/`),
- и регистрировать этот слой отдельным master-index, когда он становится каноничным.

---

## 9) MIGRATION NOTES (CURRENT REPO)
S0:
- устранить корневые коллизии `00__*` в `02_STANDARDS/` (уже начато: `01__DOC_REGISTRY.md`, `02__MASTER_INDEX__...md`)
- привести документы к Doc Control header + UID + SemVer

S1:
- нормализовать имена файлов в подпапках протоколов/шаблонов/терминов под Naming Rules

---

## FINAL RULE (LOCK)
Storage Map — это SoT по размещению и структуре.
Любая правка, меняющая слои/entrypoints/placement rules = изменение канона (Canon Protocol).
--- END.
