# CHANGE MANAGEMENT PROTOCOL (CANON)

FILE: 02_STANDARDS/02_PROTOCOLS/01__CHANGE_MANAGEMENT_PROTOCOL.md
SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: PROTOCOL
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.PROTO.CHANGE.001
OWNER: SYSTEM
ROLE: Canon protocol for proposing, approving, logging, and applying changes to docs/entities/standards under Universe Engine rules.

CHANGE_NOTE:
- DATE: 2026-01-19
- TYPE: MINOR
- SUMMARY: "Aligned change workflow with START runtime: entrypoint-only execution, snapshot refresh rule, mandatory change packets, explicit signoff chain, and no silent edits."
- REASON: "Make changes auditable and deterministic under RAW-only navigation."
- IMPACT: "Every modification becomes traceable; prevents hidden drift and path guessing."
- CHANGE_ID: UE.CHG.2026-01-19.PROTO.CHANGE.001

---

## 0) PURPOSE (LAW)
Этот протокол фиксирует единый порядок управления изменениями:
- как инициируются изменения
- как они оформляются и согласуются
- как регистрируются и проходят гейты
- как запрещаются «тихие» правки
- как обрабатывается обновление ROOT LINK BASE (снимка ссылок)

---

## 1) SCOPE
Применяется ко всем изменениям в репозитории Universe Engine:
- System Law (01_SYSTEM_LAW)
- Standards / Protocols / Specifications (02_STANDARDS)
- System Entities (03_SYSTEM_ENTITIES)
- Knowledge Base (04_KNOWLEDGE_BASE)
- Projects / Assets / DB / Logs (05/06/08/99)

---

## 2) ABSOLUTE LAWS
### 2.1 No silent changes (LAW)
Запрещены «тихие» изменения без CHANGE_PACKET.
Любая правка обязана иметь:
- CHANGE_NOTE (внутри изменяемого файла) и/или
- CHANGE_PACKET (отдельный артефакт изменения)

Минимум: в изменяемом файле должен быть блок CHANGE_NOTE с CHANGE_ID.

### 2.2 EntryPoint alignment (LAW)
Выполнение задач в чате идёт только через `START_UNIVERSE_ENGINE`.
Если пользователь не запускал рантайм, система не применяет изменения, а только:
- описывает, что надо изменить
- выдаёт полный файл (предложение правки) как артефакт

### 2.3 Snapshot refresh is a change (LAW)
Обновление ROOT LINK BASE (снимка ссылок) считается изменением системы.
Требуется CHANGE_PACKET с явной фиксацией:
- что изменилось в ссылках
- почему
- какой риск несоответствия при старом снимке

---

## 3) CHANGE TYPES
Используются три типа:

### 3.1 PATCH
- исправление формулировок, выравнивание правил, устранение неоднозначностей
- не ломает совместимость маршрутов и сущностей

### 3.2 MINOR
- добавление секций/гейтов/артефактных требований
- может расширять процесс, но не ломает базовую совместимость

### 3.3 MAJOR
- ломает совместимость, меняет маршруты, UID правила, структуры хранения, обязательные контракты
- требует явного MIGRATION PLAN и deprecation pointers

---

## 4) ROLES & APPROVAL AUTHORITY
### 4.1 Mandatory initiator
Любое изменение должно быть инициировано через Top Governance SPC:
- MACHINE_ARCHITECT_SPC (держит владение изменением)

### 4.2 Domain authorities
- GOVERNANCE_OWNER_SPC: закон, иерархия правил, authority conflicts
- STANDARDS_OWNER_SPC: стандарты/протоколы/спеки
- DOC_CONTROLLER_SPC: doc control, naming, UID, структура, шаблоны
- PIPELINE_ARCHITECT_SPC: пайплайны/ORC маршруты
- INTEGRATION_PACKER_SPC: output packs и упаковка артефактов

### 4.3 Mandatory finish chain (approval)
Изменение считается принятым только если прошло:
READINESS_CHECK_CTL → relevant VAL → relevant QA → DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC signoff

