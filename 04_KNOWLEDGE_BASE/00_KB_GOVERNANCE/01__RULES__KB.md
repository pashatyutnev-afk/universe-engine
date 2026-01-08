# KB RULES (CANON)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: RULES
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.RULES.001
OWNER: SYSTEM
ROLE: Конституция Knowledge Base: existence, навигация, запреты

---

## PURPOSE (LAW)
Этот документ закрепляет неизменяемые правила работы Knowledge Base (KB).

---

## CORE LAWS (ABSOLUTE)

### L1 — ROOT (ONE MAIN FOLDER)
Единственный канонический root KB:
- `04_KNOWLEDGE_BASE/`

Подпапки внутри root допустимы только если они уже есть в KB и/или разрешены Storage Map.

### L2 — SINGLE INDEX (ONLY SoT)
Единственный канонический индекс (SoT по существованию и навигации):
- `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`

### L3 — EXISTENCE (ONLY IN MAIN INDEX)
Канон существует только по списку в главном индексе.
- Любой файл в репо, не перечисленный в главном индексе → NON-CANON / ignored.
- Никакие другие документы не могут “вводить” файлы в канон.

### L4 — NO SUB-INDEXES (HARD BAN)
Запрещены любые под-индексы и локальные реестры существования/навигации.
- Запрещено создавать “topics index”, “entities index”, “realm index”, “sub-index”, “registry” и т.п.
- Любой найденный sub-index должен быть удалён.

Допускаются governance-словари/справочники внутри `00_KB_GOVERNANCE` даже если в названии есть `INDEX`,
но они НЕ являются навигацией и НЕ могут определять существование.

### L5 — NO INTERMEDIATE LINKS (HARD BAN)
Навигационные ссылки на файлы разрешены ТОЛЬКО в главном индексе.

Запрещено во всех прочих документах:
- PATH-референсы как навигация
- RAW/URL ссылки на файлы/репозиторий
- “перейди сюда/открой то” через ссылки
- любые “цепочки навигации” (ссылка → ссылка → ссылка)

Разрешено:
- упоминать документ по NAME/UID (без PATH/RAW)
- использовать XREF в формате “UID + WHY”, без URL

### L6 — NO DELEGATION (HARD BAN)
Делегирование subtree запрещено.
- Нельзя писать “topics определяются другим индексом”.
- Нельзя использовать “existence SoT” кроме главного индекса.

---

## AUTHORITY MODEL (KB)
- Главный индекс определяет: EXISTENCE + NAV.
- Governance-доки определяют: нормы, форматы, жизненный цикл.
- Контент-доки (realms/topics) содержат знания и могут ссылаться только по UID (без ссылок).

---

## ENFORCEMENT CHECKLIST (OPERATOR)
Перед тем как коммитить изменения KB:
1) Нет ли новых sub-index файлов? (любой “index” вне governance/и любой локальный реестр) → удалить.
2) Нет ли PATH/RAW/URL ссылок в документах кроме главного индекса → удалить/заменить на UID.
3) Любой новый файл добавлен в главный индекс → иначе он NON-CANON.
4) Алиасы (если есть) содержат только pointer на главный индекс.

--- END.
