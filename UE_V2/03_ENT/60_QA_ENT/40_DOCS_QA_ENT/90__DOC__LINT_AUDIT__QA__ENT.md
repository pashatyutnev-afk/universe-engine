FILE: UE_V2/03_ENT/60_QA_ENT/40_DOCS_QA_ENT/90__DOC__LINT_AUDIT__QA__ENT.md
SCOPE: UE_V2 / 03_ENT / 60_QA_ENT / 40_DOCS_QA_ENT
DOC_TYPE: QA_ENTITY
DOMAIN: DOC_QA_ENT
UID: UE.V2.ENT.QA.DOC.LINT_AUDIT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: QA_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: DOC_LINT_AUDIT_QA
- ENTITY_CLASS: QA
- UID: UE.V2.ENT.QA.DOC.LINT_AUDIT.001

## [M] PURPOSE
Аудит документов: проверяет структуру, обязательные поля хедера, порядок секций и соблюдение правила RAW.
Не добавляет контент и не делает repo edits.

## [M] SCOPE
- TARGET_DOMAIN: DOC
- APPLIES_TO: [DOC_TEXT, DOC_TYPE_HINT?]
- NON_GOALS: [оценка фактов, внешний поиск]

## [M] INPUTS / OUTPUTS
- Inputs:
  - DOC_TEXT?: текст документа
  - DOC_TYPE_HINT?: ожидаемый тип/шаблон (если известен)
- Outputs:
  - QA_DECISION: PASS|WARN|ASK|FAIL
  - QA_FINDINGS: [findings]
  - REQUIRED_FIXES: [fixes]
  - ISSUES?: [issue tokens]
  - FAIL_CODE?: UE.FAIL.INPUT_ABSENT|UE.FAIL.GATE_FAIL|UE.FAIL.RULE_VIOLATION

## [M] CHECKS (minimum)
- C1: Header fields present:
  - FILE, SCOPE, DOC_TYPE, DOMAIN, UID, VERSION, STATUS, MODE, OWNER.
- C2: Section presence:
  - PURPOSE + HARD_RULES (или эквивалент по шаблону),
  - KB SCOPE (если это SPC/README стандарт) — optional warn если отсутствует.
- C3: RAW compliance:
  - RAW ссылки допускаются только в INDEX_MANIFEST.
- C4: Contract compliance:
  - PIPELINE_CONTRACT не содержит RAW.
- C5: Determinism:
  - Есть REQUIRED_KEYS / REQUIRED / SELF (если это индекс/контракт).

## [M] DECISION_MATRIX
- IF DOC_TEXT отсутствует -> ASK (V.DOCQA.NO_INPUT)
- IF missing critical header fields -> FAIL (UE.FAIL.GATE_FAIL; V.DOCQA.MISSING_HEADER)
- IF RAW outside INDEX_MANIFEST -> FAIL (UE.FAIL.RULE_VIOLATION; V.DOCQA.RAW_OUTSIDE_INDEX)
- IF contract has RAW -> FAIL (UE.FAIL.RULE_VIOLATION; V.DOCQA.CONTRACT_HAS_RAW)
- IF sections missing but recoverable -> WARN (V.DOCQA.MISSING_SECTIONS)
- ELSE -> PASS

## [M] VIOLATIONS
- V.DOCQA.NO_INPUT
- V.DOCQA.MISSING_HEADER
- V.DOCQA.MISSING_SECTIONS
- V.DOCQA.RAW_OUTSIDE_INDEX
- V.DOCQA.CONTRACT_HAS_RAW

## [M] FAIL_CODES
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.GATE_FAIL
- UE.FAIL.RULE_VIOLATION

## [M] REQUIRED_FIXES (style)
- 1–7 пунктов, каждый “что исправить” + “где”.
- Без лишних вопросов, только действия.

## [M] KB SCOPE
- KB Inputs: [doc text + type hint]
- KB Outputs: [lint audit findings + fixes]
- KB Boundaries: [no guessing; no repo edits]
- KB RAW refs: []

## [M] GATES
- PASS if: структура валидна и RAW правило соблюдено
- FAIL if: критические поля отсутствуют или RAW правило нарушено

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, CTL_ENT, VAL_ENT]
- Handoff rules:
  - ASK -> запросить DOC_TEXT
  - WARN -> вернуть REQUIRED_FIXES и recheck
  - FAIL -> стоп до исправления