---

## 5) REQUIRED ARTIFACT: CHANGE_PACKET
### 5.1 Change packet minimum schema
Каждое изменение оформляется как CHANGE_PACKET (даже если мелкое).

#### CHANGE_PACKET header (minimum)
- FILE:
- SCOPE:
- DOC_TYPE: CHANGE_PACKET
- STATUS:
- VERSION:
- UID:
- OWNER:
- ROLE:
- CHANGE_ID:
- DATE:
- TYPE: PATCH | MINOR | MAJOR
- SUMMARY:
- REASON:
- IMPACT:

#### AFFECTED FILES block (minimum)
Список файлов, которые меняются:
- file path (как в репо)
- RAW link (если есть)
- change summary per file

#### RISKS block (minimum)
- Risks:
- Rollback plan:
- Deprecation pointers (если нужно):

#### SIGNOFF block (minimum)
- DOC_CONTROLLER_SPC:
- MACHINE_ARCHITECT_SPC:

### 5.2 CHANGE_ID law
Каждый CHANGE_PACKET обязан иметь уникальный CHANGE_ID формата:
UE.CHG.YYYY-MM-DD.<DOMAIN>.<NNN>

DOMAIN примеры:
- START
- PROTO.CHAT
- PROTO.CHANGE
- LAW
- STD
- ENT

---

## 6) WORKFLOW (DEFAULT)
### Step 1: Intake (MACHINE_ARCHITECT_SPC)
- формулирует change request как задачу
- определяет тип (PATCH/MINOR/MAJOR)
- определяет affected files
- определяет требуемые сущности (SPC/ORC/ENG/CTL/VAL/QA)

### Step 2: Draft (STANDARDS_OWNER_SPC + DOC_CONTROLLER_SPC)
- готовит новые версии файлов
- добавляет CHANGE_NOTE в каждый изменённый файл
- проверяет UID/naming/doc control

### Step 3: Preflight (READINESS_CHECK_CTL)
- проверка минимальных входов
- проверка что ссылки RAW доступны (если применимо)
- проверка что структура и заголовки соответствуют стандартам

### Step 4: Validation (relevant VAL)
- checks на нарушения правил (например: UID conflicts, naming conflicts, index structure violations)
- формирует violation records (если нужно)

### Step 5: QA gates (relevant QA)
- проверка читабельности, непротиворечивости, регрессии
- если MAJOR: обязательна проверка migration plan

### Step 6: Packaging (INTEGRATION_PACKER_SPC)
- собирает финальные файлы
- обеспечивает “full file” (не куски)
- фиксирует финальные имена/версии

### Step 7: Signoff
- DOC_CONTROLLER_SPC подтверждает doc control
- MACHINE_ARCHITECT_SPC подтверждает принятие
- CHANGE_PACKET готов к регистрации

---

## 7) REGISTRATION & LOGGING (MINIMUM)
После signoff изменение должно быть отражено минимум в одном месте из системных журналов:
- Change log / Audit log / Doc registry (в зависимости от подсистемы)

Минимальное требование:
- CHANGE_ID
- список файлов
- дата
- тип
- краткий summary

---

## 8) DEPRECATION & MIGRATION (MAJOR ONLY)
Если изменение ломает совместимость:
- обязателен MIGRATION PLAN (отдельный блок в CHANGE_PACKET или отдельный файл)
- обязателен DEPRECATION POINTER (куда переехало, что заменяет, сроки)
- запрещено удалять без указателя

---

## 9) ROLLBACK RULE
Любое изменение обязано иметь rollback plan:
- что возвращаем
- какие файлы
- какие зависимости затронуты

---

## 10) DONE CRITERIA
Изменение считается завершённым только если:
- есть CHANGE_PACKET с CHANGE_ID
- обновлённые файлы представлены полностью
- пройдена цепочка: READINESS_CHECK_CTL → VAL → QA → DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC
- регистрация/логирование выполнены

---
