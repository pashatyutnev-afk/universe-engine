# KB — ENTITY↔KB CONNECTOR IMPLEMENTATION TEMPLATE (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/38__KB_CONNECTOR_IMPLEMENTATION_TEMPLATE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: TEMPLATE
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TPL.ENTITY_KB_CONNECTOR.038
OWNER: SYSTEM
ROLE: Copy-paste template for implementing the Entity↔KB connector inside any entity document: required scopes, selection map UIDs, access policy, and mandatory trace output blocks (UID-only, no URL/PATH).

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created implementation template for Entity↔KB connector blocks."
- REASON: "Entities need a standardized connector block to declare KB dependencies and enforce deterministic KB intake."
- IMPACT: "Faster entity onboarding; fewer KB intake errors; consistent traceability."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TPL.038

---

## 0) PURPOSE (KB)
Provide a standard connector block to embed into entity docs.

Rule:
- This template is used in entity files; it is not a navigation mechanism.

---

## 1) CONNECTOR BLOCK (COPY)
ENTITY_KB_CONNECTOR:
- ENTITY_UID: <ENTITY_UID>
- ENTITY_CLASS: SPC | ENG | ORC | CTL | VAL | QA | XREF
- PRIMARY_DOMAIN_SCOPE: KB_SCOPE.TOPICS.<DOMAIN>
- REQUIRED_SCOPES:
  - KB_SCOPE.GOVERNANCE
  - KB_SCOPE.TOPICS.<DOMAIN>
- OPTIONAL_SCOPES:
  - KB_SCOPE.TOPICS.REFERENCE
  - KB_SCOPE.TOPICS.META
  - KB_SCOPE.TOPICS.PRODUCTION  (if pipeline/packaging involved)
  - KB_SCOPE.MAPS.TASK_SCOPE    (if task-based scope selection used)
- SELECTION_MAP_UIDS:
  - UE.KB.MAP.ENTITY_SCOPE.002 | WHY: entity→scope selection baseline
  - UE.KB.MAP.TASK_SCOPE.001   | WHY: task→scope selection (if task classification required)
- GOVERNANCE_MIN_SET_UID:
  - UE.KB.STD.SCOPE.GOVERNANCE_MIN.009 | WHY: mandatory governance baseline
- ACCESS_POLICY_UID:
  - UE.KB.POL.ENTITY_ACCESS.031 | WHY: status-based access control for KB consumption
- XREF_RULES_UID:
  - UE.KB.DICT.XREF_RULES.005 | WHY: UID-only crossref constraints
- REL_TYPES_UID (if REL used):
  - UE.KB.DICT.REL_TYPES.004 | WHY: canonical relation vocabulary
- WEB_LOOKUP_NOTICE_UID (if web lookup used):
  - UE.KB.TPL.WEB_LOOKUP_NOTICE.035 | WHY: mandatory disclosure if browsing used

RUN_BEHAVIOR:
- ACTIVE_FIRST: YES
- ALLOW_DRAFT_IF_NO_ACTIVE: YES/NO
- MEMORY_REUSE_ALLOWED: YES/NO
- DEPRECATED_AUTHORITY_ALLOWED: NO (pointer-only resolution OK)

---

## 2) TRACE OUTPUT BLOCK (COPY)
KB_SOURCES:
- XREF: <KB_MODULE_UID> | WHY: <used for>
- XREF: <KB_MODULE_UID> | WHY: <used for>
MEMORY_REUSE: YES/NO
STATUS_USED: ACTIVE_ONLY | MIXED
WEB_LOOKUP_USED: YES/NO

If WEB_LOOKUP_USED: YES
- include WEB_LOOKUP_NOTICE (use template UE.KB.TPL.WEB_LOOKUP_NOTICE.035)

---

## 3) VALIDATION (PASS/FAIL)
PASS IF:
- connector includes governance min set UID
- connector uses only UIDs (no URL/PATH)
- connector names required scopes + selection map UIDs
- trace block included

FAIL IF:
- governance omitted
- ad-hoc browsing implied as default
- any URL/PATH present
- deprecated modules treated as authority

---

## 4) HARD FAIL CONDITIONS
FAIL IF:
- ENTITY_UID missing
- PRIMARY_DOMAIN_SCOPE missing
- GOVERNANCE_MIN_SET_UID missing
- ACCESS_POLICY_UID missing

---

## 5) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.ENTITY_KB_CONNECTOR.037 | WHY: connector requirements baseline
- XREF: UE.KB.POL.ENTITY_ACCESS.031 | WHY: access control rules
- XREF: UE.KB.STD.SCOPE.GOVERNANCE_MIN.009 | WHY: governance baseline
- XREF: UE.KB.DICT.XREF_RULES.005 | WHY: uid-only crossref rules

--- END.
