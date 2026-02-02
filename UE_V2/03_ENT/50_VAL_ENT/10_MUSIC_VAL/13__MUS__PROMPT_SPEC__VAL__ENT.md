# 13__PROMPT_SPEC_VAL

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: VAL
UID: UE.V2.VAL.MUSIC.PROMPT_SPEC.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Валидация PROMPT_SPEC для музыки: контракт, негатив-спеки, соответствие плану и ограничениям.

---

## [M] INPUTS
- PROMPT_SPEC_TOKEN
- KB_TOKEN (rules + do_not)
- CTL policies:
  - 01__PROMPT_CONTRACT_CTL
  - 12__NEGATIVE_SPEC_LIBRARY_CTL (если применимо)
- PLAN_TOKEN (mode, constraints)

---

## [M] CHECKS (MIN)
P1) PROMPT_SPEC содержит: цель/жанр/темп/настроение/структуру или указание структуры.
P2) Есть NEGATIVE / DO_NOT часть (минимум 3 пункта) и она не противоречит KB_TOKEN.
P3) PROMPT_SPEC согласован с DURATION_POLICY_CTL (если задана длительность/формат).
P4) PROMPT_SPEC не содержит мусора/длинных полотен (уважает NOISE_BUDGET).
P5) PROMPT_SPEC не использует восклицательные знаки (по вашему правилу для SUNO-контента).
P6) Если используется “серия/артист ДНК” — PROMPT_SPEC не нарушает IDENTITY правила (если есть).

---

## [M] OUTPUTS
- REPORT_TOKEN (VAL): PASS/REWORK + конкретные правки

---

## [M] GATES
PASS если:
- все проверки P1–P5 выполнены
REWORK если:
- отсутствуют негатив-спеки/есть противоречия/есть "!"
