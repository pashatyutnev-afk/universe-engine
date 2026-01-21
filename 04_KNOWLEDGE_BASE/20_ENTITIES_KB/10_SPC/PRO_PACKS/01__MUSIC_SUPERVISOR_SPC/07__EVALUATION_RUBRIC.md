# 07__EVALUATION_RUBRIC — MUSIC_SUPERVISOR_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/01__MUSIC_SUPERVISOR_SPC/07__EVALUATION_RUBRIC.md
SCOPE: KB — SPC Pro Pack — Music Supervisor — Evaluation Rubric
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS
DOC_TYPE: RUBRIC
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_SUPERVISOR.RUBRIC.001
OWNER: SPC (Music Supervisor)
ROLE: Scoring rubric aligned to gates/checklists; used to judge output readiness and pack maturity.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Evaluation rubric initialized for Music Supervisor SPC pack."
- REASON: "Create consistent scoring and calibration."
- IMPACT: "Rubric ties to gates + cases."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MSUP.RUBRIC.001

---

## PURPOSE (LAW)
Рубрика нужна для:
- единообразной оценки качества результата,
- калибровки гейтов,
- оценки зрелости пака (насколько он “исполняемый”).

---

## SCORING SCALE
0–10 по каждому измерению.

- 0–2: FAIL (неиспользуемо)
- 3–4: REWORK (почти, но нельзя принимать)
- 5–7: PASS (рабочее, но без полиша)
- 8–10: READY (publish-ready)

---

## DIMENSIONS (TIED TO VALIDATIONS)

### D1 — Clarity (ties to CHK-QUALITY + GATE-CORE)
- 0–2: смысл/шаги неясны, требуется угадывание
- 3–4: ядро понятно, но есть двусмысленности
- 5–7: ясно, можно выполнять без вопросов
- 8–10: максимально ясно, компактно, читаемо

Anchors:
- 0–2: CASE-B-001
- 5–7: CASE-G-001
- 8–10: CASE-G-001 (polished)

### D2 — Completeness (ties to CHK-QUALITY + GATE-CORE)
- 0–2: отсутствуют обязательные части
- 3–4: есть пробелы/плейсхолдеры
- 5–7: всё обязательное есть
- 8–10: всё есть + аккуратная упаковка без лишнего

### D3 — Structure / Scanability (ties to CHK-QUALITY)
- 0–2: хаос, невозможно быстро понять
- 3–4: структура есть, но слабая
- 5–7: хорошо сканируется
- 8–10: структура “идеальная”, минимально-достаточная

### D4 — Consistency (ties to GATE-CONSISTENCY)
- 0–2: противоречия ломают результат
- 3–4: есть локальные конфликты/дрейф терминов
- 5–7: нет противоречий, термины стабильны
- 8–10: термины/правила предельно стабильны, нет скрытых конфликтов

Anchors:
- FAIL: CASE-B-001
- REWORK: CASE-BL-001
- PASS: CASE-G-001

### D5 — Constraint Fit (ties to CHK-COMPLIANCE)
- 0–2: грубо нарушены ограничения/формат
- 3–4: мелкие несоответствия
- 5–7: соответствует ограничениям
- 8–10: идеально под платформу/формат, без лишнего

### D6 — Scope & Safety (ties to CHK-COMPLIANCE)
- 0–2: out-of-scope / hard limit violations
- 3–4: scope creep, но removable
- 5–7: в рамках covers/excludes
- 8–10: чисто, плюс корректная маршрутизация

### D7 — Repeatability / Trace (ties to PB-03 + trace)
- 0–2: нет следа, не воспроизвести
- 3–4: след частичный
- 5–7: есть минимальный trace
- 8–10: trace ясный, краткий, полезный

### D8 — Edge Robustness (ties to GATE-EDGE when enabled)
- 0–2: ломается на edge
- 3–4: edge учтён частично
- 5–7: edge обработан, если применимо
- 8–10: edge обработан чисто и без регрессий

Anchor:
- CASE-E-001 (when enabled)

---

## OVERALL DECISION RULE
- FAIL if any of: D1<=2 OR D4<=2 OR D6<=2
- REWORK if:
  - any dimension in 3–4 range on D1/D4/D6
- PASS if:
  - D1>=5, D4>=5, D6>=5 and no hard fails
- READY if:
  - D1>=8, D4>=8, D6>=8 and trace>=8

---

## REQUIRED LINKS (UID-ONLY)
- CHECKLISTS:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CHK.READINESS.001
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CHK.QUALITY.001
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CHK.COMPLIANCE.001
- GATES:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.GATE.CORE_QUALITY.001
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.GATE.CONSISTENCY.001
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.GATE.EDGE_CASES.001
- CASES:
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CASE.GOOD.001
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CASE.BAD.001
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CASE.BORDERLINE.001
  - UE.KB.SPC.PACK.MUSIC_SUPERVISOR.CASE.EDGE.001

---
END
