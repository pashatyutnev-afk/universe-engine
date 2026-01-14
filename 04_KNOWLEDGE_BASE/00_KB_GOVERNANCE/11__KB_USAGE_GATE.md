# KB USAGE GATE — ENFORCEMENT RULESET (ABSOLUTE)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/11__KB_USAGE_GATE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: RULE
INDEX_TYPE: ENFORCEMENT_GATE (KB)
LEVEL: L1
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.RULE.USAGE_GATE.001
OWNER: SYSTEM
ROLE: Enforce mandatory KB usage for all entity outputs; define evidence requirements (KB_SOURCES/KB_GATES/OUTPUT CONTRACT) and hard-stop conditions for non-compliance

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created KB usage gate: strict PASS/FAIL evidence requirements and hard-stop rules; forbids outputs without KB grounding."
- REASON: "KB is the main quality control plane; entities must not produce results without KB proof."
- IMPACT: "All runs become auditable; fantasy outputs blocked; KB becomes operationally mandatory."
- CHANGE_ID: UE.CHG.2026-01-14.KB.GATE.001

---

## 0) PURPOSE (LAW)
KB USAGE GATE — это обязательный контроль, который делает KB реальным механизмом качества.
Gate отвечает на вопрос:
- “Результат опирается на KB или это догадки?”

Если доказательств нет — результат считается FAIL и выполнение должно быть остановлено.

---

## 1) ABSOLUTE GATE RULE (PASS/FAIL)
### PASS (minimum)
Результат считается PASS только если присутствуют все элементы:

1) **KB_SOURCES (EVIDENCE)**
- перечислены KB источники, которые реально использованы
- указаны как PATH (RAW допускается дополнительно)

2) **KB_GATES (CHECKS APPLIED)**
- перечислены обязательные проверки (rubric/validator/qa/checklist/policy)
- указаны как PATH

3) **OUTPUT CONTRACT**
- указан шаблон результата (TPL__) или контракт формата
- указан как PATH

4) **NO-FANTASY COMPLIANCE**
- утверждения не выходят за рамки источников
- при сомнении — модуль переоткрывается или stop

### FAIL (hard)
Результат FAIL, если:
- нет KB_SOURCES
- нет KB_GATES
- нет OUTPUT CONTRACT (когда он обязателен по scope)
- обнаружены домыслы/фантазия без источника
- источники недоступны/неподтверждены

---

## 2) HARD STOP CONDITIONS (MANDATORY)
Выполнение обязано остановиться (HARD FAIL), если:
- RAW источник недоступен или битый (когда требуется чтение)
- требуемый модуль не открыт и нет Memory-OK уверенности
- обнаружена попытка “додумать” вместо чтения
- обнаружен конфликт правил без policy/решения

Запрещено продолжать “как будто gate пройден”.

---

## 3) EVIDENCE FORMAT (MANDATORY OUTPUT BLOCK)
Каждый run, который производит результат, обязан включить блок доказательств:

### KB_SOURCES
- REQUIRED:
  - PATH: ...
  - PATH: ...
- OPTIONAL:
  - PATH: ...

### KB_GATES
- Gate:
  - NAME: ...
  - PATH: ...
  - RESULT: PASS/FAIL/REWORK

### OUTPUT_CONTRACT
- PATH: ...

### COMPLIANCE
- SOURCE_LOCK: ON/OFF
- MEMORY_MODE: ON (VERIFIED only) / OFF

---

## 4) REQUIRED vs OPTIONAL SOURCES (RULE)
### REQUIRED
Источники, без которых результат нельзя корректно получить (нормы/политики/обязательные процедуры).

### OPTIONAL
Источники, которые улучшают качество, но не являются обязательными.

Правило:
- REQUIRED всегда перечисляются первыми.
- Если REQUIRED не использованы — FAIL.

---

## 5) SCOPE-BASED ENFORCEMENT (TASK / ENTITY)
Gate может требовать разный минимум KB scope в зависимости от:
- типа задачи (task→scope map)
- класса сущности (entity→scope map)

Правило:
- если task→scope или entity→scope требует конкретные модули/гейты — они обязаны быть в KB_SOURCES/KB_GATES, иначе FAIL.

---

## 6) REWORK STATES (CONTROLLED)
Если результат не PASS, допускается статус REWORK:
- когда есть KB_SOURCES, но не выполнены KB_GATES
- когда OUTPUT CONTRACT не соблюдён
- когда примеров/тестов недостаточно

REWORK означает:
- исправить и снова пройти KB_GATES
- обновить evidence block

---

## 7) ANTI-PATTERNS (FORBIDDEN)
Запрещено:
- “я использовал KB” без списка источников
- “это очевидно” вместо ссылок
- подмена KB источников “общими знаниями”
- выпуск результата при SOURCE_LOCK: OFF
- ссылаться на файлы, не зарегистрированные в master-index (оперативно их нет)

---

## 8) QUICK CHECK (FAST)
Gate считается пройденным если:
- я могу открыть каждый REQUIRED PATH,
- я вижу какие checks применены,
- я вижу какой шаблон результата использован,
- и результат не содержит ничего вне источников.

--- END.
