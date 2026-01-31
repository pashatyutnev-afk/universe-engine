# 16__FOCUS_LOOP_STOP_RULES_CTL

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: CTL
UID: UE.V2.CTL.MUSIC.FOCUS_LOOP_STOP.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Контроллер остановки итераций (FOCUS-LOOP): когда продолжать, когда фиксировать, когда менять стратегию.

---

## [M] INTENT
Не допустить бесконечной шлифовки: итерации продолжаются только пока есть прогресс или пока пользователь хочет.

---

## [M] STOP CONDITIONS (ANY)
S1) USER_STOP: пользователь сказал “стоп”.
S2) PASS: QA/VAL дали PASS по фокусу (hook/mix/lyrics/etc).
S3) MAX_PASSES: достигнут лимит проходов по STEP_BUDGET_CTL и нет прогресса.
S4) REGRESSION: улучшение фокуса ломает другой обязательный критерий (regression guard).
S5) NO_DIFF: 2 прохода подряд дают “те же варианты” → сменить оси/команду.

---

## [M] PROGRESS HEURISTIC (SIMPLE)
Считаем прогресс, если выполняется хотя бы одно:
- QA score улучшился (например recognition быстрее, translation чище)
- исчезла major проблема из REPORT_TOKEN
- выросла различимость/уникальность (differentiation)
Если прогресса нет 2 прохода подряд → STOP (S3/S5).

---

## [M] OUTPUTS
- REPORT_TOKEN (CTL): CONTINUE / STOP + причина + рекомендация следующего шага

---

## [M] GATES
PASS если:
- решение STOP/CONTINUE обосновано
REWORK если:
- итерации идут без прогресса и без решения
