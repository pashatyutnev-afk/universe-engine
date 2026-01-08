# KB DOC CONTROL (CANON)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/07__KB_DOC_CONTROL.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: CONTROL
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.CTRL.DOC.001
OWNER: SYSTEM
ROLE: Стандарты документов KB: шапка, статусы, версии, запреты на ссылки

---

## PURPOSE (LAW)
Задает стандарт оформления и контроля документов KB.
Фиксирует запрет на промежуточные ссылки/навигацию вне главного индекса.

---

## MANDATORY HEADER (MUST)
Каждый KB документ обязан иметь шапку:

- SCOPE
- LAYER
- DOC_TYPE
- LEVEL
- STATUS
- LOCK
- VERSION
- UID
- OWNER
- ROLE

---

## STATUS (ENUM)
Допустимые значения:
- DRAFT
- ACTIVE
- DEPRECATED
- ARCHIVED

---

## LOCK (ENUM)
- OPEN — допускает правки
- FIXED — правки только через осознанный апдейт версии и CHANGE_NOTE (если используется)

---

## VERSIONING
- Семвер: `X.Y.Z`
- Любое изменение смысла/правил → повышает MINOR или MAJOR (на усмотрение оператора)
- Мелкие правки/опечатки → PATCH

---

## UID (RULE)
UID должен быть:
- уникальный
- стабильный
- читаемый
- не зависеть от пути/ссылок

---

## LINK POLICY (HARD BAN)

### LP1 — Main Index is the only navigation surface
Единственный документ, где разрешены навигационные ссылки (PATH/RAW/URL):
- `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`

### LP2 — Everywhere else: NO LINKS
Во всех остальных документах запрещены:
- PATH/RAW/URL на файлы репозитория
- “перейди/открой” через ссылки
- любые “цепочки навигации”

Разрешено:
- XREF по UID без URL:
  `XREF: <UID> | WHY: <reason>`

---

## INDEX POLICY (HARD BAN)
Запрещены любые под-индексы/локальные реестры существования/навигации.
Если где-то появляется “topics index / entities index / registry” — это нарушение и файл удаляется.

Допускаются governance-словари внутри `00_KB_GOVERNANCE`,
но они НЕ являются навигацией и НЕ определяют существование.

---

## ALIAS POLICY
Алиасы (98/99) — только pointer на главный индекс, без контента.

---

## CANON ENFORCEMENT
- Файл каноничен только если он зарегистрирован в главном индексе.
- Иначе: NON-CANON / ignored.

--- END.
