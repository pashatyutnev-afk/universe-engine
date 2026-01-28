# 02__CASE__BAD — MUSIC_PRODUCER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/02__MUSIC_PRODUCER_SPC/06__CASE_LIBRARY/02__CASE__BAD.md
SCOPE: KB — SPC Pro Pack — Music Producer — Case (BAD)
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS / 06__CASE_LIBRARY
DOC_TYPE: CASE
CASE_TYPE: BAD
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.CASE.BAD.001
OWNER: SPC (Music Producer)
ROLE: Calibration anchor for FAIL patterns (hard-limit violations + unusable outputs).

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "BAD case initialized for Music Producer SPC pack."
- REASON: "Prevent recurring forbidden patterns."
- IMPACT: "Defines fail signatures and automatic-stop triggers."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MPROD.CASE.BAD.001

---

## INTENT
Показать “как выглядит FAIL”:
- роль смешана (продюсер превращается в инженера/юриста/промптрайтера),
- инструкции неисполняемые,
- нет acceptance/trace,
- нарушены hard limits.

---

## INPUTS (MINIMAL)
- TASK_GOAL: "Сделай трек под короткие ролики."
- CONSTRAINTS: "хочу чтобы качало, и чтобы вокал был чистый."

---

## OUTPUT (ANTI-EXEMPLAR)

### O1 — PRODUCER_TASK_CARD (BROKEN)
- GOAL:
  - "Сделать мегахит и чтобы всем нравилось"  (неоперационально)
- DELIVERABLES:
  - "сделаем всё что надо" (не определено)
- CONSTRAINTS:
  - отсутствуют конкретные ограничения
- ACCEPTANCE:
  - "должно звучать круто" (непроверяемо)
- SCOPE:
  - отсутствует (role drift возможен)

### O2 — PRODUCTION_EXEC_PLAN (BROKEN)
#### A) “Structure”
- "Сделай интро, куплет, припев как обычно" (без таймингов/хука/логики)

#### B) Engineering recipe (HARD LIMIT VIOLATION)
- "Подними 3.5k на вокале на +4dB, срежь 200Hz, компрессор 4:1, лимитер -7 LUFS"
(запрещено для продюсера как “истина/рецепт”)

#### C) Legal determinations (HARD LIMIT VIOLATION)
- "Этот текст точно можно использовать, проблем не будет"
(юридическое утверждение запрещено)

#### D) Prompt authoring takeover (if separated)
- "Вот финальный промпт для генерации: ..."
(если у вас Prompt Architect отдельный — это role drift)

#### E) No seat plan / no contrast / no hook test
- "Добавь побольше инструментов, чтобы было мощно"
(ведёт к перегрузу, нет решений)

#### F) No acceptance / no validation / no trace
- отсутствует PASS/REWORK/FAIL
- отсутствуют чеклисты/гейты
- отсутствует trace

---

## FAIL SIGNATURES (WHAT TO DETECT)
- hard-limit: engineering recipe statements
- hard-limit: legal conclusions
- missing: acceptance criteria
- missing: section map + hook placement
- vague language: "круто/мощно/как обычно"
- no validation route, no trace

---

## RUBRIC (ROUGH SCORES)
- D1 Clarity: 2
- D2 Scope discipline: 0
- D3 Structure: 3
- D4 Seat plan: 1
- D5 Performance notes: 2
- D6 Constraints fit: 2
- D7 Validation/trace: 0
- D8 Consistency: 2
- D9 Variants: N/A

OVERALL: FAIL

---

## WHY THIS CASE EXISTS
Это “красный флаг”:
- если output похож на этот кейс → STOP + REWORK через PB-02
- если есть hard-limit violations → FAIL без попыток “принять”

---

## REQUIRED UID REFERENCES
- PRINCIPLES:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.PRINCIPLES.001
- RUBRIC:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.RUBRIC.001

---
END
