# TOPIC — KB EXCERPTING & MEMORY REUSE RULES (META / OPERATIONAL)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/80_META/03__META__KB_EXCERPTING_AND_MEMORY_REUSE_RULES.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TOPIC
INDEX_TYPE: META_POLICY
LEVEL: L2
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.TOPIC.META.EXCERPT.MEMORY.003
OWNER: SYSTEM
ROLE: Define strict rules for excerpting KB content and reusing it from memory without drift: what is allowed, forbidden, how to reference, and hard fail conditions; includes KB_SOURCES + MEMORY_REUSE formats

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created excerpting and memory reuse policy: allowed transformations, forbidden drift, trace rules, and hard fail conditions."
- REASON: "The largest quality failure mode is paraphrase drift; strict excerpt and memory rules keep KB deterministic."
- IMPACT: "Entities can reuse knowledge safely, keep outputs consistent, and avoid inventing unseen details."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPIC.META.003

---

TYPE: type_topic
STATE: UNREAD
TAGS:
- domain_meta
- knowledge_base
- excerpting
- memory_reuse
- anti_drift
- traceability
- maturity_seed

---

## 1) PURPOSE
Зафиксировать, как сущности используют KB:
- когда можно **цитировать/выписывать**,
- когда можно **использовать память**,
- какие преобразования допустимы,
- какие случаи = HARD FAIL.

---

## 2) DEFINITIONS (STRICT)
### Excerpting
Вынести из KB модуля часть содержания (правило/шаг/шаблон) в deliverable.

### Paraphrase drift
Сдвиг смысла при пересказе: добавили/убрали/поменяли условия.

### Memory reuse
Использование ранее прочитанного KB без повторного открытия, при гарантии “смысл неизменён”.

---

## 3) EXCERPTING RULES (ALLOWED / FORBIDDEN)
### Allowed excerpt types
- A1: Copy block (вставить кусок как есть)
- A2: Bullet extraction (переписать списком без изменения смысла)
- A3: Parameterization (заменить параметры на значения задачи)
  Пример: “hook ≤ 0:15” → “hook ≤ 0:12 для этого трека”
- A4: Ordering (упорядочить шаги, если порядок в KB не меняется)

### Forbidden
- F1: Добавлять новые правила, которых нет в модуле
- F2: Убирать условия/пороги так, что метод меняется
- F3: Смешивать два разных модуля без указания обоих в KB_SOURCES
- F4: “Оптимизировать” метод без KB-основания

---

## 4) MEMORY REUSE RULES (STRICT)
### Allowed memory reuse
Только если:
- MR1: модуль был ранее открыт и применён
- MR2: используется тот же метод без новых деталей
- MR3: указано MEMORY_REUSE: YES в KB_SOURCES

### Forbidden memory reuse
- MRF1: если модуль не открывался ранее
- MRF2: если задача high-stakes и требуется точное правило
- MRF3: если есть сомнение в точности → нужно открыть RAW снова
- MRF4: если добавляются детали “из головы”

---

## 5) TRACE FORMAT (MANDATORY)
Каждый deliverable, который использует KB, обязан иметь:

KB_SOURCES:
- PATH: <module_path> — used for <what>
- PATH: <module_path> — used for <what>
MEMORY_REUSE: YES/NO
EXCERPT_MODE: COPY_BLOCK | BULLET_EXTRACT | PARAMETERIZED | MIXED

Rules:
- перечислять все реально использованные модули
- если использовалась память: указать какие модули memory-based

---

## 6) EXCERPT QUALITY CHECK (ANTI-DRIFT)
Перед публикацией ответа:
- Q1: смысл совпадает с исходным правилом?
- Q2: пороги/условия не ослаблены?
- Q3: не добавлено “новых советов”?
- Q4: trace присутствует?

Если хотя бы один NO → REWORK или HARD STOP.

---

## 7) “SAFE PARAMETERIZATION” STANDARD
Можно менять:
- значения (числа/лимиты), если модуль это допускает
- имена/поля шаблона под задачу
- примеры под задачу

Нельзя менять:
- структуру метода (шаги)
- критерии PASS/FAIL
- existence/RAW-only принципы

---

## 8) HIGH-STAKES TRIGGER (FORCE RAW)
Если задача:
- юридическая/медицинская/финансовая
- или системные законы/контрольные протоколы
- или спор по версии/правилам
→ memory reuse запрещён, надо открыть RAW заново (или подтвердить через индекс).

---

## 9) HARD FAIL CONDITIONS
FAIL IF:
- нет KB_SOURCES
- MEMORY_REUSE: YES без основания
- excerpt изменил смысл (drift)
- добавлены новые правила “от себя”
- использована память при high-stakes trigger

---

## 10) EXAMPLES (MANDATORY)
### 10.1 PASS example
Взяли из hook engineering:
- “hook ≤ 0:15”
И параметризовали:
- “hook ≤ 0:12”
Trace:
- указан модуль + EXCERPT_MODE: PARAMETERIZED
WHY PASS:
- метод тот же, изменён только параметр.

### 10.2 FAIL example
Добавили “ещё 5 правил”, которых нет в KB.
WHY FAIL:
- F1 invention / drift.

---

## 11) RELATED (PATH ONLY)
REL:
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/80_META/01__META__KNOWLEDGE_BASE_USAGE_PROTOCOL.md
- REL: depends_on -> PATH: 04_KNOWLEDGE_BASE/10_TOPICS/80_META/02__META__KB_INDEX_NAVIGATION_STANDARD.md

---

## 12) COMPLIANCE
- TRACE: mandatory
- NO_DRIFT: absolute
- MEMORY_REUSE: controlled by MR rules
- HIGH_STAKES: force RAW

--- END.
