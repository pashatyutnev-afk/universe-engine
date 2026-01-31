# LAW_18

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: LAW
UID: UE.V2.LAW.18.MUST_LOAD_MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: RUNTIME_MANIFEST обязателен: без MUST_LOAD ядра запуск запрещён.

---

## [M] INTENT
Гарантировать, что система не пройдёт мимо REG/XREF/KB/PIPE/NAV/LOG и будет работать одинаково каждый раз.

---

## [M] RULES
1) Перед выполнением любой задачи MUST_LOAD_SET должен быть доступен.
2) MUST_LOAD_SET определяет минимальные документы:
   - STD: markers, nav rules, gates, noise budget
   - NAV: nav root + базовые IDX
   - PIPE: default + gap + readiness/noise + val/qa/signoff
   - KB: start + rules + inputs/outputs
   - LOG: log rules + run log
3) Если любой MUST_LOAD missing → STOP.
4) Если MUST_LOAD документы слишком большие и не помещаются в лимит → REWORK (уплотнить).
5) MUST_LOAD не расширяется произвольно. Любое расширение — через CHANGE_LOG.

---

## [M] GATES
PASS если:
- MUST_LOAD_SET доступен и используется по необходимости
REWORK если:
- MUST_LOAD раздули без причины
STOP если:
- missing MUST_LOAD
