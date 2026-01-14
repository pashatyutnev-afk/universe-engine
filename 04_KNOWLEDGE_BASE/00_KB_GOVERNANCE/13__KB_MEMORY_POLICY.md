# KB MEMORY POLICY — CONTROLLED MEMORY MODE (KB)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/13__KB_MEMORY_POLICY.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: RULE
INDEX_TYPE: MEMORY_POLICY (KB)
LEVEL: L1
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.RULE.MEMORY.001
OWNER: SYSTEM
ROLE: Define controlled Memory-OK usage for KB modules; prevent distortion, enforce VERIFIED-only recall, and define re-open triggers and conflict resolution

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created KB memory policy: VERIFIED-only recall, re-open triggers, version awareness, and conflict handling."
- REASON: "System must be able to reuse knowledge without rereading every time while preventing hallucination and drift."
- IMPACT: "Memory becomes safe and auditable; outdated recall is blocked; changes trigger revalidation."
- CHANGE_ID: UE.CHG.2026-01-14.KB.MEMORY.001

---

## 0) PURPOSE (LAW)
KB запрещает фантазию, но допускает использование памяти как ускорение,
если память управляемая и не искажает источники.

Этот документ определяет:
- когда память разрешена (Memory-OK),
- когда память запрещена (Memory-NO),
- какие триггеры требуют переоткрытия источника,
- как обрабатывать конфликты.

---

## 1) ABSOLUTE RULE: VERIFIED-ONLY RECALL
Память разрешена только для модулей, имеющих состояние:
- VERIFIED

Запрещено использовать память для:
- UNREAD
- READ_ONCE
- DEPRECATED

Правило:
- если модуль не VERIFIED → либо переоткрыть, либо STOP.

---

## 2) MEMORY-OK CONDITIONS (MANDATORY)
Memory-OK допускается, если одновременно выполняется:
1) Модуль ранее был открыт и применён в работе.
2) Модуль имеет состояние VERIFIED.
3) Формулировка воспроизводится без изменения смысла.
4) Нет признаков, что модуль изменился (см. version rules).
5) Нет конфликтов с другими REQUIRED источниками.

Если любой пункт не выполнен → Memory-NO.

---

## 3) MEMORY-NO CONDITIONS (HARD)
Память запрещена, если:
- есть сомнение в точности формулировки,
- требуется точная цитата/порог/формат (thresholds/violation format),
- модуль относится к governance (rules/policies/gates), и версия могла меняться,
- конфликт норм не разрешён policy,
- последний известный статус модуля был не VERIFIED.

При Memory-NO:
- переоткрыть источник по RAW
- или STOP, если источник недоступен.

---

## 4) RE-OPEN TRIGGERS (MANDATORY)
Источник должен быть переоткрыт, если:
- прошло “слишком много” времени с последнего применения (операционное правило: при любом сомнении),
- модуль мог быть изменён (версия/CHANGE_NOTE/KB_CHANGELOG),
- задача требует строгой формальности (контракт/порог/правило),
- результат имеет высокий риск ошибки (gates/policies),
- обнаружены расхождения между памятью и текущими другими источниками.

---

## 5) VERSION AWARENESS (REQUIRED)
Память должна быть “версийно-осознанной”.

Правила:
- если модуль VERIFIED и использовался по памяти, но его VERSION изменился:
  - Memory-OK снимается,
  - требуется переоткрытие и повторная валидация,
  - модуль может временно вернуться в READ_ONCE до подтверждения.

Источник правды о факте изменения:
- KB_CHANGELOG
- CHANGE_NOTE в шапке документа

---

## 6) CONFLICT HANDLING (ABSOLUTE)
Если память конфликтует с текущим source-locked источником:
- источник имеет приоритет,
- память считается недостоверной,
- требуется переоткрыть модуль и синхронизировать понимание,
- результат без переоткрытия запрещён.

Если конфликтуют два источника:
- требуется policy/решение (CTL) или явная карта XREF,
- пока нет решения — STOP.

---

## 7) EVIDENCE REQUIREMENT (MANDATORY)
Если применялась память, в evidence блоке должно быть явно указано:

- MEMORY_MODE: ON (VERIFIED only)
- MEMORY_ITEMS:
  - PATH: <module>
    STATE: VERIFIED
    VERSION: <known>

Если MEMORY_MODE не указан, считается что память не применялась.

---

## 8) SAFE RECALL PRACTICE (HOW TO WRITE FROM MEMORY)
Даже при Memory-OK запрещено:
- расширять смысл,
- добавлять новые детали,
- менять критерии PASS/FAIL,
- менять пороги/структуры форматов.

Разрешено:
- кратко воспроизвести утверждение,
- сослаться на PATH,
- при необходимости — переоткрыть и уточнить формулировку.

---

## 9) QUICK CHECK (FAST)
Memory-OK, если:
- модуль VERIFIED,
- формулировка воспроизводится без искажений,
- версия не менялась,
- нет конфликтов,
- при сомнении выбран re-open, а не “логическое дополнение”.

--- END.
