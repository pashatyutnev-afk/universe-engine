# KB XREF RULES (SYSTEM)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/92__KB_XREF_RULES

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_SYSTEM
SYSTEM_OBJ: XREF_RULES
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.SYS.XREF_RULES.001
OWNER: SYSTEM
ROLE: Canonical rules for cross-references (XREF) inside KB: formatting, when to use, and anti-duplication enforcement

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Зафиксированы правила XREF: формат, обязательность при пересечениях, запрет дублей"
- REASON: "Без XREF люди копируют текст между realms/topics и канон расползается"
- IMPACT: "KB realms, topics, passports, registry hygiene"

---

## PURPOSE (LAW)
Этот документ задаёт как оформлять ссылки (XREF) в KB.

---

## WHEN XREF IS MANDATORY
XREF обязателен, если:
- тема упоминается в 2+ местах (realms/topics)
- есть риск дублирования одного смысла
- документ опирается на другой документ как на источник

---

## XREF FORMAT (STANDARD)
Оформляй так (строго):

`XREF: <TARGET> | WHY:<short>`

Где `<TARGET>`:
- предпочтительно PATH внутри репо
- UID допускается, если так быстрее

Примеры:
- `XREF: 04_KNOWLEDGE_BASE/01__NARRATIVE_CRAFT | WHY:realm overview and gates`
- `XREF: UE.KB.SYS.REL_TYPES.001 | WHY:allowed REL list`

---

## LINK POLICY (NO COPY)
- XREF используется вместо копирования текста.
- Если нужно повторить правило — в текущем документе только 1 строка summary + XREF на источник.

---

## BIDIRECTIONAL RULE (RECOMMENDED)
Если topic зависит от realm:
- topic → XREF на realm (обязательно)
- realm → ссылка на topic (желательно, в секции “Topics / Links”)

---

## XREF QUALITY RULES
- WHY обязателен и короткий (до 120 символов)
- не делай XREF “ради красоты”
- если XREF больше 12 на документ — значит документ слишком широкий, дели

---

## FINAL RULE (LOCK)
Этот документ — SoT по XREF правилам KB слоя.
--- END.
