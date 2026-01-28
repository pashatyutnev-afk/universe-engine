# KB QUALITY LAWS — QUALITY CONTROL PLANE (ABSOLUTE)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/10__KB_QUALITY_LAWS.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: RULE
INDEX_TYPE: QUALITY_LAWS (KB)
LEVEL: L1
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.RULE.QUALITY.001
OWNER: SYSTEM
ROLE: Define enforceable quality laws for KB modules and assets; ensures KB is usable, audited, and capable of driving professional-grade output

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created enforceable KB quality laws with mandatory criteria, anti-patterns, and promotion rules to VERIFIED."
- REASON: "KB must be the main quality driver for all content and entity decisions."
- IMPACT: "All KB modules become checkable; low-quality content is rejected; entities can rely on VERIFIED modules safely."
- CHANGE_ID: UE.CHG.2026-01-14.KB.QUALITY.001

---

## 0) PURPOSE (LAW)
KB — главный источник качества системы. Эти законы определяют:
- что считается “качественным KB модулем”,
- какие минимальные требования обязательны,
- какие дефекты запрещены,
- как модуль повышается до VERIFIED.

Эти законы обязательны для:
- PILLARS
- TOPICS
- SHARED LIBRARIES (CL/RUBRIC/TPL/PATTERN/EXAMPLE/PROMPT)
- ENTITY KB packs (connectors / SPC PRO PACK)
- MAPS (task→scope / validation matrix / pipeline maps)

---

## 1) LAW: ACTIONABLE-ONLY (ABSOLUTE)
### Requirement
Любая KB-единица должна быть применима в работе без догадок.

### Evidence
В модуле должен быть минимум один из элементов:
- procedure (шаги)
- checklist (пункты)
- rubric (критерии PASS/FAIL/REWORK)
- template (структура результата)
- test cases/examples (вход→ожидание→пояснение)

### Fail
Если модуль — “описательный текст” без применения → FAIL.

---

## 2) LAW: EXAMPLES REQUIRED (ABSOLUTE)
### Requirement
Каждый TOPIC и большинство LIBRARY ITEMS обязаны иметь примеры.

Минимум:
- PASS example
- FAIL example
- EDGE example (если применимо)

### Fail
Нет PASS/FAIL → FAIL (модуль не пригоден для контроля качества).

---

## 3) LAW: SINGLE SOURCE OF TRUTH (ABSOLUTE)
### Requirement
Одно правило/норма/определение должно иметь одно место истины.

### Fail
Дубликаты запрещены.
Если нужно повторить — делается ссылка:
- через KB_SOURCES (PATH/RAW)
- через RELATED (REL/XREF)

---

## 4) LAW: NO FANTASY / SOURCE-LOCK (ABSOLUTE)
### Requirement
Нельзя додумывать или “улучшать смысл”.
Любая норма/процедура:
- source-locked (из открытого модуля),
- или Memory-OK без искажений (VERIFIED).

### Fail
Любая вставка “по логике” без источника → FAIL.

---

## 5) LAW: MACHINE-READABLE STRUCTURE (ABSOLUTE)
### Requirement
KB должен быть удобен для применения:
- короткие секции
- строгие заголовки
- списки вместо простыней
- однозначные формулировки (без “обычно/примерно/часто”)

### Fail
Если модуль нельзя применить быстро, он не выполняет роль KB.

---

## 6) LAW: GATES & CHECKS ATTACHMENT (ABSOLUTE)
### Requirement
Если модуль влияет на качество результата, он должен иметь привязку к проверке:
- rubric / validator / QA gate / checklist

Это может быть:
- секция `KB_GATES` (в connector packs),
- или `REL: gated_by` / `REL: validated_by` (в модулях).

### Fail
Если модуль вводит нормы, но не имеет способа проверки → FAIL.

---

## 7) LAW: COVERAGE VISIBILITY (ABSOLUTE)
### Requirement
Покрытие должно быть видимым:
- сущности: coverage status file
- SPC: proficiency matrix
- задачи: task→scope map

### Fail
Если система “не знает что покрыто”, KB не может управлять качеством.

---

## 8) LAW: CHANGE CONTROL (ABSOLUTE)
### Requirement
Любое значимое изменение KB должно быть:
- отражено в KB_CHANGELOG
- иметь impact note (кто затронут)
- иметь корректный SemVer bump

### Fail
Тихая правка → FAIL.

---

## 9) LAW: PROMOTION TO VERIFIED (CONTROLLED)
### Requirement
VERIFIED = модуль безопасен для Memory-OK.

Минимальные условия, чтобы модуль стал VERIFIED:
- модуль ACTIVE
- есть actionable content
- есть PASS/FAIL примеры (если применимо)
- модуль использовался в реальной работе и не дал конфликтов
- есть ясные REL/XREF связи (если нужно)
- изменение VERIFIED модуля требует пересмотра статуса

### Fail
Нельзя ставить VERIFIED “по желанию”.

---

## 10) ANTI-PATTERNS (FORBIDDEN)
Запрещено в KB:
- “мнения” без процедур и критериев
- бесконечные статьи без чеклистов/примеров
- дубли правил в разных местах
- размытые слова: “часто”, “как правило”, “обычно” без порога/гейта
- ссылки “куда-то туда” без PATH
- карты XREF, которые не отвечают на вопрос (свалка ссылок)

---

## 11) QUICK QUALITY CHECK (FAST)
Модуль считается годным, если ответ “ДА” на вопросы:
- Можно ли применить за 60 секунд?
- Есть ли PASS/FAIL пример?
- Есть ли способ проверки (rubric/validator/QA)?
- Нет ли дублирования смысла?
- Нет ли фантазии без источника?
- Понятно ли, где это лежит (storage map) и как называется (naming)?

--- END.
