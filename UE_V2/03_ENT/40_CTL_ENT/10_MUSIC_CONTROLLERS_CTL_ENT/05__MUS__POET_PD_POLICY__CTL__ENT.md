FILE: UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS_CTL_ENT/05__MUS__POET_PD_POLICY__CTL__ENT.md
SCOPE: UE_V2 / 03_ENT / 40_CTL_ENT / 10_MUSIC_CONTROLLERS_CTL_ENT
DOC_TYPE: CTL_BLOCKER
DOMAIN: MUS_CTL_ENT
UID: UE.V2.ENT.CTL.MUS.POET_PD_POLICY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: CTL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] BLOCKER_HEADER
- BLOCKER_NAME: MUS_POET_PD_POLICY
- BLOCKER_CLASS: CTL_BLOCKER
- UID: UE.V2.ENT.CTL.MUS.POET_PD_POLICY.001
- SEVERITY: BLOCK
- DEFAULT_ACTION: FAIL
- STATUS: ACTIVE

## [M] PURPOSE
Блокирует риск копирования и не-PD требования. Принцип: оригинальность и безопасные формулировки.

## [M] TRIGGERS
- T1: Требование сделать один в один под конкретный трек/артиста.
- T2: Прямая вставка узнаваемых строк чужих текстов.
- T3: Явная инструкция копировать мелодию, ритм, аранжировку как у конкретного произведения.

## [M] REQUIRED_FIXES
- Fix1: Переформулировать запрос как “в стиле принципов” без копирования.
- Fix2: Убрать прямые цитаты и заменить на оригинальные строки.
- Fix3: Дать собственный текст или тему, вместо внешнего произведения.

## [M] OVERRIDE_POLICY
- OVERRIDE_ALLOWED: false
- OVERRIDE_REQUIREMENTS: []
- OVERRIDE_LOGGING: []

## [M] VIOLATIONS
- V.PD.DIRECT_COPY — прямое копирование
- V.PD.QUOTE_LYRICS — узнаваемые строки
- V.PD.MELODY_CLONE — клон мелодии/аранжа

## [M] FAIL_CODES
- UE.FAIL.RULE_VIOLATION

## [M] KB SCOPE
- KB Inputs: [brief, prompts, lyrics]
- KB Outputs: [block decision + required fixes]
- KB Boundaries: [no guessing; no external copying]
- KB RAW refs: []

## [M] GATES
- PASS if: ни один trigger не сработал
- FAIL if: любой trigger сработал

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, QA_ENT, VAL_ENT]
- Handoff rules: FAIL -> stop and return REQUIRED_FIXES
