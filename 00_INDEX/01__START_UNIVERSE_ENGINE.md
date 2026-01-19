# START_UNIVERSE_ENGINE

FILE: 01__START_UNIVERSE_ENGINE.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
DOC_TYPE: ENTRYPOINT (RUNBOOK)
MODE: REPO (USAGE-ONLY, NO-EDIT)
ROLE: Single launch point. Defines runtime order, entity hierarchy, routing, gates, and the duty to propose creation of missing entities.
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.1
UID: UE.GAMES.START.001
OWNER: SYSTEM

CHANGE_NOTE:
- DATE: 2026-01-19
- TYPE: PATCH
- SUMMARY: "Doc Control alignment + explicit boot confirmation gates + clarified snapshot/refresh handling."
- REASON: "Enforce boot-first discipline and remove ambiguity about whether standards/templates were loaded."
- IMPACT: "Runtime becomes auditable: boot gates explicit, stop conditions explicit, output contract stable."
- CHANGE_ID: UE.CHG.2026-01-19.START.001

---

## 0) PURPOSE (LAW)
Этот файл — единственный рабочий рантайм-энтрипоинт.  
ROOT-INDEX не выполняет задач, а даёт снимок RAW-ссылок.

---

## 1) INPUTS (MINIMUM)
Runtime запускается только командой пользователя:

- COMMAND: `START_UNIVERSE_ENGINE`
- ROOT LINK BASE: один файл-индекс со снимком RAW ссылок
- TASK: текст запроса пользователя
- OPTIONAL LINKS: любые дополнительные RAW ссылки, которые пользователь прислал в чате

### 1.1 ROOT LINK BASE (RAW)
- 00_INDEX / 00__ROOT_INDEX__UNIVERSE_ENGINE.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/00_INDEX/00__ROOT_INDEX__UNIVERSE_ENGINE.md

---

## 2) ABSOLUTE RUNTIME LAWS
2.1 RAW-only navigation
- Использовать только RAW ссылки, которые присутствуют:
  - в ROOT LINK BASE, или
  - в сообщении пользователя.
- Запрещено угадывать пути/файлы/URL вне базы.

2.2 Boot-first
- Нельзя выполнять задачу, пока не завершён BOOT SEQUENCE (раздел 5).

2.3 Single entrypoint for any task
- Любая задача начинается у Top Governance SPC и завершается проверочной цепочкой:
  - Start: `MACHINE_ARCHITECT_SPC`
  - Finish: `READINESS_CHECK_CTL` → relevant `VAL` → relevant `QA` → `DOC_CONTROLLER_SPC` → `MACHINE_ARCHITECT_SPC` signoff.

2.4 Missing entity duty
- Если для маршрута не хватает сущности (SPC/ORC/ENG/CTL/VAL/QA) или нет подходящего шаблона/дока — система обязана:
  - зафиксировать GAP,
  - предложить создание недостающей сущности/шаблона,
  - дать полный файл сущности по TEMPLATE,
  - только после этого продолжить задачу.

2.5 Output artifact rule
- Нельзя выпускать “голый контент”.
- Любой результат должен быть оформлен как документ-артефакт по стандартам/шаблонам подсистемы.
- Если шаблона нет — сначала GAP → предложение создания.

2.6 Mandatory response format (CHAT)
Каждый ран должен возвращать строго:
- MODE
- RESOURCES USED (USING RAW + MARKER FOUND)
- DELIVERABLES
- GATES

2.7 Stop conditions (only these)
- RAW missing
- marker not confirmed
- input absent

---

## 3) LINK BASE SNAPSHOT & MANUAL REFRESH (LAW)
- ROOT-INDEX — это снимок ссылок.
- Снимок не обновляется автоматически.
- Обновление происходит только вручную пользователем (пользователь присылает обновлённый ROOT-INDEX или отдельные RAW ссылки).
- Пока пользователь не обновил — набор ссылок считается фиксированным.

---

## 4) ENTITY HIERARCHY (WHO DOES WHAT)
SPC (Specialists)
- Владельцы намерения, решений и упаковки результата.
- Top governance SPC — диспетчеры, закон и финальное согласование.

ORC (Orchestrators)
- Пайплайны: порядок шагов и handoffs.

ENG (Engines)
- Детерминированная микрологика и методы.

CTL (Controllers)
- Политики, лимиты, блокировки, принудительные гейты.

VAL (Validators)
- Проверки соответствия и фиксация нарушений.

QA (Quality)
- Гейты приёмки, эталоны, скоринг, регрессия.

XREF (Crossref)
- Карты соответствий между сущностями и слоями, матрицы валидации, карты пайплайнов.

REG / DB / LOG
- Реестры, базы и журналы аудита/изменений.

---

## 5) BOOT SEQUENCE (MANDATORY ORDER)
BOOT = чтение ключевых законов/стандартов, без которых нельзя запускать выполнение.

### 5.1 Load System Law
- 01_SYSTEM_LAW / 00__INDEX__SYSTEM_LAW.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__INDEX__SYSTEM_LAW.md
- 01_SYSTEM_LAW / 00__SYSTEM_LAW.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__SYSTEM_LAW.md
- 01_SYSTEM_LAW / 01__NAMING_RULES.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/01__NAMING_RULES.md
- 01_SYSTEM_LAW / 02__UID_RULES.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md
- 01_SYSTEM_LAW / 03__VERSIONING_CHANGE_POLICY.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md
- 01_SYSTEM_LAW / 04__CANON_PROTOCOL.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/04__CANON_PROTOCOL.md

