# PILLAR — RESEARCH & FACT CHECKING (FOUNDATION TOME)
FILE: 04_KNOWLEDGE_BASE/01_PILLARS/08__PILLAR__RESEARCH_FACT_CHECKING.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: PILLAR
INDEX_TYPE: FOUNDATION_TOME
LEVEL: L2
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.PILLAR.RESEARCH.001
OWNER: SYSTEM
ROLE: Foundational research and fact-checking craft: source hierarchy, evidence standards, uncertainty handling, verification procedures, and anti-misinformation controls; detailed methods live in TOPICS and quality instruments live in SHARED_LIBRARIES

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Initialized Research & Fact Checking pillar as foundation tome skeleton compatible with KB source-lock, no-fantasy, and usage gate."
- REASON: "System requires deterministic non-fiction handling; research must be auditable and uncertainty-aware."
- IMPACT: "Entities can ground outputs in evidence; unsupported claims are blocked or labeled; source quality becomes enforceable."
- CHANGE_ID: UE.CHG.2026-01-14.KB.PILLAR.RSCH.001

---

## 0) PURPOSE (WHAT THIS PILLAR GIVES)
Этот PILLAR задаёт фундамент “ИССЛЕДОВАНИЕ И ФАКТ-ЧЕК”:
- иерархию источников (каким доверять и почему),
- стандарты доказательств (что считается подтверждённым),
- работу с неопределённостью (как маркировать уверенность),
- процедуры проверки фактов и противоречий,
- защиту от дезинформации и “фантазии”.

Детальные техники (шаблоны заметок, чеклисты, матрицы оценок источника) — в TOPICS/LIBRARIES.

---

## 1) SOURCE-LOCK / NO FANTASY (ABSOLUTE)
- Никаких домыслов как фактов.
- Любое утверждение должно иметь статус:
  - VERIFIED (подтверждено источниками),
  - PLAUSIBLE (правдоподобно, но требует проверки),
  - UNKNOWN (нет данных),
  - DISPUTED (источники конфликтуют).
- Если нет источника → нельзя выдавать как факт.

---

## 2) CORE PRINCIPLES (FOUNDATION)
### P1) Evidence beats confidence
Уверенность не равна доказательству. Важны источники и проверка.

### P2) Primary sources > retellings
Первичные источники предпочтительнее пересказов.

### P3) Two independent confirmations (when possible)
Для критичных утверждений требуется минимум 2 независимых подтверждения.

### P4) Cite the claim, not the topic
Ссылки должны подтверждать именно утверждение, а не “в целом”.

### P5) Separate fact from inference
Факт и вывод разделяются. Вывод помечается как inference и зависит от фактов.

### P6) Handle conflicts explicitly
Если источники конфликтуют — помечаем DISPUTED и ищем разрешение.

### P7) Bias awareness
Источник может быть заинтересованным. Это не запрет, но требует контекста.

### P8) Scope control
Не расширять утверждение за рамки источника (“говорит про A” ≠ “доказывает B”).

---

## 3) SOURCE HIERARCHY (QUALITY LEVELS)
### Level A — Highest
- первичные документы/данные
- официальные спецификации/стандарты
- оригинальные исследования/публикации

### Level B — Strong
- авторитетные вторичные источники с ссылками на первичку
- академические обзоры/мета-аналитика (если применимо)

### Level C — Medium
- качественные статьи/книги без первички, но с репутацией автора

### Level D — Weak / contextual only
- блоги без источников
- слухи/форумы
- “пересказ пересказа”

Правило:
- Level D нельзя использовать как доказательство факта, только как “сигнал что надо проверить”.

---

## 4) HIGH-LEVEL PROCEDURES (HOW TO VERIFY)
### Proc A) Verify a factual claim
1) Сформулируй утверждение в одном предложении.
2) Определи что именно нужно доказать (ключевые элементы).
3) Найди первичные источники (Level A) если возможно.
4) Найди независимое подтверждение (второй источник).
5) Проверь дату/контекст/определения терминов.
6) Зафиксируй результат:
   - VERIFIED / DISPUTED / UNKNOWN
