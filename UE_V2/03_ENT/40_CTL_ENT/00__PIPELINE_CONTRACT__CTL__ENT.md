FILE: UE_V2/03_ENT/40_CTL_ENT/00__PIPELINE_CONTRACT__CTL__ENT.md
SCOPE: UE_V2 / 03_ENT / 40_CTL_ENT
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: CTL_ENT
UID: UE.V2.ENT.PIPE.CTL_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: CTL_ENT
NAV_RULE: Contract has no RAW

---

## [M] PURPOSE
CTL PIPELINE_CONTRACT — корневой роутер контроллеров.
Определяет, какой CTL-реалм использовать (TPL/MUS/VID/WEB/LIB) и какой контракт/план ключей вернуть.
RAW не хранит, работает через KEY и INDEX_MANIFEST.

## [M] HARD_RULES
- RAW запрещён внутри CONTRACT.
- Все ссылки: только KEYS.
- MODE REPO: никаких правок репозитория.
- Выход: TARGET_REALM_KEY + TARGET_PIPE_KEY + (optional) ROUTE_HINT_KEYS.

## [M] REQUIRED_KEYS
- INDEX_MANIFEST
- PIPELINE_CONTRACT
- REALM.TPL_CTL
- REALM.MUS_CTL
- REALM.VID_CTL
- REALM.WEB_CTL
- REALM.LIB_CTL

## [M] ROUTING (keys only)
- If request mentions templates / “шаблон” / “tpl” -> REALM.TPL_CTL
- If request mentions music / suno / udio / lyrics / track / release -> REALM.MUS_CTL
- If request mentions video / shot / prompt video / export video -> REALM.VID_CTL
- If request mentions web / html / css / js / a11y / seo / block -> REALM.WEB_CTL
- If request mentions policy / safe copy / naming / shared lib / negative spec -> REALM.LIB_CTL
- Else -> choose by artifact hints:
  - presence of LYRICS/PROMPT_PACK -> MUS
  - presence of SHOT_PLAN/VID_BRIEF -> VID
  - presence of HTML_BUNDLE/WEB_BRIEF -> WEB
  - else -> LIB (safe defaults)

## [M] STEP-RUN
- STEP: S0
  GOAL: Determine target realm for CTL usage
  INPUTS: [TASK_TEXT, ARTIFACT_HINTS?]
  TARGETS: [INDEX_MANIFEST]
  ACTIONS:
    - Classify domain intent using ROUTING rules
    - Output TARGET_REALM_KEY
  OUTPUTS: [TARGET_REALM_KEY]
  CHECKS: [TARGET_REALM_KEY_RESOLVABLE]
  FAIL: UE.FAIL.ROUTE_UNRESOLVED
  NEXT: "го"

- STEP: S1
  GOAL: Return realm-specific pipeline contract key hint
  INPUTS: [TARGET_REALM_KEY]
  TARGETS: [TARGET_REALM_KEY]
  ACTIONS:
    - Return TARGET_PIPE_KEY:
      - REALM.TPL_CTL -> (use templates realm PIPELINE_CONTRACT key via its index)
      - REALM.MUS_CTL -> (use music realm PIPELINE_CONTRACT key via its index)
      - REALM.VID_CTL -> (use video realm PIPELINE_CONTRACT key via its index)
      - REALM.WEB_CTL -> (use web realm PIPELINE_CONTRACT key via its index)
      - REALM.LIB_CTL -> (use shared lib PIPELINE_CONTRACT key via its index)
    - Provide ROUTE_HINT_KEYS (optional) = [TARGET_REALM_KEY]
  OUTPUTS: [TARGET_PIPE_KEY, ROUTE_HINT_KEYS?]
  CHECKS: []
  FAIL: UE.FAIL.GATE_FAIL
  NEXT: "го"

## [M] FAIL_CODES
- UE.FAIL.ROUTE_UNRESOLVED
- UE.FAIL.MISSING_KEY
- UE.FAIL.GATE_FAIL
- UE.FAIL.RULE_VIOLATION

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
