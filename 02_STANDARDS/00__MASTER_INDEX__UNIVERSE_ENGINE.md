# MASTER INDEX — UNIVERSE ENGINE (GLOBAL MAP)
FILE: 02_STANDARDS/00__MASTER_INDEX__UNIVERSE_ENGINE.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: INDEX
INDEX_TYPE: GLOBAL_MASTER_MAP
LEVEL: L0
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.2.0
UID: UE.IDX.GLOBAL.MASTER.001
OWNER: SYSTEM
ROLE: Global canonical map of the repo: official entrypoints to all layers + canonical entrypoints inside 02_STANDARDS

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: PATCH
- SUMMARY: "02_STANDARDS canonicalized: this file is the only entrypoint for 02_STANDARDS. Any other master-index filenames are aliases/pointers only. Removed footer meta duplication."
- REASON: "Убрать коллизии 00__/02__ и запретить паразитные master-index дублёры."
- IMPACT: "Один канонический master-index в 02_STANDARDS."

---

## 0) PURPOSE (LAW)
Этот документ — глобальная карта Universe Engine: куда идти и что является entrypoint.

Правило:
- Этот файл НЕ дублирует содержимое слоёв.
- Он даёт только канонические входные точки (entrypoints) и raw-ссылки.

---

## 1) GLOBAL ENTRYPOINTS (CANON)

### 00_INDEX
- ROOT INDEX
  PATH: `00_INDEX/00__ROOT_INDEX.md`
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/00_INDEX/00__ROOT_INDEX.md

- REPO TREE
  PATH: `00_INDEX/01__REPO_TREE__UNIVERSE_ENGINE.md`
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/00_INDEX/01__REPO_TREE__UNIVERSE_ENGINE.md

---

### 01_SYSTEM_LAW
- SYSTEM LAW MASTER INDEX
  PATH: `01_SYSTEM_LAW/00__INDEX__SYSTEM_LAW.md`
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__INDEX__SYSTEM_LAW.md

- CORE LAW
  PATH: `01_SYSTEM_LAW/00__SYSTEM_LAW.md`
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__SYSTEM_LAW.md

---

### 02_STANDARDS (THIS LAYER)
CANONICAL ENTRYPOINT (only):
- MASTER INDEX
  PATH: `02_STANDARDS/00__MASTER_INDEX__UNIVERSE_ENGINE.md`
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/00__MASTER_INDEX__UNIVERSE_ENGINE.md

- DOC REGISTRY (catalog, not SoT for NAV/EXISTENCE)
  PATH: `02_STANDARDS/01__DOC_REGISTRY.md`
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01__DOC_REGISTRY.md

02_STANDARDS TREE (official docs by folders):
- 00_CANON/*
- 01_SPECIFICATIONS/*
- 02_PROTOCOLS/*
- 03_TECHNICAL/*
- 04_TERMS_DEFINITIONS/*
- 05_REQUIREMENTS_TZ/*
- 06_MARKING_STANDARDS/*

---

### 03_SYSTEM_ENTITIES
- README
  PATH: `03_SYSTEM_ENTITIES/00__README__SYSTEM_ENTITIES.md`
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00__README__SYSTEM_ENTITIES.md

- INDEX
  PATH: `03_SYSTEM_ENTITIES/02__INDEX__SYSTEM_ENTITIES.md`
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/02__INDEX__SYSTEM_ENTITIES.md

---

### 04_KNOWLEDGE_BASE
- KB MASTER INDEX
  PATH: `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md

---

### 05_PROJECTS
- PRJ Governance README
  PATH: `05_PROJECTS/00_PRJ_GOVERNANCE/00__README__PRJ_REALM.md`
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/05_PROJECTS/00_PRJ_GOVERNANCE/00__README__PRJ_REALM.md

---

### 06_ASSETS
- AST Governance README
  PATH: `06_ASSETS/00_AST_GOVERNANCE/00__README__AST_REALM.md`
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/06_ASSETS/00_AST_GOVERNANCE/00__README__AST_REALM.md

---

### 08_DATABASES
- DB ENTITY TYPES
  PATH: `08_DATABASES/DB__ENTITY_TYPES.md`
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/08_DATABASES/DB__ENTITY_TYPES.md

- DB DOC REGISTRY
  PATH: `08_DATABASES/DB__DOC_REGISTRY.md`
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/08_DATABASES/DB__DOC_REGISTRY.md

---

## 2) ALIAS RULE (STRICT)
Любой файл вида:
- `02_STANDARDS/02__MASTER_INDEX__UNIVERSE_ENGINE.md`
- `02_STANDARDS/00__MASTER_INDEX_UNIVERSE_ENGINE.md`
и любые подобные “дублёры entrypoint”
должны быть либо удалены, либо превращены в чистый POINTER на этот документ.

--- END.
