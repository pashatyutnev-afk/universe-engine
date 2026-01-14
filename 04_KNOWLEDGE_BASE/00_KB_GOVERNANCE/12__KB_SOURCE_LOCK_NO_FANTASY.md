# KB SOURCE-LOCK / NO FANTASY — ABSOLUTE EXECUTION LAW (KB)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/12__KB_SOURCE_LOCK_NO_FANTASY.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: RULE
INDEX_TYPE: SOURCE_LOCK_POLICY (KB)
LEVEL: L1
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.RULE.SOURCE_LOCK.001
OWNER: SYSTEM
ROLE: Absolute ban on invented knowledge; enforce strict source-locked usage of KB modules and controlled Memory-OK mode; defines hard-stop conditions

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created KB source-lock law: no-fantasy ban, source-first execution, memory rules, and hard-stop enforcement."
- REASON: "KB must remain factual and deterministic; prevents drift and hallucinated rules."
- IMPACT: "All entity outputs become auditable; any missing source triggers hard fail; Memory-OK becomes safe only for VERIFIED modules."
- CHANGE_ID: UE.CHG.2026-01-14.KB.SOURCELOCK.001

---

## 0) PURPOSE (LAW)
Этот документ запрещает фантазию и вводит строгий режим применения KB:
- любое знание должно быть привязано к источнику (source-locked),
- память допускается только как контролируемый режим (Memory-OK),
- при нарушении — hard stop.

---

## 1) ABSOLUTE BAN: NO FANTASY
Запрещено:
- придумывать правила/пороги/процедуры,
- добавлять “логически очевидные” детали,
- улучшать смысл источника,
- смешивать разные источники в одно “правило” без явного указания.

Любое утверждение в работе системы должно быть:
- либо прямым применением KB-источника,
- либо точным воспроизведением ранее открытого VERIFIED модуля (Memory-OK).

---

## 2) SOURCE-FIRST EXECUTION (ABSOLUTE)
Если модуль указан в KB_SOURCES как REQUIRED:
- модуль должен быть открыт по RAW (или доступен в текущем рабочем контексте),
- правило/процедура применяется строго как в источнике.

Запрещено:
- “вспоминать” UNREAD/READ_ONCE модуль без открытия,
- заменять чтение “логикой”.

---

## 3) MEMORY POLICY (CONTROLLED)
### 3.1 Memory-OK (allowed)
Память разрешена только если одновременно выполняется:
- модуль ранее открывался,
- модуль имеет состояние VERIFIED,
- смысл воспроизводится без изменений,
- нет противоречий с другими VERIFIED источниками.

### 3.2 Memory-NO (forbidden)
Запрещено использовать память если:
- модуль UNREAD или READ_ONCE,
- модуль изменялся после последнего применения (версии разные),
- есть сомнения в точности формулировки,
- есть конфликт норм.

### 3.3 Memory conflict rule
Если “память” и “текущий источник” расходятся:
- источник имеет приоритет,
- модуль должен быть переоткрыт и перепроверен,
- результат без переоткрытия — запрещён.

---

## 4) EVIDENCE REQUIREMENT (MANDATORY)
Любой результат обязан иметь доказательство:
- список KB_SOURCES (REQUIRED/OPTIONAL) в PATH формате,
- список KB_GATES (проверки) в PATH формате,
- указание режима:
  - SOURCE_LOCK: ON/OFF
  - MEMORY_MODE: ON (VERIFIED only) / OFF

Если SOURCE_LOCK: OFF → результат запрещён.

---

## 5) HARD STOP CONDITIONS (MANDATORY)
Выполнение должно остановиться (HARD FAIL), если:
- REQUIRED источник недоступен/битый,
- REQUIRED модуль не открыт и Memory-OK нельзя применить,
- обнаружена попытка “додумать”,
- обнаружено противоречие норм без policy/решения,
- ссылка ведёт на файл вне master-index (оперативно не существует).

---

## 6) SAFE COMPOSITION RULE (WHEN MULTIPLE SOURCES)
Если результат опирается на несколько источников:
- каждый источник должен быть перечислен отдельно в KB_SOURCES,
- конфликтующие нормы должны быть зафиксированы через policy (CTL) или через явный “conflicts_with” REL + решение.

Запрещено:
- “сшивать” источники так, что теряется, откуда взято правило.

---

## 7) COMMON VIOLATIONS (EXAMPLES)
### Violation 1 — “Logic fill”
Симптом: добавлена деталь, которой нет в источнике (“логично же”).
Решение: удалить деталь или найти модуль-источник, где это сказано.

### Violation 2 — “Memory without VERIFIED”
Симптом: применена память по UNREAD/READ_ONCE.
Решение: переоткрыть модуль или остановить run.

### Violation 3 — “Hidden source”
Симптом: сказано “я использовал KB”, но нет списка KB_SOURCES.
Решение: FAIL, пока не будет evidence block.

---

## 8) QUICK CHECK (FAST)
Source-lock соблюдён, если:
- любой ключевой тезис можно привязать к KB_SOURCES,
- нет новых деталей без источника,
- память используется только VERIFIED,
- при сомнении выбран re-open, а не домысел.

--- END.
