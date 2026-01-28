# PILLAR — REFERENCE & GLOSSARY (FOUNDATION TOME)
FILE: 04_KNOWLEDGE_BASE/01_PILLARS/09__PILLAR__REFERENCE_GLOSSARY.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: PILLAR
INDEX_TYPE: FOUNDATION_TOME
LEVEL: L2
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.PILLAR.REFERENCE.001
OWNER: SYSTEM
ROLE: Foundational reference system: canonical definitions, glossary discipline, term stability, and cross-linking rules; enables deterministic understanding across all entities and prevents semantic drift

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Initialized Reference & Glossary pillar as foundation tome skeleton for term discipline and semantic stability."
- REASON: "Universal KB requires stable meanings; terms must not drift across entities and docs."
- IMPACT: "Entities can align on definitions; conflicts are handled via canonical terms list and XREF maps."
- CHANGE_ID: UE.CHG.2026-01-14.KB.PILLAR.REF.001

---

## 0) PURPOSE (WHAT THIS PILLAR GIVES)
Этот PILLAR задаёт фундамент “СПРАВОЧНИК И ГЛОССАРИЙ”:
- как фиксировать определения терминов,
- как предотвращать семантический дрейф (“слово значит разное у разных сущностей”),
- как связывать термины с модулями KB (topics/policies/templates),
- как разрешать конфликты терминов.

Детальные списки терминов и конкретные определения хранятся в:
- TOPICS/REFERENCE (атомарные определения),
- RELATION_XREF (канонические списки и карты терминов, если нужно),
- GLOSSARY файл в стандартах/словарях (если существует).

---

## 1) SOURCE-LOCK / NO FANTASY (ABSOLUTE)
- Определения не придумываются “по ощущению”.
- Каждый термин должен иметь:
  - источник (KB module / standard / policy),
  - границы (что включает/что не включает),
  - примеры употребления (PASS/FAIL контекста).

Если нет источника — термин маркируется UNKNOWN и не используется как нормативный.

---

## 2) CORE PRINCIPLES (FOUNDATION)
### P1) One term = one meaning (within system)
Термин должен иметь одно фиксированное значение в рамках системы.

### P2) Meaning stability beats convenience
Нельзя менять смысл терминов ради удобства.

### P3) Definitions must be operational
Определение должно помогать действовать/проверять, а не “красиво звучать”.

### P4) Boundaries prevent confusion
Любой термин должен иметь границы: что входит и что точно не входит.

### P5) Examples anchor meaning
Примеры правильного/неправильного употребления закрепляют смысл.

### P6) Synonyms are controlled
Синонимы допускаются только как alias, но с указанием канонического термина.

### P7) Conflicts must be explicit
Если термин конфликтует (разные школы/источники) — маркируем DISPUTED и фиксируем policy/решение.

---

## 3) HIGH-LEVEL PROCEDURES (HOW TO DEFINE TERMS)
### Proc A) Define a term (canonical)
1) Запиши термин (строка).
2) Дай краткое определение (1–2 предложения).
3) Определи границы:
   - includes
   - excludes
4) Дай 1–2 примера корректного применения.
5) Дай 1 пример некорректного применения.
6) Привяжи к источникам (PATH):
   - источник нормы (policy/standard/topic)
7) Если есть синонимы — оформи alias и укажи canonical term.

### Proc B) Resolve term conflict
1) Зафиксируй два значения.
2) Проверь, не разные ли это термины под одним словом.
3) Если разные — раздели на два термина (разные names).
4) Если один термин должен быть единым — выбери канон через governance/policy.
5) Обнови карты и ссылки, чтобы смысл стал единым.

### Proc C) Prevent drift
1) Любое использование термина в документах должно ссылаться на canonical definition (PATH).
2) Если документ использует термин в новом смысле — STOP и исправление.

---

## 4) QUALITY FRAME (WHAT “GOOD” LOOKS LIKE)
Система терминов считается качественной, если:
- определения однозначны и операциональны,
- границы терминов прописаны,
- есть примеры применения,
- alias-система контролируемая,
- конфликты терминов явные и разрешаются policy/решением,
- сущности используют канонические определения через ссылки.

---

## 5) COMMON FAILURE MODES (ANTI-PATTERNS, HIGH LEVEL)
### F1) “Floating term”
Термин используется, но никто не знает что он значит.

### F2) “Semantic drift”
Термин постепенно меняет смысл между документами/сущностями.

### F3) “Definition without boundaries”
Определение настолько широкое, что не отличает термин от соседних.

### F4) “Synonym chaos”
Много синонимов без канонического термина → невозможно искать и проверять.

### F5) “Hidden conflict”
В системе две школы определения, но конфликт не отмечен → постоянные споры и ошибки.

---

## 6) REQUIRED CONNECTIONS (WHERE DETAILS LIVE)
Список целевых ссылок (PATH) на будущие TOPICS/LIBRARIES и карты.

### TOPICS (to create in 10_TOPICS/90_REFERENCE/)
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/90_REFERENCE/TOPIC__CANON_TERMS_DEFINITION_FORMAT.md
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/90_REFERENCE/TOPIC__TERM_BOUNDARIES_INCLUDES_EXCLUDES.md
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/90_REFERENCE/TOPIC__ALIAS_SYNONYM_POLICY.md
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/90_REFERENCE/TOPIC__SEMANTIC_DRIFT_PREVENTION.md

### SHARED LIBRARIES (to create)
#### Templates
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/30_TEMPLATES/TPL__TERM_DEFINITION_CARD.md
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/30_TEMPLATES/TPL__GLOSSARY_ENTRY.md

#### Rubrics
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/20_RUBRICS/RUBRIC__TERM_CLARITY.md

#### Checklists
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/10_CHECKLISTS/CL__TERM_USAGE_AUDIT.md

### RELATION / XREF MAPS
- PATH: 04_KNOWLEDGE_BASE/40_RELATION_XREF/04__GLOSSARY_CANON_TERMS.md

---

## 7) ENTITY USAGE (HOW ENTITIES SHOULD CONSUME THIS)
Сущности подключают этот PILLAR через KB_SOURCES:
- чтобы использовать термины строго по канону,
- чтобы не создавать новые значения без governance,
- чтобы маркировать неопределённость и конфликты явно.

---

## 8) NEXT EXPANSION (CONTROLLED)
Расширение допускается только:
- добавлением принципов/процедур верхнего уровня,
- добавлением ссылок на новые TOPICS/LIBRARIES/карты,
- без превращения PILLAR в “словарь всех терминов” (термины должны жить в атомарных модулях и картах).

Все изменения фиксируются в KB_CHANGELOG.

--- END.
