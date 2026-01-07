# UNIVERSE ENGINE — MASTER INDEX (GLOBAL MAP) (CANON)
FILE: 02_STANDARDS/02__MASTER_INDEX__UNIVERSE_ENGINE.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: INDEX
INDEX_TYPE: GLOBAL_MASTER_MAP
LEVEL: L0
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.IDX.STD.MASTER_MAP.002
OWNER: SYSTEM
ROLE: Global navigation map of the Universe Engine. Single entrypoint for locating layer master-indexes, registries, and canonical flows.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MAJOR
- SUMMARY: "Нормализован GLOBAL MASTER INDEX под System Law: Doc Control header, UID/SemVer, корректные канонические entrypoints, устранение конфликтного имени 00__*"
- REASON: "Конфликт '00__*' в корне слоя + необходимость согласования с System Law"
- IMPACT: "Глобальная навигация по всем слоям"

---

## 0) PURPOSE (LAW)
Этот файл — глобальная карта системы Universe Engine.

Он определяет:
- где находятся канонические entrypoints слоёв (master-index)
- как работает правило существования (existence via index)
- как человек и чат навигируют по системе без путаницы

---

## 1) EXISTENCE LAW (ABSOLUTE)
1) Любой слой “существует” через свой master-index (L1).
2) Если объекта/файла нет в соответствующем master-index слоя — он NON-CANON (ignored).
3) Любая “альтернативная точка входа” (alt-index) запрещена как канон.

---

## 2) ID LAW (GLOBAL)
Единственный язык идентификации системы — UID.

- UID обязателен для всех канонических документов/реестров/пайплайнов.
- Межслойные ссылки (REL/XREF) должны использовать UID как primary.

---

## 3) SYSTEM LAYERS (GLOBAL MAP)
Ниже — карта слоёв. Для каждого слоя указан entrypoint (master-index).

### 3.1 CORE LAW (System)
- Layer: 01_SYSTEM_LAW
- Entrypoint (Master Index): `01_SYSTEM_LAW/00__INDEX__SYSTEM_LAW.md`

### 3.2 STANDARDS
- Layer: 02_STANDARDS
- Entrypoint (Master Index): `02_STANDARDS/00__INDEX__STANDARDS.md`
- Doc Registry (Standards): `02_STANDARDS/01__DOC_REGISTRY.md`

Key SoT specs (entry references):
- UID & Marking SoT: `02_STANDARDS/01_SPECIFICATIONS/01__UID_AND_MARKING_STANDARD.md`
- Doc Control SoT: `02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md`
- REL/XREF SoT: `02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md`

### 3.3 KNOWLEDGE BASE
- Layer: 04_KNOWLEDGE_BASE
- Entrypoint (Master Index): `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`
- Governance core: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/00__README__KB_REALM.md`

### 3.4 OTHER LAYERS (PLANNED / OPTIONAL)
Следующие слои могут быть подключены, но считаются каноничными только после появления их master-index и регистрации:
- ENT (System Entities)
- PRJ (Projects)
- AST (Assets)
- OUT (Output)
- LOG (Audit/Logs)

---

## 4) SOURCE OF TRUTH — REGISTRIES (PRIMARY RULE)
Если два файла претендуют на одну истину:
- истина = зарегистрированный SoT/Registry (по master-index)
- всё остальное = производные/копии/представления и не может переопределять SoT

---

## 5) NAVIGATION FLOW (HOW TO USE)
### 5.1 Если решаем системные вопросы
01_SYSTEM_LAW → master-index → нужный LAW → применяем

### 5.2 Если работаем со стандартами
02_STANDARDS → master-index → SPEC (SoT) → MODULE (если нужно детализация) → применяем

### 5.3 Если строим знания о мире
04_KNOWLEDGE_BASE → master-index → governance → realm → сущности → регистрация в KB registry

---

## 6) CHANGE RULE (CANON)
Любая правка этого файла меняет глобальную навигацию и считается изменением канона:
- проходит Canon Protocol
- требует SemVer version bump
- требует актуализации ссылок на entrypoints

---

## FINAL RULE (LOCK)
Этот документ — глобальная карта системы.
Любая правка структуры entrypoints/реестров = изменение канона.
--- END.
