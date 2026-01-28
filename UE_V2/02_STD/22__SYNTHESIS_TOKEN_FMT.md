# 22__SYNTHESIS_TOKEN_FMT

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: STD
UID: UE.V2.STD.SYNTHESIS_TOKEN_FMT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Формат SYNTHESIS_TOKEN — сборка лучшего варианта из прошлых попыток и отчётов.

---

## [M] INTENT
Фиксировать, как именно из набора вариантов и репортов собран "best-of" композит: что взято, что отброшено, почему, какие риски появились.

---

## [M] RULES
1) SYNTHESIS_TOKEN создаётся только после наличия:
   - OPTIONS_TOKEN / SELECTION_TOKEN
   - REPORT_TOKEN(QA) и/или REPORT_TOKEN(VAL/CTL)
   - ссылок на TOKEN_ARCHIVE
2) Синтез не создаёт "с нуля", а:
   - пересобирает компоненты
   - добавляет минимально нужные правки
3) Каждый перенос компонента обязан иметь SOURCE_REF.
4) Каждый отказ обязан иметь REASON (из REPORT/score).
5) После синтеза обязателен QA/VAL прогон.

---

## [M] SYNTHESIS_TOKEN_TEMPLATE
SYNTHESIS_TOKEN:
- TOKEN_ID:
- STEP_ID:
- DOMAIN: MUSIC
- ARTIFACT: TRACK|HOOK|LYRICS|MIX|MASTER
- INPUT_REFS:
  - OPTIONS_REF: (TOKEN_ID)
  - REPORT_REFS: (TOKEN_ID list)
  - ARCHIVE_REFS: (RUN_ID/STEP_ID list)
- WINNERS_TABLE (top 3):
  - CANDIDATE_ID: SCORE_TOTAL: KEY_STRENGTHS: KEY_WEAKNESSES
- COMPONENT_PICKLIST:
  - COMPONENT_TAG:
    - TAKE_FROM: CANDIDATE_ID
    - WHAT_EXACTLY: (1–2 строки)
    - WHY: (1–2 строки)
    - RISK: (optional)
- REMOVALS (0–10):
  - REMOVE: (что убрать) / WHY
- ADDITIONS (0–10):
  - ADD: (что добавить) / WHY
- COMPOSITE_SPEC:
  - SUMMARY (5–12 bullets): что должно получиться в композите
- EXPECTED_QA_OUTCOME:
  - target: PASS
  - watchouts: (0–5 bullets)
- NEXT_ACTION:
  - run: QA panel / VAL checks / FOCUS-LOOP if needed

---

## [M] GATES
PASS если:
- есть COMPONENT_PICKLIST + COMPOSITE_SPEC + NEXT_ACTION
REWORK если:
- нет источников (TAKE_FROM) или нет причин (WHY)
