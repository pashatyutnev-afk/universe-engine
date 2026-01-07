# MASTER INDEX — UNIVERSE ENGINE (GLOBAL MAP)
FILE: 02_STANDARDS/02__MASTER_INDEX__UNIVERSE_ENGINE.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: INDEX
INDEX_TYPE: GLOBAL_MASTER_MAP
LEVEL: L0
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.IDX.GLOBAL.MASTER.001
OWNER: SYSTEM
ROLE: Global canonical map of the repo: official entrypoints to all layers + existence roots (single navigation start)

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MINOR
- SUMMARY: "Создан канонический глобальный master-index с Doc Control шапкой и стабильными entrypoints; подготовлено для полной перестройки индексов"
- REASON: "Нужен один глобальный навигационный старт + устранение 00__ коллизий в 02_STANDARDS"
- IMPACT: "Единая карта проекта, удобная точка входа"

---

## 0) PURPOSE (LAW)
Этот документ — глобальная карта Universe Engine: **куда идти** и **что является entrypoint**.

Правило:
- Этот файл НЕ дублирует содержимое слоёв.
- Он даёт только канонические входные точки (entrypoints) и их raw-ссылки.

---

## 1) GLOBAL ENTRYPOINTS (CANON)

### 00_INDEX (Repo root entrypoints)
- ROOT INDEX
  PATH: `00_INDEX/00__ROOT_INDEX.md`
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/00_INDEX/00__ROOT_INDEX.md

- REPO TREE (structure map)
  PATH: `00_INDEX/01__REPO_TREE__UNIVERSE_ENGINE.md`
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/00_INDEX/01__REPO_TREE__UNIVERSE_ENGINE.md

---

### 01_SYSTEM_LAW (Core system laws)
- SYSTEM LAW MASTER INDEX
  PATH: `01_SYSTEM_LAW/00__INDEX__SYSTEM_LAW.md`
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__INDEX__SYSTEM_LAW.md

- CORE LAW (highest authority inside layer)
  PATH: `01_SYSTEM_LAW/00__SYSTEM_LAW.md`
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__SYSTEM_LAW.md

---

### 02_STANDARDS (Standards / Specs / Protocols / Templates)
- STANDARDS MASTER INDEX (entrypoint)
  PATH: `02_STANDARDS/00__INDEX__STANDARDS.md`
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/00__INDEX__STANDARDS.md

- DOC REGISTRY (SoT registry)
  PATH: `02_STANDARDS/01__DOC_REGISTRY.md`
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01__DOC_REGISTRY.md

---

### 03_SYSTEM_ENTITIES (System entities: ENG/ORC/SPC/CTL/VAL/QA + registries/templates)
- SYSTEM ENTITIES README
  PATH: `03_SYSTEM_ENTITIES/00__README__SYSTEM_ENTITIES.md`
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00__README__SYSTEM_ENTITIES.md

- SYSTEM ENTITIES INDEX
  PATH: `03_SYSTEM_ENTITIES/02__INDEX__SYSTEM_ENTITIES.md`
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/02__INDEX__SYSTEM_ENTITIES.md

- ENG (Engines) GLOBAL REGISTRY
  PATH: `03_SYSTEM_ENTITIES/10_ENG__ENGINES/02__INDEX_ALL_ENGINES.md`
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/02__INDEX_ALL_ENGINES.md

---

### 04_KNOWLEDGE_BASE (KB layer)
- KB MASTER INDEX (entrypoint)
  PATH: `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md

---

### 05_PROJECTS (Project layer)
- PRJ Governance README
  PATH: `05_PROJECTS/00_PRJ_GOVERNANCE/00__README__PRJ_REALM.md`
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/05_PROJECTS/00_PRJ_GOVERNANCE/00__README__PRJ_REALM.md

---

### 06_ASSETS (Assets layer)
- AST Governance README
  PATH: `06_ASSETS/00_AST_GOVERNANCE/00__README__AST_REALM.md`
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/06_ASSETS/00_AST_GOVERNANCE/00__README__AST_REALM.md

---

### 08_DATABASES (Databases)
- DB ENTITY TYPES
  PATH: `08_DATABASES/DB__ENTITY_TYPES.md`
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/08_DATABASES/DB__ENTITY_TYPES.md

- DB DOC REGISTRY
  PATH: `08_DATABASES/DB__DOC_REGISTRY.md`
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/08_DATABASES/DB__DOC_REGISTRY.md

---

## 2) EXISTENCE NOTE (STRICT)
Этот файл — глобальная карта.  
Existence rules живут в master-index каждого слоя (например `01_SYSTEM_LAW/00__INDEX__SYSTEM_LAW.md`, `02_STANDARDS/00__INDEX__STANDARDS.md`, `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`).

---

## FINAL RULE (LOCK)
LOCK: FIXED
--- END.