### 5.2 Load Standards for navigation + doc control
- 02_STANDARDS / 00_STANDARDS — MASTER INDEX.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/00_STANDARDS%20%E2%80%94%20MASTER%20INDEX.md
- 02_STANDARDS / 01_SPECIFICATIONS / 03__DOC_CONTROL_STANDARD.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
- 02_STANDARDS / 01_SPECIFICATIONS / 09__INDEX_STRUCTURE_SPEC.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/09__INDEX_STRUCTURE_SPEC.md
- 02_STANDARDS / 01_SPECIFICATIONS / 02__STORAGE_MAP_STANDARD.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/02__STORAGE_MAP_STANDARD.md
- 02_STANDARDS / 02_PROTOCOLS / 02__CHAT_PROTOCOL.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/02_PROTOCOLS/02__CHAT_PROTOCOL.md
- 02_STANDARDS / 02_PROTOCOLS / 01__CHANGE_MANAGEMENT_PROTOCOL.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/02_PROTOCOLS/01__CHANGE_MANAGEMENT_PROTOCOL.md

### 5.3 Load System Entities model + Templates indexes
- 03_SYSTEM_ENTITIES / 00__README__SYSTEM_ENTITIES.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00__README__SYSTEM_ENTITIES.md
- 03_SYSTEM_ENTITIES / 01__RULES__SYSTEM_ENTITIES.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/01__RULES__SYSTEM_ENTITIES.md
- 03_SYSTEM_ENTITIES / 02__INDEX__SYSTEM_ENTITIES.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/02__INDEX__SYSTEM_ENTITIES.md
- 03_SYSTEM_ENTITIES / 00_REG__REGISTRIES / 00__INDEX_ALL_REGISTRIES.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/00__INDEX_ALL_REGISTRIES.md
- 03_SYSTEM_ENTITIES / 01_TPL__TEMPLATES / 00__INDEX_ALL_TEMPLATES.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/00__INDEX_ALL_TEMPLATES.md

### 5.4 Load Knowledge Base entrypoint
- 04_KNOWLEDGE_BASE / 00__INDEX__KNOWLEDGE_BASE.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md
- 04_KNOWLEDGE_BASE / 00_KB_GOVERNANCE / 00__README__KB_REALM.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/00__README__KB_REALM.md
- 04_KNOWLEDGE_BASE / 00_KB_GOVERNANCE / 01__RULES__KB.md
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md

### 5.5 BOOT COMPLETE MARKER (REQUIRED)
BOOT считается завершённым только если явно подтверждено:
- Naming + UID rules loaded
- Doc Control + Index structure loaded
- Entity model loaded
- KB entrypoint loaded

Если любой пункт не подтверждён → STOP: marker not confirmed

---

## 6) TASK LIFECYCLE (DEFAULT PIPELINE)
1) INTAKE (MACHINE_ARCHITECT_SPC)
- цель, область, тип артефакта, минимальные входы

2) ROUTING (TOP GOVERNANCE SPC)
- назначение сущностей
- выбор ORC пайплайна

3) EXECUTION (ORC + ENG)
- черновики артефактов

4) CONTROL + VALIDATION (CTL + VAL)
- ограничения, нарушения, правки

5) QA (QA realm)
- гейты, скоринг, регресс

6) PACKAGING (INTEGRATION_PACKER_SPC)
- финальные файлы/пакеты, структура, названия

7) SIGNOFF (DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC)
- финальное согласование

---

## 7) TOP GOVERNANCE ENTRY LINKS (RAW)
- MACHINE_ARCHITECT_SPC
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/01__MACHINE_ARCHITECT_SPC.md
- GOVERNANCE_OWNER_SPC
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/02__GOVERNANCE_OWNER_SPC.md
- STANDARDS_OWNER_SPC
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/03__STANDARDS_OWNER_SPC.md
- DOC_CONTROLLER_SPC
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/04__DOC_CONTROLLER_SPC.md
- PIPELINE_ARCHITECT_SPC
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/05__PIPELINE_ARCHITECT_SPC.md
- INTEGRATION_PACKER_SPC
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00_TOP_GOVERNANCE/06__INTEGRATION_PACKER_SPC.md

---

## 8) CORE CONTROL + ACCEPTANCE LINKS (RAW)
- READINESS_CHECK_CTL
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__READINESS_CHECK_CTL.md

---

## 9) QUICK ROUTE MAP (DEFAULT WHEN AMBIGUOUS)
- rules/standards → STANDARDS_OWNER_SPC + DOC_CONTROLLER_SPC + change protocol
- new entity role → MACHINE_ARCHITECT_SPC + templates + registries
- pipelines → PIPELINE_ARCHITECT_SPC + ORC realm
- packaging/releases → INTEGRATION_PACKER_SPC + domain QA

---

## 10) RUNTIME OUTPUT (CHAT CONTRACT)
MODE:
RESOURCES USED (USING RAW + MARKER FOUND):
DELIVERABLES:
GATES:
