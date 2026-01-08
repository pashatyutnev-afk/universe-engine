# KB XREF RULES (DICTIONARY, CANON)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/92__KB_XREF_RULES.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: DICTIONARY
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.DICT.XREF_RULES.001
OWNER: SYSTEM
ROLE: Правила перекрёстных ссылок XREF (без URL/путей, только UID)

---

## PURPOSE
Закрепляет формат перекрёстных ссылок между документами KB без “промежуточной навигации”.

Главный принцип:
- Навигация по файлам (PATH/RAW/URL) разрешена только в главном индексе.
- Везде остальное — только UID.

---

## XREF FORMAT (MANDATORY)
- XREF: <UID> | WHY: <reason>

Пример:
- XREF: UE.KB.CTRL.DOC.001 | WHY: doc formatting and link bans

---

## WHEN TO USE XREF
Используй XREF, когда:
- документ опирается на правило/словарь/шаблон
- нужно указать “см. базовую норму”
- нужно явно связать темы, не создавая навигации по путям

---

## WHAT IS FORBIDDEN
Запрещено:
- URL на репозиторий/Raw
- PATH к файлу
- “перейди по ссылке”
- любые “цепочки ссылок”

---

## UID MENTION POLICY
Можно упоминать:
- UID
- имя документа (только name)
Но нельзя добавлять путь/ссылку.

--- END.
