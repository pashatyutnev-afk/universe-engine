# 01__RULES__CTL

FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__RULES__CTL.md
SCOPE: Universe Engine / Controllers (CTL) / Ruleset
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: RULESET
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.CTL.RULES.001
OWNER: SYSTEM
ROLE: Canonical rules for CTL: checkpoint states, blocker format, interaction law with ORC, and boundary enforcement (no role mixing).

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MAJOR
- SUMMARY: "Aligned rules with DOC CONTROL + canonical SoT pointers + explicit RAW snapshot interaction."
- REASON: "Eliminate outdated references and prevent CTL/ORC/VAL/QA role mixing."
- IMPACT: "Deterministic control behavior, stable gate semantics, audit-friendly blockers."

---

## 0) CTL CORE LAW (ABSOLUTE)
CTL отвечает за:
- управление состоянием выполнения (execution state)
- проверку наличия обязательных артефактов шага/пайплайна
- блокировку/разблокировку по условиям CTL
- выдачу списка blockers в обязательном формате

CTL не отвечает за:
- доменные решения (SPC/ENG)
- структурную валидацию и канон-совместимость (VAL)
- качество/естественность/вкус (QA)

---

## 1) RAW SNAPSHOT INTERACTION LAW (ABSOLUTE)
- CTL может ссылаться на стандарты/индексы только по RAW.
- Разрешены ссылки только из:
  - ROOT link base (snapshot), или
  - явных RAW ссылок пользователя, или
  - канон-индексов слоя (например CTL INDEX), которые сами доступны по RAW.
- Любая ссылка на неразрешённый документ = нарушение (S0) и причина остановки (BLOCKED).

---

## 2) UID + VERSION (MANDATORY)
- UID обязателен для каждого CTL.
- VERSION обязателен и должен быть semver (например 1.0.0 / 2.1.3).
- Формат UID задаётся системными правилами UID.

---

## 3) CTL MINI-CONTRACT (MANDATORY)
Каждый CTL обязан содержать MINI-CONTRACT:

CONSUMES:
- что принимает контроллер (например: PRJ_UID, список ожидаемых артефактов, кандидат-артефакт)

PRODUCES:
- что выдаёт (checkpoint state, blockers list, readiness report)

DEPENDS_ON:
- зависимости (обычно [] или ссылки на стандарты/контракты)

OUTPUT_TARGET:
- куда писать результат (LOG / PRJ / OUT)

---

## 4) CHECKPOINT STATES (CANON)
Каждый CTL-checkpoint возвращает ровно одно состояние:

- READY — можно продолжать
- BLOCKED — нельзя продолжать
- DONE — checkpoint завершён
- SKIP — разрешённый пропуск (только если явно разрешено в ORC или политике)

---

## 5) BLOCKERS FORMAT (MANDATORY)
Если состояние BLOCKED:
- blockers обязателен
- каждый blocker имеет severity S0–S3
- каждый blocker содержит требуемое действие

BLOCKER:
- CODE:
- SEVERITY: S0 | S1 | S2 | S3
- MESSAGE: "<что отсутствует или что нарушено>"
- REQUIRED_ACTION: "<что сделать, чтобы снять blocker>"

Severity guidance:
- S0: ломает канон/навигацию/закон — стоп немедленно
- S1: критично для корректного результата — стоп
- S2: желательно исправить — допускается продолжение только если ORC разрешает
- S3: уведомление — продолжение разрешено

---

## 6) INTERACTION WITH ORC (GATES)
Если ORC step имеет gate CTL:
- CTL обязан проверить обязательные outputs текущего шага
- CTL обязан вернуть state и blockers (если BLOCKED)
- ORC обязан остановиться при BLOCKED (S0/S1)
- ORC может продолжить при S2/S3 только если политика/ORC это явно разрешают

---

## 7) ROLE MIXING CONFLICT RULE (S0)
Если CTL начинает:
- придумывать доменное решение (роль SPC/ENG)
- утверждать канон-правила (роль VAL)
- оценивать художественное качество (роль QA)
то это нарушение S0.
CTL обязан вместо этого:
- сформировать BLOCKED
- сослаться на релевантный закон/стандарт (RAW)
- потребовать корректировку через нужную роль (SPC/VAL/QA)

---

## 8) INTERFACES (RAW)
- UID RULES: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md
- DOC CONTROL: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
- CTL INDEX (SoT): https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/02__INDEX_ALL_CONTROLLERS.md
- CTL TEMPLATE (ENTITY): https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/00__TEMPLATES/00__TEMPLATE__CTL_ENTITY.md
- CTL TEMPLATE (BLOCKER): https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/00__TEMPLATES/00__TEMPLATE__CTL_BLOCKER.md

---

## 9) KNOWLEDGE BASE (KB) SCOPE
KB может хранить примеры blockers, gate-отчётов, паттерны контроля.
CTL не создаёт знания и не переписывает стандарты.

--- END.
