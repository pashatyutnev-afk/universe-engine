# 03__CASE__BORDERLINE — MUSIC_PRODUCER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/02__MUSIC_PRODUCER_SPC/06__CASE_LIBRARY/03__CASE__BORDERLINE.md
SCOPE: KB — SPC Pro Pack — Music Producer — Case (BORDERLINE)
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS / 06__CASE_LIBRARY
DOC_TYPE: CASE
CASE_TYPE: BORDERLINE
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.CASE.BORDERLINE.001
OWNER: SPC (Music Producer)
ROLE: Calibration anchor for REWORK-grade outputs (almost usable but fails thresholds).

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "BORDERLINE case initialized for Music Producer SPC pack."
- REASON: "Show typical near-miss issues that require PB-02 one-axis repair."
- IMPACT: "Defines rework triggers and minimal patches."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MPROD.CASE.BORDER.001

---

## INTENT
Показать “4–6 баллов”:
- структура есть, но не привязана к цели/платформе
- seat plan есть, но нет рисков/контраста
- acceptance частично, но непроверяемо
- trace/валидация неполные

---

## INPUTS (MINIMAL)
- TASK_GOAL: "Сделать трек для драйвового видео, нужен hook быстро."
- CONSTRAINTS:
  - hook early
  - общий вайб: энергично, но читаемо
- PLATFORM_INTENT: short-friendly

---

## OUTPUT (NEAR-MISS)

### O1 — PRODUCER_TASK_CARD (OK-ish)
- GOAL:
  - "Энергичный трек с ранним хуком"
- DELIVERABLES:
  - "план аранжировки" (не уточнено O2 состав)
- CONSTRAINTS:
  - "в первые 15 сек должен быть хук" (норм)
- ACCEPTANCE:
  - "чтобы хук запоминался" (не тестируемо)
- SCOPE:
  - не указан (риски role drift)

### O2 — PRODUCTION_EXEC_PLAN (PARTIAL)

#### A) Section map (missing time / logic)
- Intro → Verse → Chorus → Bridge → Chorus
(нет таймингов, нет почему так)

#### B) Arrangement / seat plan (too generic)
- "Вокал спереди, бочка и бас снизу, синты сверху"
(нет решения про плотность, нет предупреждений про перегруз)

#### C) Hook plan (not testable)
- "Сделай цепляющую фразу"
(нет must-hear, нет проверки за 10s)

#### D) Take direction (weak)
- "Пусть поёт эмоционально"
(неоперационально)

#### E) Validation route (incomplete)
- упомянут “чеклист качества”
- нет порядка CHK/GATE
- нет PASS/REWORK/FAIL условий

#### F) Trace (missing)
- TASK_ID отсутствует
- OUTPUTS_PRODUCED не зафиксировано
- rerun/decision отсутствуют

---

## WHAT FAILS HERE (WHY REWORK)
- D1 Clarity страдает: много общих слов
- D3 Structure: нет таймингов и привязки к цели
- D5 Performance notes: нет действий/критериев
- D7 Validation/trace: неполно
- D2 Scope: не обозначены границы

---

## MINIMAL FIX (PB-02) — ONE AXIS EXAMPLE
### Choose axis: clarity
Patch ideas:
- добавить acceptance как проверку (hook recognized <=10s)
- добавить тайминги section map
- добавить must-hear targets
- добавить минимум trace + порядок CHK/GATE

(важно: в одном прогоне выбираем одну ось, здесь пример — clarity, а не всё сразу)

---

## RUBRIC (ROUGH SCORES)
- D1 Clarity: 5
- D2 Scope: 6
- D3 Structure: 5
- D4 Seat plan: 6
- D5 Performance notes: 4
- D6 Constraints fit: 6
- D7 Validation/trace: 4
- D8 Consistency: 7
- D9 Variants: N/A

OVERALL: REWORK

---

## WHY THIS CASE EXISTS
Это типичный “почти норм”:
- не нарушает hard limits,
- но не проходит пороги 7+,
- чинится PB-02 быстро, если держать one-axis.

---

## REQUIRED UID REFERENCES
- RUBRIC:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.RUBRIC.001
- REGRESSION GUARD:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.REGRESSION_GUARD.001
- PLAYBOOK (repair):
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.PB.DIAG_REWORK.001

---
END
