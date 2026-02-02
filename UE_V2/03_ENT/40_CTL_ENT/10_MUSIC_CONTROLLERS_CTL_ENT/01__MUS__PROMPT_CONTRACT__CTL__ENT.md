FILE: UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS_CTL_ENT/01__MUS__PROMPT_CONTRACT__CTL__ENT.md
SCOPE: UE_V2 / 03_ENT / 40_CTL_ENT / 10_MUSIC_CONTROLLERS_CTL_ENT
DOC_TYPE: CTL_ENTITY
DOMAIN: MUS_CTL_ENT
UID: UE.V2.ENT.CTL.MUS.PROMPT_CONTRACT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: CTL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_PROMPT_CONTRACT_CTL
- ENTITY_CLASS: CTL
- UID: UE.V2.ENT.CTL.MUS.PROMPT_CONTRACT.001

## [M] PURPOSE
Стандартизирует PROMPT_PACK и запрещает опасные паттерны копирования. Пунктуация без восклицаний.

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [PROMPT_PACK, MAIN_PROMPT, NEGATIVE_PROMPT, LYRICS]
- NON_GOALS: [оценка аудио, права/PD, коллизии]

## [M] INPUTS / OUTPUTS
- Inputs: [MUS_BRIEF, STYLE_ROUTE_TOKEN, LYRICS_FINAL?]
- Outputs: [CTL_DECISION, CTL_FINDINGS, REQUIRED_FIXES, FAIL_CODE?]

## [M] RULESET
- R1: PROMPT_PACK обязан содержать MAIN_PROMPT и NEGATIVE_PROMPT.
- R2: MAIN_PROMPT обязан фиксировать genre/substyle, tempo band, energy, vocal rule, structure hint.
- R3: NEGATIVE_PROMPT обязан содержать запрет прямого копирования.
- R4: В текстах и промптах запрещены восклицательные знаки.
- R5: Запрещено требование сделать один в один под конкретного артиста/трек.

## [M] DECISION_MATRIX
- IF отсутствует MUS_BRIEF -> ASK
- IF отсутствует STYLE_ROUTE_TOKEN -> ASK
- IF нет секций MAIN/NEGATIVE -> FAIL (UE.FAIL.RULE_VIOLATION)
- IF найден запретный паттерн копирования -> FAIL (UE.FAIL.RULE_VIOLATION)
- IF нарушена пунктуация -> WARN
- ELSE -> PASS

## [M] VIOLATIONS
- V.PROMPT.MISSING_SECTION — нет MAIN/NEGATIVE
- V.PROMPT.DIRECT_COPY — запрос на копирование
- V.PROMPT.PUNCT — нарушена пунктуационная политика

## [M] FAIL_CODES
- UE.FAIL.RULE_VIOLATION
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.GATE_FAIL

## [M] KB SCOPE
- KB Inputs: [brief/style tokens]
- KB Outputs: [ctl findings + fixes]
- KB Boundaries: [не выдумывать стиль/цели без входа]
- KB RAW refs: []

## [M] GATES
- PASS if: PROMPT_PACK структурно валиден и без запретных паттернов
- FAIL if: прямое копирование или отсутствует базовая структура

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, QA_ENT, VAL_ENT]
- Handoff rules: FAIL -> stop; WARN -> fix loop; PASS -> continue
