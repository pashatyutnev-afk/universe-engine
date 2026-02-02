FILE: UE_V2/03_ENT/50_VAL_ENT/90_SHARED_LIB_VAL_ENT/03__LIB__EVIDENCE_RULES__VAL__ENT.md
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT / 90_SHARED_LIB_VAL_ENT
DOC_TYPE: VAL_ENTITY
DOMAIN: LIB_VAL_ENT
UID: UE.V2.ENT.VAL.LIB.EVIDENCE_RULES.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: VAL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: LIB_EVIDENCE_RULES_VAL
- ENTITY_CLASS: VAL
- UID: UE.V2.ENT.VAL.LIB.EVIDENCE_RULES.001

## [M] PURPOSE
Правила evidence для VAL: что считается доказательством, когда использовать ASK вместо PASS/FAIL, и где границы “не угадывать”.

## [M] SCOPE
- TARGET_DOMAIN: MULTI
- APPLIES_TO: [ALL_VALIDATORS, ALL_REPORTS]
- NON_GOALS: [внешняя верификация, веб-поиск]

## [M] EVIDENCE TYPES (allowed)
- E.TYPE.TOKEN: явный токен/артефакт присутствует (например PROMPT_PACK, QA_REPORT).
- E.TYPE.TEXT: текст содержит прямую информацию (например header fields).
- E.TYPE.NOTES: структурированные notes (hook timing, variant notes, merge notes).
- E.TYPE.CHECKLIST: чеклист пройден (если он часть артефакта).
- E.TYPE.NONE: evidence отсутствует.

## [M] HARD RULES
- R1: PASS запрещён при E.TYPE.NONE на критической проверке.
- R2: Если вход отсутствует -> ASK (не FAIL), кроме случаев когда режим требует обязательный вход прямо сейчас.
- R3: FAIL требует:
  - либо явного нарушения правила/политики,
  - либо явного провала гейта при наличии входа.
- R4: WARN допустим при частичном evidence (есть вход, но не хватает детализации).
- R5: Evidence должно быть фактами: без предположений и без “кажется”.

## [M] DECISION MATRIX (evidence-first)
- IF required input missing -> ASK + REQUIRED_FIXES (provide input)
- IF rule violation evident -> FAIL + FAIL_CODE (RULE_VIOLATION)
- IF gate failed with evidence -> FAIL + FAIL_CODE (GATE_FAIL)
- IF evidence partial -> WARN + REQUIRED_FIXES
- ELSE -> PASS

## [M] REQUIRED FIXES (style)
- Минимальные, исполнимые, без лишних вопросов.
- Формат: 1–5 пунктов, каждый “что сделать/что дать”.

## [M] KB SCOPE
- KB Inputs: [validator context + artifacts]
- KB Outputs: [evidence classification guidance]
- KB Boundaries: [no guessing; no external sources]
- KB RAW refs: []

## [M] GATES
- PASS if: decisions align with evidence rules
- FAIL if: PASS/FAIL выставлен без допустимого evidence
