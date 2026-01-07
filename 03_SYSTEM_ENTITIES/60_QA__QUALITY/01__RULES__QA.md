# QUALITY (QA) — RULES
FILE: 03_SYSTEM_ENTITIES/60_QA__QUALITY/01__RULES__QA.md

SCOPE: Universe Engine / QA Rules
ENTITY_GROUP: ENT
CATEGORY: QA
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Правила QA: что считается качеством, как оформляется отчёт, как QA используется как gate в ORC.

SOURCE OF TRUTH:
- UID Standard: `02_STANDARDS/01_SPECIFICATIONS/UID_AND_MARKING_SPEC.md`

---

## 0) QA CORE LAW
QA отвечает за:
- качество восприятия результата (human-likeness)
- консистентность (world/character/style)
- анти-ИИ сигнатуры (speech/text patterns)
- художественные дефекты (темп, тяжесть, перегруз, “пластик”)

QA НЕ отвечает за:
- структурную/правовую валидность (VAL)
- доменные решения (SPC/ENG)
- маршрутизацию и порядок шагов (ORC)
- execution state (CTL)

---

## 1) UID FORMAT (QA)
`UE.ENT.QA.<FAMILY>.<NAME>`

FAMILY рекомендуется:
- NAT (naturalness)
- STY (style/genre/tone)
- TXT (text/speech)
- AUD (audio quality)
- VIS (visual quality)
- GEN (общий)

---

## 2) QA MINI-CONTRACT (MANDATORY)
CONSUMES:
- артефакт результата (текст/сцена/стек/визуал-пак/аудио-пак) + рамки (жанр/тон/правила)
PRODUCES:
- qa report + issues + suggestions
DEPENDS_ON:
- связанные ENG/SPC стандарты или []
OUTPUT_TARGET:
- OUT | PRJ | LOG

---

## 3) QA RESULT STATES (CANON)
QA возвращает:

- PASS — можно выпускать/идти дальше
- FAIL — нельзя выпускать/идти дальше

Если FAIL — обязателен список ISSUES.

---

## 4) ISSUE SEVERITY (CANON S0–S3)
- S0 — стоп. “палево”, ломает восприятие / нарушает рамки жанра/тона.
- S1 — серьёзно. заметно большинству, ухудшает продукт.
- S2 — средне. влияет на качество, но терпимо.
- S3 — мелочь/улучшение.

---

## 5) QA REPORT FORMAT (MANDATORY)
RESULT: <PASS|FAIL>
TARGET_UID: <UID if exists else NONE>
SCORE: <0..100> (опционально, но желательно)
ISSUES:
- CODE
- SEVERITY
- MESSAGE
- FIX_SUGGESTION

RED_FLAGS (optional):
- <anti-ai signature flags>

---

## 6) ORC GATE (QA)
Если ORC STEP имеет `GATE: QA`, то:
- QA обязан вернуть PASS/FAIL
- FAIL с S0 блокирует пайплайн
- S1 блокирует, если ORC не разрешает continuation

---

## 7) CONFLICT RULE
Если QA начинает:
- валидировать структуру законами (VAL роль)
- принимать доменные решения (SPC роль)
— это нарушение (S0).

---
END.
