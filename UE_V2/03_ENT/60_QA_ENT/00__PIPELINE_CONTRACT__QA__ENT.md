FILE: UE_V2/03_ENT/60_QA_ENT/00__PIPELINE_CONTRACT__QA__ENT.md
SCOPE: UE_V2 / 03_ENT / 60_QA_ENT
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: QA_ENT
UID: UE.V2.ENT.PIPE.QA_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: QA_ENT
NAV_RULE: Contract has no RAW

---

## [M] PURPOSE
QA PIPELINE_CONTRACT — корневой роутер QA слоя.
Определяет, какой QA-реалм использовать (GVN/MUS/VID/WEB/DOC/LIB) и какой контракт вернуть.
RAW не хранит: всё через KEY и INDEX_MANIFEST.

## [M] HARD_RULES
- RAW запрещён внутри CONTRACT.
- Все ссылки: только KEYS.
- MODE REPO: никаких правок репозитория.
- Выход: TARGET_REALM_KEY + TARGET_PIPE_KEY + ROUTE_HINT_KEYS?.

## [M] REQUIRED_KEYS
- INDEX_MANIFEST
- PIPELINE_CONTRACT
- REALM.GVN_QA
- REALM.MUS_QA
- REALM.VID_QA
- REALM.WEB_QA
- REALM.DOC_QA
- REALM.LIB_QA
- QA.NATURALNESS_GATE
- QA.CREATE_FLOW

## [M] ROUTING (keys only)
- If request mentions governance / gates / issue lifecycle / qa flow -> REALM.GVN_QA
- If request mentions music / track / hook / mix / loop / scroll stop -> REALM.MUS_QA
- If request mentions video / shot / export / style switches -> REALM.VID_QA
- If request mentions web / html / css / js / a11y audit -> REALM.WEB_QA
- If request mentions docs / readme / lint / manifest / contract -> REALM.DOC_QA
- If request mentions severity / fail codes / evidence requirements -> REALM.LIB_QA
- If request explicitly says “naturalness gate (root)” -> QA.NATURALNESS_GATE (standalone)
- If request explicitly says “create flow (root)” -> QA.CREATE_FLOW (standalone)
- Else -> default by artifact hints:
  - TRACK_TOKEN / lyrics / music notes -> REALM.MUS_QA
  - SHOT_PLAN / VID_BRIEF -> REALM.VID_QA
  - HTML_BUNDLE -> REALM.WEB_QA
  - DOC_TEXT -> REALM.DOC_QA
  - Otherwise -> REALM.GVN_QA (safe governance default)

## [M] STEP-RUN
- STEP: S0
  GOAL: Determine target realm for QA
  INPUTS: [TASK_TEXT, ARTIFACT_HINTS?]
  TARGETS: [INDEX_MANIFEST]
  ACTIONS:
    - Classify intent using ROUTING rules
    - Output TARGET_REALM_KEY (or ROOT_ENTITY_KEY for standalone)
  OUTPUTS: [TARGET_REALM_KEY?, ROOT_ENTITY_KEY?]
  CHECKS: []
  FAIL: UE.FAIL.ROUTE_UNRESOLVED
  NEXT: "го"

- STEP: S1
  GOAL: Return realm pipeline contract key
  INPUTS: [TARGET_REALM_KEY?]
  TARGETS: [TARGET_REALM_KEY?]
  ACTIONS:
    - For realm routes return TARGET_PIPE_KEY = corresponding PIPE.* key (resolved via realm INDEX_MANIFEST)
    - For standalone return ROOT_ENTITY_KEY as final target
  OUTPUTS: [TARGET_PIPE_KEY?, ROOT_ENTITY_KEY?]
  CHECKS: []
  FAIL: UE.FAIL.MISSING_KEY
  NEXT: "го"

## [M] FAIL_CODES
- UE.FAIL.ROUTE_UNRESOLVED
- UE.FAIL.MISSING_KEY
- UE.FAIL.GATE_FAIL
- UE.FAIL.RULE_VIOLATION

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
