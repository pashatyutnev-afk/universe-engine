# 15__STEP_TOKEN_SET

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: STD
UID: UE.V2.STD.STEP_TOKEN_SET.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Единый набор токенов, которыми система фиксирует прогресс по шагам.

---

## [M] INTENT
Свести длинные процессы к коротким токенам, чтобы контекст не раздувался, а результат был воспроизводим.

---

## [M] TOKEN_TYPES (REQUIRED)
1) BRIEF_TOKEN
- что делаем, для кого, формат, ограничения, критерии успеха

2) PLAN_TOKEN
- этапы, режим (быстро/шедевр), бюджеты, кто участвует, какие гейты обязательны

3) ROUTE_TOKEN
- DOMAIN, ARTIFACT_TYPE, PIPE_SELECTED, REQUIRED_IDX, REQUIRED_VALIDATION

4) KB_TOKEN
- что нужно знать, какие правила применяем, какие источники разрешены, запреты

5) OPTIONS_TOKEN
- варианты A/B/C… с отличиями и рисками

6) DECISION_TOKEN
- что выбрано, почему, что отброшено, какие компромиссы

7) REPORT_TOKEN
- CTL/VAL/QA результаты: PASS/REWORK + список конкретных проблем

8) DELTA_TOKEN
- что изменили относительно предыдущей версии, почему, чем улучшилось

9) PACK_TOKEN
- финальная упаковка: что готово, что приложено, чеклисты экспорта/публикации

---

## [M] OPTIONAL_TOKENS
- FOCUS_TOKEN (для FOCUS-LOOP): формулировка одного узкого фокуса
- TEAM_TOKEN: какая партия сущностей работала в этом проходе
- TRACE_TOKEN: список участников и их вкладов (ID токенов)
- SCORE_TOKEN: оценка вариантов по рубрике
- BASELINE_TOKEN: закрепление эталона для регрессии

---

## [M] TOKEN_MIN_FORMAT (COMMON)
Каждый токен обязан иметь:
- TOKEN_ID
- STEP_ID
- DOMAIN
- ARTIFACT_TYPE (если применимо)
- VERSION_TAG (v1, v2… или baseline)
- SUMMARY (3–10 строк)
- LINKS (optional: ссылки на другие токены)

---

## [M] GATES
PASS если:
- для STEP есть минимум: ROUTE_TOKEN + один из (BRIEF/OPTIONS/REPORT/DELTA/PACK) по смыслу шага
REWORK если:
- токены дублируют друг друга без изменений
STOP если:
- нет ROUTE_TOKEN и непонятно куда движемся
