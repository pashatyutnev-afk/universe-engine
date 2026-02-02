FILE: UE_V2/03_ENT/50_VAL_ENT/40_DOCS_VAL_ENT/90__DOC__LINT_MIN__VAL__ENT.md
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT / 40_DOCS_VAL_ENT
DOC_TYPE: VAL_ENTITY
DOMAIN: DOC_VAL_ENT
UID: UE.V2.ENT.VAL.DOC.LINT_MIN.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: VAL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: DOC_LINT_MIN_VAL
- ENTITY_CLASS: VAL
- UID: UE.V2.ENT.VAL.DOC.LINT_MIN.001

## [M] PURPOSE
Минимальный lint для документов: проверяет наличие хедера, обязательных секций и отсутствие RAW вне INDEX_MANIFEST.

## [M] SCOPE
- TARGET_DOMAIN: DOC
- APPLIES_TO: [DOC_TEXT, DOC_TYPE_HINT?]
- NON_GOALS: [факты, качество содержания, внешний поиск]

## [M] INPUTS / OUTPUTS
- Inputs:
  - DOC_TEXT?: текст документа
  - DOC_TYPE_HINT?: ожидаемый DOC_TYPE/шаблон
- Outputs:
  - VAL_DECISION: PASS|FAIL|WARN|ASK
  - VAL_FINDINGS: [findings]
  - REQUIRED_FIXES: [fixes]
  - VIOLATIONS: [violation ids]
  - FAIL_CODE?: UE.FAIL.INPUT_ABSENT|UE.FAIL.GATE_FAIL|UE.FAIL.RULE_VIOLATION

## [M] CHECKS
- C1: Есть FILE/SCOPE/DOC_TYPE/UID/VERSION/STATUS/MODE/OWNER в хедере.
- C2: Есть секции PURPOSE и HARD_RULES (если doc governance-типа) или эквивалент по шаблону.
- C3: Нет RAW ссылок, если DOC_TYPE не INDEX_MANIFEST.
- C4: Есть SELF в INDEX_MANIFEST (если проверяется индекс).
- C5: Разделы не перепутаны (например, CONTRACT не содержит RAW).

## [M] EVIDENCE_REQUIREMENTS
- E1: PASS возможен только при наличии DOC_TEXT.
- E2: Если doc_type_hint задан и структура не совпадает -> WARN или FAIL по критичности.
- E3: RAW вне индекса -> FAIL.

## [M] DECISION_MATRIX
- IF DOC_TEXT отсутствует -> ASK (V.DOC.NO_INPUT)
- IF missing critical header fields -> FAIL (UE.FAIL.GATE_FAIL; V.DOC.MISSING_HEADER)
- IF RAW detected outside INDEX_MANIFEST -> FAIL (UE.FAIL.RULE_VIOLATION; V.DOC.RAW_OUTSIDE_INDEX)
- IF sections missing but recoverable -> WARN (V.DOC.MISSING_SECTIONS)
- ELSE -> PASS

## [M] VIOLATIONS
- V.DOC.NO_INPUT
- V.DOC.MISSING_HEADER
- V.DOC.MISSING_SECTIONS
- V.DOC.RAW_OUTSIDE_INDEX
- V.DOC.CONTRACT_HAS_RAW

## [M] FAIL_CODES
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.GATE_FAIL
- UE.FAIL.RULE_VIOLATION

## [M] KB SCOPE
- KB Inputs: [doc text, doc_type_hint]
- KB Outputs: [lint findings + required fixes]
- KB Boundaries: [не дописывать документ за автора; не менять репо]
- KB RAW refs: []

## [M] GATES
- PASS if:
  - хедер валиден
  - RAW правило не нарушено
  - минимальные секции присутствуют
- FAIL if:
  - нет хедера или RAW вне индекса

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, CTL_ENT, QA_ENT]
- Handoff rules:
  - WARN -> вернуть REQUIRED_FIXES
  - ASK -> запросить DOC_TEXT
  - FAIL -> стоп до исправления
