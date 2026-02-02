FILE: UE_V2/03_ENT/60_QA_ENT/90_SHARED_LIB_QA_ENT/03__LIB__QA_EVIDENCE_REQUIREMENTS__QA__ENT.md
SCOPE: UE_V2 / 03_ENT / 60_QA_ENT / 90_SHARED_LIB_QA_ENT
DOC_TYPE: QA_ENTITY
DOMAIN: LIB_QA_ENT
UID: UE.V2.ENT.QA.LIB.EVIDENCE_REQUIREMENTS.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: QA_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: QA_EVIDENCE_REQUIREMENTS_LIB
- ENTITY_CLASS: QA
- UID: UE.V2.ENT.QA.LIB.EVIDENCE_REQUIREMENTS.001

## [M] PURPOSE
Правила evidence для QA: когда ставить ASK, когда WARN, когда FAIL.
Главное: не угадывать и не выдавать PASS без входов.

## [M] EVIDENCE TYPES (allowed)
- E.TYPE.TOKEN: есть явный токен/артефакт (TRACK_TOKEN, HTML_BUNDLE, DOC_TEXT).
- E.TYPE.NOTES: есть структурированные notes (baseline/current, panel notes).
- E.TYPE.TEXT: есть проверяемый текст/код.
- E.TYPE.NONE: входов нет.

## [M] HARD RULES
- R1: PASS запрещён при E.TYPE.NONE.
- R2: Если нет входа -> ASK (по умолчанию).
- R3: FAIL ставить только при наличии evidence провала (или policy break).
- R4: WARN допустим при частичном evidence или при “исполнимых” проблемах без блокировки.
- R5: REQUIRED_FIXES всегда конкретные (1–7 пунктов), без лишних вопросов.

## [M] DECISION MATRIX (evidence-first)
- IF E.TYPE.NONE -> ASK + REQUIRED_FIXES (что дать)
- IF rule violation evident -> FAIL + UE.FAIL.RULE_VIOLATION
- IF gate failed with evidence -> FAIL + UE.FAIL.GATE_FAIL
- IF evidence partial / non-critical issues -> WARN + REQUIRED_FIXES
- ELSE -> PASS

## [M] GATES
- PASS if: QA decisions align with evidence rules
- FAIL if: PASS/FAIL выставлен без допустимого evidence
