# 12__IDX_KB_MODULES_BY_TOPIC

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: KB / INDEX
UID: UE.V2.KB.IDX.MODULES_BY_TOPIC.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Индекс KB модулей по темам (Topics/Pillars). Для точечного выбора “что именно нужно” в рамках scope.

---

## [M] INTENT
Дать быстрый вход в KB по смысловой теме: хук/структура/палитра/микс/релиз/канон и т.д.
ORC использует это, когда домен известен, но нужна точная тема.

---

## [M] RULES
1) Выбор тем обязан соответствовать KB_SCOPE (DOMAIN_ALLOWED + SOURCES_ALLOWED).
2) PICKSET: максимум 7 модулей.
3) Тема → ведёт в малый индекс (семейство модулей), а не в список из сотен.

---

## [M] TOPIC MAP (STARTER, MUSIC FOCUSED)
MUSIC.HOOK:
- UE_V2/05_KB/10_TOPICS/50_SOUND_MUSIC/03__SOUND_MUSIC__HOOK_ENGINEERING.md
- UE_V2/05_KB/10_TOPICS/50_SOUND_MUSIC/14__SOUND_MUSIC__TRACK_FACTORY_ITERATION_LOG.md (если используешь как эталон целей)
- QA: UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/06__MUS__HOOK_PANEL__QA__ENT.md

MUSIC.STRUCTURE:
- UE_V2/05_KB/10_TOPICS/50_SOUND_MUSIC/07__SOUND_MUSIC__STRUCTURE_SONG_BLUEPRINTS.md

MUSIC.PALETTE:
- UE_V2/05_KB/10_TOPICS/50_SOUND_MUSIC/11__SOUND_MUSIC__GENRE_FUSION_FINGERPRINTS.md

MUSIC.PROMPT:
- UE_V2/05_KB/10_TOPICS/50_SOUND_MUSIC/01__SOUND_MUSIC__PROMPT_CONTRACTS.md
- CTL: UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS_CTL_ENT/01__MUS__PROMPT_CONTRACT__CTL__ENT.md

MUSIC.MIX_TRANSLATION:
- QA: UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/05__MUS__MIX_TRANSLATION__QA__ENT.md

MUSIC.UNIQUENESS:
- QA: UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/07__MUS__CATALOG_DIFFERENTIATION__QA__ENT.md
- VAL: UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/05__MUS__COLLISION_BLOCKER__VAL__ENT.md (если есть)

MUSIC.REGRESSION:
- QA: UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/09__MUS__REGRESSION_GUARD__QA__ENT.md

REL.METADATA:
- UE_V2/10_REL/04__SHEET_FMT.md
- UE_V2/10_REL/07__DROP_RULES.md

---

## [M] NOTE (IMPORTANT)
Этот файл — "карта тем". Если у тебя названия конкретных KB модулей отличаются:
- оставь темы (MUSIC.HOOK, MUSIC.MIX_TRANSLATION и т.д.)
- замени ссылки на реальные файлы.
Главное — чтобы тема вела в 1–3 модуля, не в 100.

---

## [M] GATES
PASS если:
- по теме можно быстро выбрать 1–3 модуля и собрать KB_TOKEN
GAP если:
- нужной темы нет -> добавить topic entry
REWORK если:
- тема ведёт в слишком много файлов
