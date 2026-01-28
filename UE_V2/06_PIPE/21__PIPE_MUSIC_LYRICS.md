# 21__PIPE_MUSIC_LYRICS

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: PIPE
UID: UE.V2.PIPE.MUSIC.LYRICS.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Пайп текста/лирики: концепт -> варианты -> проверка -> вписывание в трек.

---

## [M] INTENT
Делать тексты так, чтобы они:
- попадали в тему и психологию
- не были штампом/коллизией
- были удобны для вокала/ритма
- проходили PD/rights правила (если применимо)

---

## [M] STEP-RUN
STEP_00 BRIEF (тема/эмоция/персона/запреты)
STEP_01 PLAN (структура текста, схема рифм/ритма, coverage)
STEP_02 KB (лексикон, табу, голос, стиль)
STEP_03 OPTIONS (A–E куплет/припев/хук)
STEP_04 DECISION
STEP_05 PRODUCTION (сборка финала)
STEP_06 REVIEW (VAL: коллизии/PD-only; QA: узнаваемость/запоминаемость)
STEP_07 FIX (FOCUS-LOOP на проблемном месте)
STEP_08 PACK (lyrics pack: финальный текст + подсказки по исполнению)

---

## [M] GATES
PASS если:
- текст принят (QA) и нет коллизий/нарушений (VAL)
REWORK если:
- штамп/слабый хук/не ложится в ритм
GAP если:
- не хватает правил/лексикона/источников
