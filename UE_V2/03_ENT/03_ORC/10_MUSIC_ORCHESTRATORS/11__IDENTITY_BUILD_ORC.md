# 11__IDENTITY_BUILD_ORC

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: ORC
UID: UE.V2.ORC.MUSIC.IDENTITY_BUILD.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Оркестратор пайпа "ДНК артиста/группы": образ, тон, темы, табу, серийность, naming.

---

## [M] PURPOSE
Сделать Identity Pack, чтобы все будущие треки были консистентны и различимы.

---

## [M] INPUTS
- BRIEF_TOKEN (жанр/ценности/образ/аудитория)
- OPTIONAL: референсы бренда/визуала/лирики

---

## [M] OUTPUTS
- IDENTITY_PROFILE_TOKEN
- NAMING_RULES_TOKEN
- SERIES_POLICY_TOKEN
- PACK_TOKEN (identity pack)
- BASELINE_TOKEN

---

## [M] RULES
1) Следовать questions gate: максимум 3 вопроса, всегда дефолт.
2) Покрыть минимум Pillars: GOAL_FIT, EMOTION_PSYCH, UNIQUENESS, PACKAGING, COMPLIANCE.
3) Закрепить baseline: темы/табу/тон/лексика/названия/серийность.
4) Результат использовать как вход для TRACK_BUILD_STEP_ORC.

---

## [M] GATES
PASS если:
- профиль консистентен и различим (QA PASS) и закреплён baseline
REWORK если:
- "слишком общий" или конфликтует с naming/сериями
GAP если:
- нет нужных SPC/QA по покрытию
