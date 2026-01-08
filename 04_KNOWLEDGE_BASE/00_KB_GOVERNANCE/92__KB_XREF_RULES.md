# KB XREF RULES (DICTIONARY, CANON)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/92__KB_XREF_RULES.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: DICTIONARY
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.KB.DICT.XREF_RULES.001
OWNER: SYSTEM
ROLE: Canonical KB cross-reference rules (UID-only, no navigation)

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MINOR
- SUMMARY: "XREF made UID-only. Removed PATH/RAW/URL. Enforced WHY requirement."
- REASON: "Под закон KB: никакой навигации/промежуточных ссылок вне master-index."
- IMPACT: "All KB cross-references are stable and path-independent."

---

## PURPOSE (LAW)
Закрепляет формат перекрёстных ссылок (XREF) в KB без промежуточной навигации.

Ключевое:
- XREF НЕ содержит PATH/RAW/URL.
- XREF указывает только UID.
- WHY обязателен.

---

## FORMAT (ABSOLUTE)
Единственный допустимый формат:

XREF: <UID> | WHY: <reason>

RULES:
- WHY обязателен (конкретика, 1 строка).
- UID обязателен.
- Никаких путей, ссылок, raw, URL.

---

## WHEN TO USE XREF
Используй XREF, когда:
- нужно сослаться на правило/словарь/шаблон/реалм/топик
- нужно объявить зависимость или контекст, не создавая навигацию

---

## WHAT IS FORBIDDEN (HARD BAN)
Запрещено:
- URL любого вида
- RAW ссылки
- PATH как “куда перейти”
- “смотри документ X по ссылке”
- цепочки навигации документ → документ → документ

---

## NAVIGATION RULE (KB)
Навигация по файлам (PATH/RAW) разрешена только в:
- `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`

В любых других документах KB:
- только UID и WHY.

--- END.