7) Запиши KB_SOURCES (PATH/RAW) и краткое “почему”.

### Proc B) Conflict resolution
1) Выпиши конфликтующие утверждения.
2) Проверь, не разные ли определения/контексты.
3) Проверь авторитетность источников (уровни).
4) Если конфликт остаётся — маркируй DISPUTED и укажи обе стороны.
5) Ищи первичку/данные, которые снимают конфликт.

### Proc C) Inference discipline
1) Отдели факты (с источниками).
2) Отдели выводы (логическая связка).
3) Маркируй выводы как inference.
4) Не увеличивай силу вывода (“возможно” ≠ “доказано”).

---

## 5) QUALITY FRAME (WHAT “GOOD” LOOKS LIKE)
Исследование считается качественным, если:
- каждое важное утверждение привязано к источнику,
- источники оценены по уровню,
- неопределённость маркирована (VERIFIED/DISPUTED/UNKNOWN),
- выводы отделены от фактов,
- конфликт источников обработан явно,
- нет расширения смысла за рамки источников.

---

## 6) COMMON FAILURE MODES (ANTI-PATTERNS, HIGH LEVEL)
### F1) “Confident hallucination”
Утверждение звучит уверенно, но без источников.

### F2) “Source laundering”
Слабый источник выдаётся как сильный (пересказ без первички).

### F3) “Cherry-picking”
Берём только подтверждающие факты, игнорируем противоречия.

### F4) “Scope inflation”
Источник говорит про частное, а вывод делается общий.

### F5) “Inference as fact”
Вывод выдаётся как подтверждённый факт.

---

## 7) REQUIRED CONNECTIONS (WHERE DETAILS LIVE)
Список целевых ссылок (PATH) на будущие TOPICS/LIBRARIES.

### TOPICS (to create in 10_TOPICS/90_REFERENCE/ or 10_TOPICS/.. as needed)
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/90_REFERENCE/TOPIC__SOURCE_HIERARCHY.md
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/90_REFERENCE/TOPIC__CLAIM_DECOMPOSITION.md
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/90_REFERENCE/TOPIC__CONFLICT_RESOLUTION.md
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/90_REFERENCE/TOPIC__FACT_VS_INFERENCE.md
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/90_REFERENCE/TOPIC__CITATION_DISCIPLINE.md
- PATH: 04_KNOWLEDGE_BASE/10_TOPICS/90_REFERENCE/TOPIC__UNCERTAINTY_LABELS.md

### SHARED LIBRARIES (to create)
#### Rubrics
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/20_RUBRICS/RUBRIC__SOURCE_QUALITY.md
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/20_RUBRICS/RUBRIC__FACT_CHECK_PASS.md

#### Checklists
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/10_CHECKLISTS/CL__FACT_CHECK_PREFLIGHT.md
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/10_CHECKLISTS/CL__CONFLICT_HANDLING.md

#### Templates
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/30_TEMPLATES/TPL__RESEARCH_NOTE.md
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/30_TEMPLATES/TPL__CLAIM_EVIDENCE_TABLE.md

#### Examples
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/50_EXAMPLES/EXAMPLE__RESEARCH_VERIFIED.md
- PATH: 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/50_EXAMPLES/EXAMPLE__RESEARCH_DISPUTED.md

---

## 8) ENTITY USAGE (HOW ENTITIES SHOULD CONSUME THIS)
Сущности подключают этот PILLAR через KB_SOURCES:
- как фундамент для non-fiction задач,
- оценку источников и проверки — через рубрики и чеклисты,
- выводы отделяют от фактов и маркируют уверенность.

---

## 9) NEXT EXPANSION (CONTROLLED)
Расширение допускается только:
- добавлением принципов/процедур верхнего уровня,
- добавлением ссылок на новые TOPICS/LIBRARIES,
- без переноса атомарных техник внутрь PILLAR.

Все изменения фиксируются в KB_CHANGELOG.

--- END.
