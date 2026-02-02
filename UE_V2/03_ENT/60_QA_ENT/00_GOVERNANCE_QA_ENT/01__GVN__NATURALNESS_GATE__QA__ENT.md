FILE: UE_V2/03_ENT/60_QA_ENT/00_GOVERNANCE_QA_ENT/01__GVN__NATURALNESS_GATE__QA__ENT.md
SCOPE: UE_V2 / 03_ENT / 60_QA_ENT / 00_GOVERNANCE_QA_ENT
DOC_TYPE: QA_ENTITY
DOMAIN: GVN_QA_ENT
UID: UE.V2.ENT.QA.GVN.NATURALNESS_GATE.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: QA_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: GVN_NATURALNESS_GATE_QA
- ENTITY_CLASS: QA
- UID: UE.V2.ENT.QA.GVN.NATURALNESS_GATE.001

## [M] PURPOSE
Минимальный гейт “естественности” для текста/описаний/инструкций.
Ловит роботизированный тон, мусорные повторения, бессмысленные вставки, и ломающееся форматирование.

## [M] SCOPE
- TARGET_DOMAIN: MULTI
- APPLIES_TO: [ANSWER_TEXT, DOC_TEXT, PROMPT_TEXT, README_TEXT]
- NON_GOALS: [оценка фактов через внешние источники, художественный вкус]

## [M] INPUTS / OUTPUTS
- Inputs: [ARTIFACT_TEXT?]
- Outputs:
  - QA_DECISION: PASS|WARN|ASK|FAIL
  - QA_FINDINGS: [findings]
  - REQUIRED_FIXES: [fixes]
  - ISSUES?: [issue tokens]
  - FAIL_CODE?: <optional>

## [M] CHECKS
- C1: Вход есть (не пусто).
- C2: Нет повторяющихся фраз/абзацев без смысла (spam-like).
- C3: Нет “воды” и пустых утверждений вместо конкретики (если документ должен быть процедурным).
- C4: Форматирование не сломано (заголовки/списки/код-блоки согласованы).
- C5: Нет запрещённой пунктуации в контексте, где это правило действует (например, “!” в трековых промптах).

## [M] DECISION_MATRIX
- IF ARTIFACT_TEXT отсутствует -> ASK (UE.FAIL.INPUT_ABSENT)
- IF формат критично сломан -> FAIL (UE.FAIL.GATE_FAIL)
- IF повтор/мусор выраженный -> WARN
- IF тон роботизированный и мешает исполнению -> WARN
- ELSE -> PASS

## [M] VIOLATIONS
- V.QA.NAT.NO_INPUT
- V.QA.NAT.REPEAT_SPAM
- V.QA.NAT.FLAT_ROBOTIC
- V.QA.NAT.FORMAT_BROKEN

## [M] FAIL_CODES
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.GATE_FAIL

## [M] KB SCOPE
- KB Inputs: [artifact text]
- KB Outputs: [naturalness findings + fixes]
- KB Boundaries: [не добавлять новые требования вне входа]
- KB RAW refs: []

## [M] GATES
- PASS if: текст исполним, без мусора и без сломанного формата
- FAIL if: формат ломает исполнение или документ непригоден

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, CTL_ENT, VAL_ENT]
- Handoff rules:
  - WARN -> правки текста, затем recheck
  - FAIL -> стоп до исправления
  - ASK -> запросить минимальный вход
