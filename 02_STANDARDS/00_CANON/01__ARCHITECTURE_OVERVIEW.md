# ARCHITECTURE OVERVIEW (CANON)

FILE: 02_STANDARDS/00_CANON/01__ARCHITECTURE_OVERVIEW.md
SCOPE: Universe Engine
LAYER: 02_STANDARDS/00_CANON
DOC_TYPE: STANDARD
STANDARD_TYPE: ARCHITECTURE_OVERVIEW
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.1
UID: UE.STD.ARCH.OVERVIEW.001
OWNER: SYSTEM
ROLE: Canonical architecture overview of Universe Engine: layers, responsibilities, runtime entrypoints, navigation laws, and artifact governance.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "DOC CONTROL compliance cleanup + canonical structured overview (no meta duplication in body)."
- REASON: "Architecture overview must be auditable; forbidden meta repetition patterns removed."
- IMPACT: "Single source overview for system readers; stable onboarding reference."
- CHANGE_ID: UE.CHG.2026-01-20.STD.ARCH.OVERVIEW.001

---

## 0) PURPOSE (LAW)
Этот документ — обзор того, **как устроен Universe Engine** как система документации и рантайма.

Он отвечает:
- какие есть слои и зачем они;
- какие правила навигации обязательны;
- где “единственные точки входа”;
- как оформляется результат (артефакты) и как проходит контроль качества.

---

## 1) CORE PRINCIPLES (ABSOLUTE)

### 1.1 Single Source of Truth (SoT)
- У каждой области есть единственная “точка истины”:
  - ROOT-INDEX для базы RAW-ссылок (snapshot),
  - MASTER INDEX слоя для существования/состава внутри слоя,
  - стандарты для формата документов,
  - сущности для ролей и поведения.

### 1.2 RAW-only navigation (when enabled)
- Навигация выполняется только по RAW-ссылкам из:
  - ROOT-INDEX, и/или
  - явных ссылок, присланных пользователем в сообщении.
- Запрещено угадывать пути/файлы/URL.

### 1.3 Boot-first runtime
- Выполнение любой задачи возможно только после загрузки ключевых законов/стандартов/модели сущностей.

### 1.4 Output as artifacts
- Система не выпускает “голый контент”.
- Любой результат оформляется документом-артефактом по стандартам/шаблонам.

---

## 2) LAYER MODEL (WHAT LIVES WHERE)

### 2.1 00_INDEX
Назначение:
- entrypoints рантайма,
- ROOT link base (snapshot),
- центральные маршруты и quick start.

Типовые документы:
- ROOT INDEX (raw link base snapshot)
- START (entrypoint / runbook)

### 2.2 01_SYSTEM_LAW
Назначение:
- конституция системы, обязательные законы, которые выше любых стандартов/проектов.

Содержит:
- naming rules
- UID rules
- versioning & change policy
- canon protocol
- registries (artifact schema, constraints, pipeline registry)

### 2.3 02_STANDARDS
Назначение:
- стандарты структуры, форматов и протоколов.
- шаблоны (technical templates) для воспроизводимого выпуска документов/сущностей.

Содержит:
- CANON (архитектура, системный канон)
- SPECIFICATIONS (doc control, index structure, storage map и т.д.)
- PROTOCOLS (chat protocol, change management)
- TECHNICAL templates (entity passport, index template)

### 2.4 03_SYSTEM_ENTITIES
Назначение:
- модель ролей/сущностей (SPC/ORC/ENG/CTL/VAL/QA/XREF),
- шаблоны сущностей и индексы сущностей.

Содержит:
- realm readmes и rules
- registries + template registries
- сами сущности (каталоги по realm)

### 2.5 04_KNOWLEDGE_BASE
Назначение:
- структурированная база знаний:
  - governance,
  - pillars,
  - topics,
  - entity competence packs / connectors,
  - shared libraries.

### 2.6 05_PROJECTS
Назначение:
- работа над конкретными продуктами/линиями (проекты, воркшопы, output).
- L0 intake → L1 project → L2 canon → L3 output (если применяется).

### 2.7 06_ASSETS
Назначение:
- ассеты и их правила хранения/учёта (включая паспорта ассетов и индексы).

### 2.8 08_DATABASES
Назначение:
- базы и реестры данных (каталоги, типы, логи релизов и т.д.)
- структура данных отделена от стандартов/законов.

### 2.9 99_LOGS
Назначение:
- аудит и журнал изменений.

---

## 3) RUNTIME MODEL (WHO DOES WHAT)

### 3.1 Entity roles (high level)
- SPC: намерение/решения/упаковка результата.
- ORC: пайплайны и handoffs.
- ENG: детерминированные методы и микрологика.
- CTL: политики, лимиты, блокировки, принудительные гейты.
- VAL: проверки соответствия и фиксация нарушений.
- QA: гейты приёмки, эталоны, регресс.
- XREF: карты соответствий и матрицы проверок.

### 3.2 Task lifecycle (default)
1) Intake (MACHINE_ARCHITECT_SPC)
2) Routing (Top Governance SPC)
3) Execution (ORC + ENG)
4) Control + Validation (CTL + VAL)
5) QA (QA realm)
6) Packaging (INTEGRATION_PACKER_SPC)
7) Signoff (DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC)

---

## 4) NAVIGATION LAW (HOW TO READ SYSTEM)

### 4.1 ROOT-INDEX as snapshot
- ROOT-INDEX — снимок ссылок.
- Не обновляется автоматически.
- Обновляется только вручную пользователем.

### 4.2 START as single entrypoint
- Любая задача запускается только через START.
- ROOT-INDEX не выполняет задач.

---

## 5) ARTIFACT GOVERNANCE (OUTPUT RULES)

### 5.1 Artifact requirement
- Любой результат — это артефакт-документ по стандартам/шаблонам.
- Если нет подходящего шаблона — сначала GAP → предложение создания → полный файл сущности/шаблона.

### 5.2 Change control
- Изменения фиксируются через CHANGE_NOTE/CHANGE_ID.
- Применяются протоколы изменения и канонизации.

---

## 6) QUICK ONBOARDING (MINIMUM READ)
1) System Law: naming + UID + versioning + canon protocol  
2) Doc Control + Index Structure + Storage Map  
3) System Entities model + templates registry  
4) Knowledge Base entrypoint  
5) START runbook (runtime entrypoint)

---

## 7) END
