# 09__MIX_FOCUS_LOOP_ORC

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: ORC
UID: UE.V2.ORC.MUSIC.MIX_FOCUS_LOOP.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: FOCUS-LOOP оркестратор для микса и трансляции (translation).

---

## [M] PURPOSE
Доводить микс сериями правок: баланс, удар, бас, маскинг, пространство.
Каждый pass решает 1–2 проблемы, не всё сразу.

---

## [M] INPUTS
- FOCUS_TOKEN ("улучшить микс/translation")
- CURRENT_MIX_REF (TOKEN_ID)
- CONSTRAINTS (что не ломать)

---

## [M] OUTPUTS
- OPTIONS_TOKEN (2–4 направления правок)
- DECISION_TOKEN
- MINI_REPORT_TOKEN (QA translation)
- DELTA_TOKEN
- NEXT_PROMPT

---

## [M] RULES
1) Каждый pass выбирает 1–2 узких фокуса (например бас vs кик, или вокал vs лид).
2) Обязателен mini QA по translation (телефон/наушники/колонка — как минимум логически).
3) Запрещено лечить всё "громкостью" вместо баланса.
4) Останов при PASS по translation и отсутствии major дефектов.

---

## [M] GATES
PASS если:
- QA translation PASS
REWORK если:
- правки не улучшают или ломают другие части
STOP если:
- фокус не определён
