# VALIDATORS (VAL) — RULES
FILE: 03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/01__RULES__VAL.md

SCOPE: Universe Engine / VAL Rules
ENTITY_GROUP: ENT
CATEGORY: VAL
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Правила VAL: что валидируем, как оформляем нарушения, как используем S0–S3 и как VAL подключается в ORC gates.

SOURCE OF TRUTH:
- UID Standard: `02_STANDARDS/01_SPECIFICATIONS/UID_AND_MARKING_SPEC.md`
- Standards Layer: `02_STANDARDS/`

---

## 0) VAL CORE LAW
VAL отвечает за:
- проверку канонической корректности (law/standards compliance)
- проверку структуры и обязательных требований
- отчёт о нарушениях и действиях исправления

VAL НЕ отвечает за:
- художественное качество (QA)
- доменные решения (SPC/ENG)
- управление маршрутизацией (ORC)
- управление выполнением (CTL)

---

## 1) UID FORMAT (VAL)
`UE.ENT.VAL.<FAMILY>.<NAME>`

FAMILY рекомендуется:
- DOC (документы/форматы)
- IDX (реестры/индексы)
- ENT (сущности/паспорт)
- STD (standards compliance)
- GEN (общий)

---

## 2) VAL MINI-CONTRACT (MANDATORY)
CONSUMES:
- артефакт(ы) + контекст стандарта
PRODUCES:
- validation report + violations + fix actions
DEPENDS_ON:
- стандарты/правила (обычно STD docs) или []
OUTPUT_TARGET:
- PRJ | OUT | LOG (куда кладётся отчёт)

---

## 3) VIOLATION SEVERITY (CANON)
Каждое нарушение обязано иметь severity:

- S0 — стоп. Артефакт считается НЕВАЛИДНЫМ.
- S1 — серьёзно. Можно продолжать только если ORC разрешает.
- S2 — предупреждение. Желательно исправить.
- S3 — заметка/улучшение.

---

## 4) REPORT FORMAT (MANDATORY)
VAL REPORT обязан содержать:

RESULT: <PASS|FAIL>
TARGET_UID: <UID of checked artifact if exists, else NONE>
VIOLATIONS:
- CODE
- SEVERITY
- MESSAGE
- FIX_ACTION

OPTIONAL:
- AUTO_FIX_SUGGESTION

---

## 5) ORC GATE (VAL)
Если ORC STEP имеет `GATE: VAL`, то:
- VAL обязан вернуть PASS/FAIL
- FAIL с S0 блокирует пайплайн
- S1 блокирует, если ORC не разрешает continuation

---

## 6) CONFLICT RULE
Если VAL начинает:
- “улучшать творчество” (роль QA/SPC)
- “решать смысловые решения” (роль SPC/ENG)
— это нарушение (S0).

---
END.
