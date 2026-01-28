# 22__PIPE_MUSIC_IDENTITY

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: PIPE
UID: UE.V2.PIPE.MUSIC.IDENTITY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Пайп "ДНК артиста/группы": образ, тон, темы, ограничения, naming, релизные правила.

---

## [M] INTENT
Создать стабильную "матрицу личности" артиста/группы, чтобы:
- треки не были рандомом
- стиль держался сериями
- naming/обложки/описания были едиными
- маркетинг/психология были встроены

---

## [M] STEP-RUN
STEP_00 BRIEF (жанры, ценности, образ, аудитория)
STEP_01 PLAN (что постоянно / что переменно, coverage)
STEP_02 KB (словарь/темы/табу/референсы)
STEP_03 OPTIONS (3–5 концептов ДНК)
STEP_04 DECISION (выбор ДНК)
STEP_05 PRODUCTION (IDENTITY_PROFILE v1)
STEP_06 REVIEW (QA: консистентность, differentiation; VAL: naming collision)
STEP_07 FIX (FOCUS-LOOP на слабом месте)
STEP_08 PACK (Identity Pack + правила серии)

---

## [M] OUTPUTS
- IDENTITY_PROFILE_TOKEN
- NAMING_RULES_TOKEN
- SERIES_POLICY_TOKEN

---

## [M] GATES
PASS если:
- профиль консистентен и различим (QA PASS)
REWORK если:
- "слишком общий" или конфликтует с naming/сериями
GAP если:
- нет нужных SPC/QA по маркетингу/психологии/уникальности
