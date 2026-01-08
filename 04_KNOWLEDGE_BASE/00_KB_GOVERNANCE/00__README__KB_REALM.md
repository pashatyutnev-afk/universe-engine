# KB REALM — README (CANON)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/00__README__KB_REALM.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: README
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.README.REALM.001
OWNER: SYSTEM
ROLE: Описание слоя Knowledge Base и правила входа

---

## PURPOSE
KB — слой знаний, правил и практик для Universe Engine.

---

## SINGLE ENTRYPOINT (ABSOLUTE)
Единственная точка входа в KB:
- `00__INDEX__KNOWLEDGE_BASE.md`
- UID: UE.KB.IDX.MASTER.001

Вся навигация по файлам, любые списки существования и любые “куда перейти” — только там.

---

## WHAT YOU CAN DO HERE
- Хранить правила, словари и контрольные документы KB.
- Поддерживать стандарты оформления и контроля.
- НЕ вводить существование (это делает только главный индекс).

---

## HARD BANS (REMINDER)
Запрещено:
- создавать под-индексы/локальные реестры (topics-index, entities-index и т.п.)
- вставлять PATH/RAW/URL ссылки (в любые документы кроме главного индекса)
- делать “цепочку навигации” документ → документ → документ

Разрешено:
- XREF на документ по UID без ссылок:
  `XREF: <UID> | WHY: <reason>`

---

## GOVERNANCE SET (WHAT IS INSIDE)
Этот realm содержит:
- RULES / MAP / FLOW / CONTROL
- системные словари: TAGS / REL TYPES / XREF RULES
- шаблоны документов

Все эти документы — контент-правила.
EXISTENCE и NAV — только главный индекс.

--- END.
