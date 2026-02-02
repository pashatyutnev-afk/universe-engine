FILE: UE_V2/03_ENT/30_ORC_ENT/07_RESEARCH_ORC_ENT/03__RCH__SUMMARY_SYNTH__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 07_RESEARCH_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: RCH_ORC_ENT
UID: UE.V2.ENT.ORC.RCH.SUMMARY_SYNTH.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: RCH_SUMMARY_SYNTH
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.RCH.SUMMARY_SYNTH.001

## [M] PURPOSE
Синтезирует ответ из SOURCE_SET: структурно, с минимальными утверждениями, помечая предположения.
Не вставляет ссылки в пользовательский текст по умолчанию.

## [M] INPUTS / OUTPUTS
- Inputs: [SOURCE_SET, RESEARCH_BRIEF]
- Outputs: [SUMMARY_PACK, ASSUMPTIONS, FAIL_CODE?]

## [M] SUMMARY_PACK (schema)
- ANSWER (structured)
- KEY_POINTS
- UNCERTAINTIES
- ASSUMPTIONS
- WHAT_WOULD_CHANGE_MY_MIND (optional)

## [M] KB SCOPE
- KB Inputs: [source set token]
- KB Outputs: [summary pack]
- KB Boundaries: [без домыслов; помечать неопределённость]
- KB RAW refs: []

## [M] GATES
- PASS: вывод логичен и опирается на evidence set
- FAIL: evidence слабое и нет безопасного ответа

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Handoff: SUMMARY_PACK -> CITATION_POLICY_BRIDGE

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
