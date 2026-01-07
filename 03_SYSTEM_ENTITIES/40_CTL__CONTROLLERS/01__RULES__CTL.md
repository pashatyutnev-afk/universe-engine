# CONTROLLERS (CTL) — RULES
FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__RULES__CTL.md

SCOPE: Universe Engine / CTL Rules
ENTITY_GROUP: ENT
CATEGORY: CTL
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Правила CTL: как ставятся gates, как определяется READY/BLOCKED/DONE, и как CTL взаимодействует с ORC/VAL/QA.

SOURCE OF TRUTH:
- UID Standard: `02_STANDARDS/01_SPECIFICATIONS/UID_AND_MARKING_SPEC.md`

---

## 0) CTL CORE LAW
CTL отвечает за:
- управление состоянием процесса (execution state)
- проверку наличия обязательных артефактов
- блокировку/разблокировку по условиям

CTL НЕ отвечает за:
- доменные решения (SPC/ENG)
- структурную валидацию (VAL)
- художественное качество/естественность (QA)

---

## 1) UID FORMAT (CTL)
`UE.ENT.CTL.<FAMILY>.<NAME>`

FAMILY рекомендуется:
- GOV (governance/process)
- PROD (production control)
- GEN (general)

---

## 2) CTL MINI-CONTRACT (MANDATORY)
CONSUMES:
- контекст пайплайна (обычно PRJ_UID + список ожидаемых outputs)
PRODUCES:
- checkpoint status + blockers
DEPENDS_ON:
- ORC (план шагов) или []
OUTPUT_TARGET:
- PRJ | OUT | LOG (куда фиксируются результаты контроля)

---

## 3) CHECKPOINT STATES (CANON)
Каждый CTL чекпоинт обязан возвращать одно состояние:

- READY — можно продолжать
- BLOCKED — нельзя продолжать
- DONE — чекпоинт завершён
- SKIP — разрешённый пропуск (только если явно разрешено в ORC)

---

## 4) BLOCKERS FORMAT (MANDATORY)
Если BLOCKED:
- список blockers обязателен
- каждый blocker имеет severity S0–S3

BLOCKER:
- CODE: <short>
- SEVERITY: <S0|S1|S2|S3>
- MESSAGE: <что отсутствует/что нарушено>
- REQUIRED_ACTION: <что сделать>

---

## 5) INTERACTION WITH ORC (GATES)
ORC STEP может иметь `GATE: CTL`.
В таком случае:
- CTL обязан проверить обязательные outputs текущего шага
- CTL обязан вернуть state
- ORC обязан остановиться при BLOCKED (S0/S1)

---

## 6) CONFLICT RULE
Если CTL начинает:
- “решать как должно быть” (роль ENG/SPC)
- “утверждать правила” (роль VAL/QA)
— это нарушение (S0).

---
END.
