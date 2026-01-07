# KNOWLEDGE BASE (KB) — RULES
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md

SCOPE: Universe Engine / Knowledge Base Rules
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Правила создания и ведения KB-сущностей. Анти-дубли. Связи. Обязательные поля.

---

## 0) CORE LAW
- UID обязателен и является единственным идентификатором.
- Сущность без регистрации в KB Global Registry считается недействительной.
- Дубли сущностей запрещены (S0).

---

## 1) UID FORMAT (KB)
Единый формат системы:
`UE.<GLOBAL>.<CATEGORY>.<FAMILY>.<NAME>`

Для KB:
- GLOBAL = KB
- CATEGORY = тип сущности (CHR/LOC/OBJ/EVT/SYS/FACT/CONCEPT/REL/ARC/STYLE…)
- FAMILY = доменное семейство (WORLD/NAR/VIS/SND/GOV/GEN/…)
- NAME = UPPER_SNAKE_CASE

Пример:
`UE.KB.CHR.GEN.VITA`

---

## 2) REQUIRED PASSPORT FIELDS (MINIMUM)
Каждый KB-файл обязан содержать:
- UID
- STATUS / LOCK / VERSION
- SUMMARY (1–5 строк)
- TAGS (опционально)
- XREFS (опционально)
- DEPENDS_ON (если есть)

---

## 3) ANTI-DUPLICATION LAW
Перед созданием новой сущности:
- проверить KB Global Registry
- проверить похожие NAME/семейства
Если нашли дубль → создаём XREF на существующую, не плодим копии.

---

## 4) LINKS & DEPENDENCIES
- XREF/XREFS — для навигации и контекста
- DEPENDS_ON — только если “без этого сущность не может быть определена”

---

## 5) STATUS POLICY
- ACTIVE — используется
- DRAFT — в разработке
- DEPRECATED — заменена
- ARCHIVED — историческое, не менять

---

## 6) CHANGE POLICY
Если меняется структура/контракт сущности:
- VERSION повышается
- фиксируется в реестре (NOTES)

---
END.
