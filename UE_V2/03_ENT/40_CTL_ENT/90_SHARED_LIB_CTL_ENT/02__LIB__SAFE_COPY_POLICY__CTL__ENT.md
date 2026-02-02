FILE: UE_V2/03_ENT/40_CTL_ENT/90_SHARED_LIB_CTL_ENT/02__LIB__SAFE_COPY_POLICY__CTL__ENT.md
SCOPE: UE_V2 / 03_ENT / 40_CTL_ENT / 90_SHARED_LIB_CTL_ENT
DOC_TYPE: CTL_BLOCKER
DOMAIN: LIB_CTL_ENT
UID: UE.V2.ENT.CTL.LIB.SAFE_COPY_POLICY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: CTL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] BLOCKER_HEADER
- BLOCKER_NAME: LIB_SAFE_COPY_POLICY
- BLOCKER_CLASS: CTL_BLOCKER
- UID: UE.V2.ENT.CTL.LIB.SAFE_COPY_POLICY.001
- SEVERITY: BLOCK
- DEFAULT_ACTION: FAIL
- STATUS: ACTIVE

## [M] PURPOSE
Жёсткий блокер прямого копирования. Разрешены только “принципы” и оригинальные формулировки.

## [M] TRIGGERS
- T1: Просьба “сделай один в один”, “так же как”, “копируй” с указанием конкретного произведения/исполнителя.
- T2: Вставка узнаваемых строк/фраз из чужих текстов.
- T3: Инструкция воспроизвести мелодию/аранжировку как у конкретного трека.

## [M] REQUIRED_FIXES
- Fix1: Убрать конкретные референсы копирования, заменить на принципы.
- Fix2: Переписать цитаты в оригинальные строки.
- Fix3: Уточнить цель/вайб/жанровые принципы без сравнения с конкретной работой.

## [M] OVERRIDE_POLICY
- OVERRIDE_ALLOWED: false
- OVERRIDE_REQUIREMENTS: []
- OVERRIDE_LOGGING: []

## [M] FAIL_CODES
- UE.FAIL.RULE_VIOLATION

## [M] KB SCOPE
- KB Inputs: [task text, drafts]
- KB Outputs: [block decision + fixes]
- KB Boundaries: [не выдавать копируемый контент]
- KB RAW refs: []

## [M] GATES
- PASS if: ни один trigger не сработал
- FAIL if: любой trigger сработал

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, QA_ENT, VAL_ENT]
- Handoff rules: FAIL -> stop and return REQUIRED_FIXES
