# RESEARCH & FACT CHECKING (KB REALM) (CANON)
FILE: 04_KNOWLEDGE_BASE/08_RESEARCH_FACT_CHECKING.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: REALM
REALM: RESEARCH_FACT_CHECKING
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.REALM.RESEARCH.108
OWNER: SYSTEM
ROLE: Knowledge realm for research and fact checking: how evidence is collected, evaluated, recorded, and promoted into KB canon. Defines confidence levels, citation formats, and external reference handling.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MAJOR
- SUMMARY: "Нормализован realm Research: Doc Control header + confidence levels + fact-check pipeline + EXTERNAL_REF format + rules of promotion to canon"
- REASON: "Чтобы факты не были 'на вере' и можно было проверять основание"
- IMPACT: "All research claims and KB canon truth"

---

## XREF (UID-first)
XREF: UE.KB.IDX.MASTER.001 | depends_on | KB existence and navigation | 04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md
XREF: UE.KB.GOV.RULES.011 | governs | KB canon and no-dup | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md
XREF: UE.STD.SPEC.REL_XREF.104 | depends_on | UID-first linking | 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md

---

## 0) PURPOSE
Этот realm задаёт:
- как мы исследуем утверждения
- как фиксируем источники и доказательства
- как назначаем уровень уверенности
- когда утверждение становится “фактом KB”
- как не плодить мифы/слухи как канон

---

## 1) DEFINITIONS
### 1.1 Claim
Claim — утверждение, требующее проверки.

### 1.2 Evidence
Evidence — данные/источник, который поддерживает или опровергает Claim.

### 1.3 KB Fact
KB Fact — утверждение, которое прошло проверку и получило достаточную уверенность (по правилам ниже).

---

## 2) CONFIDENCE LEVELS (CONTROLLED)
- C0 — Unknown (нет данных)
- C1 — Weak (1 источник низкой надёжности / косвенное)
- C2 — Moderate (несколько источников или один сильный)
- C3 — Strong (несколько независимых сильных источников)
- C4 — Verified (первичные источники/документы + независимое подтверждение)

Правило:
- ниже C2 — это НЕ “факт”, а “непроверенное утверждение”.

---

## 3) EXTERNAL REFERENCES (STANDARD)
Внешние источники не оформляются XREF строками (там UID нет).
Используем блоки `EXTERNAL_REF`.

Формат:
EXTERNAL_REF: <url>
- TYPE: <paper|book|archive|site|video|interview|dataset|...>
- DATE_ACCESSED: YYYY-MM-DD
- WHY: "<зачем нужен источник>"
- RELIABILITY: <low|medium|high>
- NOTES: "<коротко>"

---

## 4) RESEARCH RECORD (COPY TEMPLATE)
Используй этот формат для фиксации исследования:

RESEARCH_RECORD:
- CLAIM_ID: <local token>
- CLAIM: "<text>"
- TARGET: <what entity/scene/document it affects>
- CURRENT_CONFIDENCE: C0|C1|C2|C3|C4
- STATUS: open|resolved|deprecated
- EVIDENCE:
  - EXTERNAL_REF: <url> | REL: supports|contradicts | NOTE: "<...>"
  - EXTERNAL_REF: <url> | REL: supports|contradicts | NOTE: "<...>"
- CONCLUSION: "<what we believe now>"
- PROMOTION: <none|candidate|promoted>
- PROMOTION_NOTE: "<if promoted: where recorded as KB fact>"

---

## 5) FACT-CHECK PIPELINE (HOW TO PROMOTE TO CANON)
Step R0 — Define claim precisely
- переписать claim так, чтобы можно было доказать/опровергнуть

Step R1 — Collect evidence
- минимум 2 независимых источника желательно
- отмечать RELIABILITY

Step R2 — Assign confidence
- дать C0–C4 по шкале

Step R3 — Decide action
- если C0–C1: оставляем как open/unknown
- если C2–C3: можно использовать как рабочее знание, но помечать уровень
- если C4: можно продвигать в KB fact

Step R4 — Promote into KB
Если claim становится KB fact:
- внести факт в соответствующий паспорт сущности (если факт про сущность)
или
- внести в соответствующий realm как правило/утверждение
и обязательно:
- указать уровень уверенности
- добавить EXTERNAL_REF список

---

## 6) WHERE FACTS LIVE (PLACEMENT)
- Факты про сущность → в её KB passport (SoT)
- Методики/правила → в realm
- Список исследований/кейсов → можно держать внутри этого realm как журнал

---

## 7) ANTI-PATTERNS (FORBIDDEN)
- “я думаю” как факт
- отсутствие источников для сильных утверждений
- дублирование одного и того же исследования в разных местах без XREF/ссылки
- превращать внешние ссылки в XREF UID-first (это разные вещи)

---

## 8) LINKING TO ENTITIES (UID-FIRST)
Если исследование относится к внутренней сущности:
- ссылка на ENTITY_UID обязательна (как TARGET)

Pattern:
XREF:
- XREF: <ENTITY_UID> | references | "research target" | <passport-path(optional)>

---

## 9) RESEARCH JOURNAL (OPTIONAL)
> Здесь можно вести журнал исследований по датам.

YYYY-MM-DD
- CLAIM: ...
- CONF: C1
- NEXT: ...

---

## FINAL RULE (LOCK)
Факт становится каноном KB только после исследовательской фиксации и достаточной уверенности.
--- END.
