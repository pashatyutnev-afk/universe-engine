# CONTROLLERS (CTL) — RULESET (LAW) (CANON)

FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__RULES__CTL.md
SCOPE: Universe Engine (Games volume) / System Entities / Controllers (CTL)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: RULESET
ENTITY_GROUP: CONTROLLERS (CTL)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.CTL.RULES.001
OWNER: SYSTEM
ROLE: Hard rules for CTL controllers: gate semantics, checkpoint schema, blocker schema, role boundaries, and stop behavior.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MAJOR
- SUMMARY: "Rebuilt CTL ruleset to DOC CONTROL + RAW-only interfaces; removed legacy UID spec pointers; hardened gate/order semantics and conflict rules."
- REASON: "Old rules had drift and weak enforcement contract."
- IMPACT: "CTL becomes deterministic and machine-checkable across ORC pipelines."
- CHANGE_ID: UE.CHG.2026-01-20.CTL.RULES.002

---

## 0) CORE LAW
CTL отвечает за:
- контроль состояния выполнения (execution state)
- проверку обязательных артефактов/полей/регистраций в точке gate
- блокировку/разблокировку по условиям CTL
- выдачу blockers в едином формате

CTL НЕ отвечает за:
- доменные решения (SPC/ENG)
- структурную валидацию законов/канона (VAL)
- художественное качество/естественность (QA)

Нарушение границ роли → S0.

---

## 1) EXISTENCE RULE (ABSOLUTE)
CTL контроллер является каноном только если:
- зарегистрирован в CTL Global Registry (SoT)
- имеет UID
- оформлен по CTL Entity Template (или допустимому base-template как reference)

---

## 2) CTL MINI-CONTRACT (MANDATORY)
Каждый CTL обязан иметь MINI-CONTRACT:

CONSUMES:
- контекст пайплайна (минимум: что проверяем + где применяется)
- входные артефакты для проверки (списком)

PRODUCES:
- checkpoint status
- blockers list (если BLOCKED)

DEPENDS_ON:
- ORC (как минимум: шаг/ожидаемые outputs) или []

OUTPUT_TARGET:
- LOG | PRJ | OUT (куда фиксируется результат контроля)

Если mini-contract отсутствует → INVALID (S0).

---

## 3) CHECKPOINT STATES (CANON)
Каждый CTL checkpoint обязан вернуть ровно одно состояние:
- READY — можно продолжать
- BLOCKED — нельзя продолжать
- DONE — checkpoint выполнен (фиксируем completion)
- SKIP — разрешённый пропуск (только если ORC явно допускает)

Если state не из списка → INVALID (S0).

---

## 4) CHECKPOINT SCHEMA (MANDATORY)
Каждый CTL должен содержать минимум один checkpoint:

CHECKPOINT:
- NAME:
- APPLIES_TO:
- REQUIRES (ARTIFACTS):
- CHECKS:
- OUTPUT:
- STATE: READY | BLOCKED | DONE | SKIP
- BLOCKERS: (обязателен, если BLOCKED)

---

## 5) BLOCKERS FORMAT (MANDATORY)
Если state = BLOCKED:
- список blockers обязателен
- каждый blocker строго по шаблону `CTL_BLOCKER`

BLOCKER:
- CODE:
- SEVERITY: S0 | S1 | S2 | S3
- MESSAGE: ""
- REQUIRED_ACTION: ""

Severity meaning:
- S0: нарушен закон/канон/навигация/контракт (стоп)
- S1: критично для корректного результата (обычно стоп)
- S2: важно, но может быть отложено если ORC разрешает
- S3: уведомление/улучшение

---

## 6) INTERACTION WITH ORC (GATES)
Если ORC step имеет `GATE: CTL`:
- CTL обязан проверить REQUIRES/ CHECKS для данного шага
- CTL обязан вернуть STATE
- ORC обязан остановиться при BLOCKED, если есть S0/S1 blockers
- ORC может продолжить при S2/S3 только если это явно разрешено policy/notes ORC

---

## 7) CONFLICT RULE (S0)
Если CTL начинает:
- “решать как должно быть” (роль ENG/SPC)
- “утверждать закон/канон” (роль VAL)
- “оценивать качество/естественность” (роль QA)
это S0: role contamination.

---

## 8) KNOWLEDGE BASE (KB) SCOPE
KB INPUTS:
- playbooks/checklists по типовым контролям
- примеры blockers и gate отчётов

KB OUTPUTS:
- none

BOUNDARIES:
- KB не является обязательным входом для CTL; CTL должен быть самодостаточен.

---

## 9) INTERFACES (RAW ONLY)
- CTL REALM README:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/00__README__CTL_REALM.md
- CTL GLOBAL REGISTRY (SoT):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/02__INDEX_ALL_CONTROLLERS.md
- CTL CREATE FLOW:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/03__CREATE_FLOW__CTL.md
- CTL ENTITY TEMPLATE:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/00__TEMPLATES/00__TEMPLATE__CTL_ENTITY.md
- CTL BLOCKER TEMPLATE:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/00__TEMPLATES/00__TEMPLATE__CTL_BLOCKER.md

--- END.
