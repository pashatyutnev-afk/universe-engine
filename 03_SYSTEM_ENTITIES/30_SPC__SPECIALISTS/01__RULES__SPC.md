# SPECIALISTS (SPC) — RULES
FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/01__RULES__SPC.md

SCOPE: Universe Engine / SPC Rules
ENTITY_GROUP: ENT
CATEGORY: SPC
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Правила для SPC: границы ответственности, формат контрактов, структура ответов, анти-конфликты.

SOURCE OF TRUTH:
- UID Standard: `02_STANDARDS/01_SPECIFICATIONS/UID_AND_MARKING_SPEC.md`

---

## 0) SPC CORE LAW
SPC отвечает за:
- доменную экспертизу
- конкретные решения и параметры
- формализацию решений в структуры (для PRJ/KB/AST/OUT)

SPC НЕ отвечает за:
- порядок пайплайна (ORC)
- законы системы (ENG governance)
- финальную валидацию структуры (VAL)
- финальную оценку качества/естественности (QA)

---

## 1) UID FORMAT (SPC)
`UE.ENT.SPC.<FAMILY>.<NAME>`

Пример:
`UE.ENT.SPC.VIS.CINEMATOGRAPHER`
`UE.ENT.SPC.SND.SFX_DESIGNER`
`UE.ENT.SPC.NAR.DIALOGUE_DOCTOR`

FAMILY рекомендуется:
- NAR (narrative)
- WORLD (worldbuilding)
- VIS (visual)
- SND (sound)
- GEN (general)
- QLT (quality-advice only, без финального QA)

---

## 2) SPC MINI-CONTRACT (MANDATORY)
Каждый SPC обязан иметь:

CONSUMES:
- 1–5 типов входа (контекст/цель/ограничения)

PRODUCES:
- 1–5 типов выхода (decision pack / constraints / prompt payload / KB suggestions)

DEPENDS_ON:
- список ENG/STD правил или []

OUTPUT_TARGET:
- KB | PRJ | AST | OUT (куда основной результат)

Если mini-contract отсутствует — SPC incomplete.

---

## 3) SPC OUTPUT SHAPE (MANDATORY)
Ответ SPC обязан иметь:
- DECISIONS (что выбрано и почему)
- CONSTRAINTS (что нельзя нарушать)
- DELIVERABLES (что отдаём в PRJ/KB/AST/OUT)
- OPEN_QUESTIONS (если есть, но минимум)

---

## 4) CONFLICT RULE
Если SPC начинает:
- маршрутизировать шаги (роль ORC)
- “утверждать канон” (роль governance ENG/CTL/VAL)
— это конфликт (S0).

---
END.
