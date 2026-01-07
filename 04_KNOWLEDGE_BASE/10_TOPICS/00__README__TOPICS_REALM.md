# TOPICS REALM — README (CANON)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/99__README__TOPICS_REALM.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: README
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TOPICS.README.001
OWNER: SYSTEM
ROLE: How to use Topics subtree + rules for topic content boundaries

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Topics subtree introduced: rules, purpose, and workflow."
- REASON: "Need expandable KB articles without breaking realms."
- IMPACT: "KB authorsing workflow"

---

## WHAT IS TOPICS
`10_TOPICS` — это KB-статьи/пакеты по конкретным темам.
Они:
- расширяют realms (но не дублируют их)
- живут отдельными файлами
- всегда имеют XREF на realm-источник

---

## CANON ENTRY
- Existence всего subtree определяется индексом:
  `04_KNOWLEDGE_BASE/10_TOPICS/00__INDEX__TOPICS.md`

---

## RULES (HARD)
- Topic = один фокус. Если больше 1 фокуса — дели.
- Любой пересекающийся смысл → XREF вместо копирования.
- Topic обязан иметь XREF на основной realm (если тема “из realm-а”).
- Нумерация в папке уникальна. Meta-доки в 00/99, topic-файлы в 01..99.

--- END.
