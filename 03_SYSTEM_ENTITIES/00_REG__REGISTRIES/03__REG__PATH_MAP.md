# REGISTRY — PATH MAP (UNIVERSE ENGINE) (CANON)
FILE: 03_SYSTEM_ENTITIES/00_REG__REGISTRIES/03__REG__PATH_MAP.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: REGISTRY
REGISTRY_TYPE: PATH_MAP
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.REG.PATH_MAP.003
OWNER: SYSTEM
ROLE: Source-of-Truth path map of the repository structure. Provides full tree snapshot and canonical entrypoints per layer.

---

## 0) PURPOSE
- показать всю структуру репо одним документом
- дать канонические entrypoints по слоям
- быть “снимком факта”: обновляется при изменении структуры

---

## 1) ENTRYPOINTS (CANON)
- ROOT: 00_INDEX/00__ROOT_INDEX.md
- SYSTEM LAW: 01_SYSTEM_LAW/00__INDEX__SYSTEM_LAW.md
- STANDARDS: 02_STANDARDS/00__INDEX__STANDARDS.md
- SYSTEM ENTITIES: 03_SYSTEM_ENTITIES/00_REG__REGISTRIES/00__INDEX__ALL_REGISTRIES.md
- KB: 04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md
- PROJECTS: 05_PROJECTS/00_PRJ_GOVERNANCE/...

---

## 2) FULL TREE SNAPSHOT (SoT)
> Обновляй этот блок при изменениях структуры.

00_INDEX/
  00__ROOT_INDEX.md
  ...

01_SYSTEM_LAW/
  00__INDEX__SYSTEM_LAW.md
  00__SYSTEM_LAW.md
  ...

02_STANDARDS/
  00__INDEX__STANDARDS.md
  00__DOC_REGISTRY.md
  00__MASTER_INDEX__UNIVERSE_ENGINE.md
  ...

03_SYSTEM_ENTITIES/
  00_REG__REGISTRIES/
    00__INDEX__ALL_REGISTRIES.md
    03__REG__PATH_MAP.md
    ...

04_KNOWLEDGE_BASE/
  00__INDEX__KNOWLEDGE_BASE.md
  00_KB_GOVERNANCE/
    ...
  ...

05_PROJECTS/
  ...

06_ASSETS/
  ...

99_LOGS/
  ...

---

## 3) CHANGE RULE
- Любая правка структуры папок/имен → обновить snapshot
- PATCH: добавил файл/папку
- MINOR: перестроение внутри слоя
- MAJOR: переносы/переименование entrypoints

--- END.
