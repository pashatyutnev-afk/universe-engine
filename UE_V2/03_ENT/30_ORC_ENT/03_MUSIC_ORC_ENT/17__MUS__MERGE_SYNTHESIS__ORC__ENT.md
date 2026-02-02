# 12__MERGE_SYNTHESIS_ORC

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: ORC
UID: UE.V2.ORC.MUSIC.MERGE_SYNTHESIS.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Оркестратор синтеза: анализирует все варианты и репорты, выбирает лучшее, собирает композит, запускает проверку.

---

## [M] PURPOSE
Не делать всё заново.
Собрать лучший композит из вариантов A/B/C… с учётом QA/VAL/CTL, и довести до PASS через точечные правки.

---

## [M] INPUTS
- OPTIONS_TOKEN или SELECTION_TOKEN
- REPORT_TOKEN(QA/VAL/CTL)
- TOKEN_ARCHIVE refs (успешные и неуспешные попытки)
- MODE (FAST|RELEASE_READY|MASTERPIECE)

---

## [M] OUTPUTS
- SCORE_TOKEN (если MODE != FAST)
- SYNTHESIS_TOKEN
- COMPOSITE_DRAFT_REF (как новая версия артефакта)
- NEXT_PROMPT ("го" или "ещё проход" если нужен focus)

---

## [M] FLOW (CANON)
F0 Collect:
- собрать кандидатов (top N) и их отчёты
- выделить fail flags и strengths

F1 Score:
- сформировать SCORE_TOKEN по рубрике (STD/23)

F2 Pick components:
- выбрать 4–8 переносов по COMPONENT_TAGS (STD/24)
- сформировать COMPONENT_PICKLIST

F3 Build composite:
- собрать COMPOSITE_SPEC и SYNTHESIS_TOKEN

F4 Validate composite:
- CTL: SYNTHESIS_MERGE_POLICY_CTL
- VAL: SYNTHESIS_COHERENCE_VAL
- QA: TRACK_QA_PANEL_QA (или доменная панель)

F5 Decide next:
- если PASS -> handoff на PACK/SIGNOFF
- если REWORK -> включить FOCUS-LOOP на проблемной зоне (hook/mix/lyrics) и повторить синтез

---

## [M] GATES
PASS если:
- есть SYNTHESIS_TOKEN и он прошёл VAL/QA
REWORK если:
- синтез дал конфликты и нужен focus loop
STOP если:
- отсутствуют входные варианты/репорты
