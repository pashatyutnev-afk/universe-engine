# KB STORAGE MAP (CANON)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/04__KB_STORAGE_MAP.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: MAP
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.MAP.STORAGE.001
OWNER: SYSTEM
ROLE: Разрешённая топология хранения KB (без навигационных ссылок)

---

## PURPOSE (LAW)
Определяет допустимую структуру хранения файлов KB внутри `04_KNOWLEDGE_BASE/`.
Этот документ НЕ является индексом и НЕ содержит навигационных ссылок на файлы (PATH/RAW).

---

## ROOT
- ROOT: `04_KNOWLEDGE_BASE/`

---

## ALLOWED ZONES (WHITELIST)

### Z0 — Governance
- Folder: `00_KB_GOVERNANCE/`
- Назначение: правила, словари, шаблоны, контроль документов.
- Внутри допускаются “INDEX” документы только как словари/справочники (не навигация и не existence).

### Z1 — Realms (Root-level content)
- Файлы в корне `04_KNOWLEDGE_BASE/` с диапазоном `01__...` — `08__...`
- Назначение: большие области знаний (realms).

### Z2 — Topics (Topic files)
- Folder: `10_TOPICS/`
- Назначение: конкретные темы/практики/гайдлайны.
- Запрещены любые под-индексы в этой папке.

### Z3 — Aliases (Legacy pointers)
- Файлы в корне `04_KNOWLEDGE_BASE/` с диапазоном `98__...` — `99__...`
- Назначение: только pointer на главный индекс (без контента).

---

## PROHIBITED (HARD BAN)

### P1 — Any sub-index as navigation/existence registry
Запрещено создавать любые локальные “index/registry” документы как навигацию/реестр существования
(включая внутри `10_TOPICS/`).

### P2 — Any navigation links outside main index
Запрещены PATH/RAW/URL ссылки в любых документах, кроме:
- `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`

### P3 — Unregistered files
Любой файл, не зарегистрированный в главном индексе → NON-CANON / ignored.

---

## CHANGE POLICY
Любое расширение карты хранения (новая папка/новая зона):
- допускается только как изменение governance (и должно быть отражено в главном индексе),
- но не должно вводить под-индексы и промежуточную навигацию.

--- END.
