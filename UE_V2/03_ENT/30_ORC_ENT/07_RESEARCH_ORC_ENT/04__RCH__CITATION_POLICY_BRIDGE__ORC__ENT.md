FILE: UE_V2/03_ENT/30_ORC_ENT/07_RESEARCH_ORC_ENT/04__RCH__CITATION_POLICY_BRIDGE__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 07_RESEARCH_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: RCH_ORC_ENT
UID: UE.V2.ENT.ORC.RCH.CITATION_POLICY_BRIDGE.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: RCH_CITATION_POLICY_BRIDGE
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.RCH.CITATION_POLICY_BRIDGE.001

## [M] PURPOSE
Применяет политику цитирования: решает, когда ссылки обязательны и как их хранить (внутренне/внешне).
По умолчанию: ссылки не показывать пользователю, если это не требуется явно.

## [M] INPUTS / OUTPUTS
- Inputs: [SUMMARY_PACK, TRIAGE_REPORT, USER_CITATION_REQUEST?]
- Outputs: [CITATION_MODE, CITATION_PACK?, FAIL_CODE?]

## [M] CITATION_MODES
- NONE: no citations shown and none attached
- HIDDEN: citations stored internally for audit/trust but not shown
- ATTACH: citations attached to output (only when required or requested)

## [M] GATES
- PASS: режим выбран и совместим с запросом
- FAIL: если политика требует citations, но источник отсутствует

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA, CTL]
- Handoff: CITATION_MODE/CITATION_PACK -> PIPELINE_CONTRACT output packaging

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
