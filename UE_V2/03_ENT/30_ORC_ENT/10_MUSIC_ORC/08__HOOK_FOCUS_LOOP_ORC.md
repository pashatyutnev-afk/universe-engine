# 08__HOOK_FOCUS_LOOP_ORC

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: ORC
UID: UE.V2.ORC.MUSIC.HOOK_FOCUS_LOOP.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: FOCUS-LOOP оркестратор для прокачки хука несколькими проходами.

---

## [M] PURPOSE
Довести хук до PASS: узнаваемость, скролл-стоп, луп без шва.
Проходит партиями сущностей, каждый pass даёт варианты A–E и выбор.

---

## [M] INPUTS
- FOCUS_TOKEN (формулировка: "улучшить хук")
- CURRENT_BEST_REF (TOKEN_ID текущего лучшего варианта)
- CONSTRAINTS (темп/тональность/стиль/запреты)

---

## [M] OUTPUTS
- OPTIONS_TOKEN (A–E)
- DECISION_TOKEN
- MINI_REPORT_TOKEN (QA/VAL)
- ARCHIVE запись (в TOKEN_ARCHIVE)
- NEXT_PROMPT ("ещё проход" или "го дальше")

---

## [M] RULES
1) Один pass = один угол атаки (ритм/мотив/контраст/инструмент/пауза).
2) Каждый pass обязан дать различимые варианты (не косметика).
3) Вопросы максимум 3, всегда с дефолтом.
4) Останов: QA PASS или команда "стоп".

---

## [M] PASS_CRITERIA (DEFAULT)
- Узнаваемость хука ≤ 5 секунд
- Луп без ощутимого стыка
- Хук не тонет и не режет ухо

---

## [M] GATES
PASS если:
- есть winner + MINI_REPORT PASS
REWORK если:
- варианты не различимы
STOP если:
- фокус не определён
