# 07__EVALUATION_RUBRIC — MUSIC_PRODUCER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/02__MUSIC_PRODUCER_SPC/07__EVALUATION_RUBRIC.md
SCOPE: KB — SPC Pro Pack — Music Producer — Evaluation Rubric
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS
DOC_TYPE: EVALUATION_RUBRIC
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.RUBRIC.001
OWNER: SPC (Music Producer)
ROLE: Scoring rubric for producer outputs (O1/O2/O3) + pass thresholds + rework triggers.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Evaluation rubric initialized for Music Producer SPC pack."
- REASON: "Make quality measurable; prevent 'looks ok' acceptance."
- IMPACT: "Defines scoring dimensions, thresholds, and automatic REWORK triggers."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MPROD.RUBRIC.001

---

## PURPOSE (LAW)
Рубрика превращает “нормально/ненормально” в измерение.
Используется для:
- self-check перед выдачей,
- калибровки кейсов,
- решений PASS/REWORK/FAIL.

---

## SCORING SCALE (0–10)
- 0–3: FAIL (неиспользуемо)
- 4–6: BORDERLINE (нужен REWORK)
- 7–8: PASS (готово к работе)
- 9–10: EXCELLENT (почти эталон)

---

## PASS THRESHOLDS (MIN)
- Output O1 (PRODUCER_TASK_CARD): average >= 7, no dimension < 6
- Output O2 (PRODUCTION_EXEC_PLAN): average >= 7, no dimension < 6
- If O3 (VARIANTS_PLAN) exists: average >= 7, no dimension < 6

Automatic REWORK if any “hard fail trigger” fires (below).

---

## DIMENSIONS (D1–D9)

### D1 — Clarity & Actionability
Score criteria:
- 10: каждая инструкция исполнима, без двусмысленности, проверяема
- 7–8: почти всё исполнимо, 1–2 места можно уточнить
- 4–6: много “слов”, мало “что сделать”
- 0–3: непонятно, что делать

Hard fail trigger:
- ключевые deliverables неясны → REWORK

### D2 — Scope Discipline
Score criteria:
- 10: строго in-scope, out-of-scope корректно routed
- 7–8: мелкие лишние элементы, не мешают
- 4–6: роль смешана (инженерия/право/промпты)
- 0–3: явное нарушение лимитов

Hard fail trigger:
- выданы инженерные “рецепты” или юридические решения → FAIL

### D3 — Structural Blueprint Quality (sections/arc)
Score criteria:
- 10: карта секций + динамика + hook placement логичны и связаны с целью
- 7–8: структура норм, но слабее связка с целью/платформой
- 4–6: структура случайная/плоская
- 0–3: структуры нет или она противоречива

Hard fail trigger:
- O2 не содержит section map/arc → REWORK

### D4 — Arrangement / Seat Plan Coherence
Score criteria:
- 10: ясно “что где звучит и зачем”, риск маскирования учтён
- 7–8: план понятен, но не хватает 1–2 причин/контраста
- 4–6: перегруз/хаос, непонятно роли элементов
- 0–3: конфликт элементов, нет seat логики

Hard fail trigger:
- явные противоречия seat plan → REWORK

### D5 — Performance / Take Direction Quality
Score criteria:
- 10: конкретные указания по подаче + критерии приёма
- 7–8: полезно, но местами слишком общо
- 4–6: “эмоции” без действий
- 0–3: отсутствует/неприменимо

Hard fail trigger:
- если задача про вокал/исполнение, но нет take acceptance → REWORK

### D6 — Constraint Fit (platform/format)
Score criteria:
- 10: ограничения переведены в проверяемые правила
- 7–8: ограничения учтены, но часть не операционализирована
- 4–6: ограничения упомянуты, но не влияют на план
- 0–3: игнор ограничений

Hard fail trigger:
- конфликт ограничений не замечен → REWORK

### D7 — Validation Routing & Trace
Score criteria:
- 10: указан порядок CHK/GATE + PASS/REWORK/FAIL + минимальный trace
- 7–8: почти всё есть, мелкие пробелы
- 4–6: есть чеклисты, но нет route/trace
- 0–3: ничего не валидируется

Hard fail trigger:
- нет trace → REWORK

### D8 — Consistency & Terminology Stability
Score criteria:
- 10: термины стабильны, нет конфликтов, нет “дрейфа”
- 7–8: редкие мелкие расхождения
- 4–6: термины плавают, есть несостыковки
- 0–3: противоречия

Hard fail trigger:
- contradiction found → REWORK/FAIL (depending severity)

### D9 — Variant Safety (only if O3 exists)
Score criteria:
- 10: есть identity anchors + чётко что меняется/что нельзя менять
- 7–8: варианты норм, но anchors неполные
- 4–6: варианты уводят стиль/цель
- 0–3: варианты ломают идентичность

Hard fail trigger:
- variants drift identity → REWORK

---

## OVERALL DECISION RULE
- PASS:
  - all required outputs meet thresholds
  - no hard fail triggers
- REWORK:
  - any hard fail trigger OR average < 7 OR any dimension < 6
- FAIL:
  - hard limit violation (engineering recipe / legal determination)
  - repeated contradictions after 2 repair loops

---

## REQUIRED UID REFERENCES
- PASSPORT:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.PASSPORT.001
- PRINCIPLES:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.PRINCIPLES.001
- REGRESSION GUARD:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.REGRESSION_GUARD.001
- GATES:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CORE_QUALITY.001
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.GATE.CONSISTENCY.001

---
END
