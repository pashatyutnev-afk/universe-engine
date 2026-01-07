# TOPICS REALM — README (CANON)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/00__README__TOPICS_REALM.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
SUBTREE: 10_TOPICS
DOC_TYPE: README
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TOPICS.README.001
OWNER: SYSTEM
ROLE: Definition + rules of Topics subtree (how topics differ from realms, how to create and link)

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Topics subtree defined as KB article packs: narrow, reusable, cross-realm knowledge units."
- REASON: "Нужно отделить topics (атомарные статьи) от realms (канонические области)."
- IMPACT: "Creation flow + linking rules + existence delegation clarity"

---

## PURPOSE
`10_TOPICS` — это **атомарные статьи/пакеты знаний**, которые:
- узкие (1 тема = 1 файл),
- переиспользуемые между realms,
- не заменяют realms, а **подпитывают** их.

### TOPICS vs REALMS
- **REALMS (01..08)** = “области знания” (большие канонические документы-реалмы).
- **TOPICS (10_TOPICS/01..99)** = “атомарные модули” (конкретные техники/правила/паттерны/разборы).

---

## EXISTENCE RULE (HARD)
- Subtree `10_TOPICS` существует **только через**:
  `04_KNOWLEDGE_BASE/10_TOPICS/00__INDEX__TOPICS.md`
- Любой topic-файл, которого нет в `00__INDEX__TOPICS.md` = **NON-CANON / ignored**.

---

## NAMING (HARD)
Формат topic-файла:
`NN__DOMAIN__TOPIC_NAME.md`

DOMAIN фиксируем из набора (минимум):
- `NARRATIVE`
- `CHARACTER`
- `VISUAL`
- `SOUND`
- `PRODUCTION`
- `MARKETING`
- `GLOSSARY`
- `RESEARCH`

`00__*` зарезервировано под README/INDEX.

---

## TOPIC STRUCTURE (MINIMAL TEMPLATE)
Каждый topic должен иметь:
1) HEADER (Doc Control)
2) PURPOSE (что решает)
3) CORE RULES (пункты/правила)
4) EXAMPLES (минимум 1)
5) XREF / REL (ссылки на связанные topics/realms)

---

## LINKING RULES (MINIMAL)
- Если realm использует topic — realm обязан иметь XREF на topic.
- Если topic уточняет realm — topic обязан иметь XREF на realm.
- Дубли смысла запрещены: расширяй существующий topic или делай новый только если это реально другой смысл.

--- END.
