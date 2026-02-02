FILE: UE_V2/03_ENT/40_CTL_ENT/90_SHARED_LIB_CTL_ENT/01__LIB__NEGATIVE_SPEC_LIBRARY__CTL__ENT.md
SCOPE: UE_V2 / 03_ENT / 40_CTL_ENT / 90_SHARED_LIB_CTL_ENT
DOC_TYPE: CTL_ENTITY
DOMAIN: LIB_CTL_ENT
UID: UE.V2.ENT.CTL.LIB.NEGATIVE_SPEC_LIBRARY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: CTL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: LIB_NEGATIVE_SPEC_LIBRARY_CTL
- ENTITY_CLASS: CTL
- UID: UE.V2.ENT.CTL.LIB.NEGATIVE_SPEC_LIBRARY.001

## [M] PURPOSE
Кросс-доменная библиотека negative specs: общие блоки запретов/ограничений для MUS/VID/WEB/DOC.
Цель — убрать типовые провалы, артефакты, рисковые формулировки и “лишние объекты”.

## [M] SCOPE
- TARGET_DOMAIN: MULTI
- APPLIES_TO: [PROMPT_PACK, NEGATIVE_PROMPT, LYRICS, HTML_BUNDLE, DOC_TEXT]
- NON_GOALS: [выбор контента вместо пользователя, конкретные палитры, монтаж]

## [M] INPUTS / OUTPUTS
- Inputs: [ARTIFACT_HINTS?, PROMPT_PACK?, LYRICS?, HTML_BUNDLE?, DOC_TEXT?]
- Outputs: [CTL_DECISION, CTL_FINDINGS, REQUIRED_FIXES]

## [M] RULESET (library blocks)

### [L] CORE_NO_COPY
- Avoid: direct imitation, “make it identical”, “same as <artist/track>”, quoting lyrics, recognizable lines.
- Fix: rewrite as principles, keep originality.

### [L] CORE_NO_GARBAGE
- Avoid: watermarks, logos, UI overlays, timestamps, random text overlays.

### [L] CORE_QUALITY_MIN (principles)
- Avoid: low quality, distorted audio, clipping, harsh sibilance, muddy mix, unintelligible vocals.
- Avoid (video/web): blur, compression artifacts, broken layout, unreadable text.

### [L] CORE_NO_EXTRA_SUBJECTS
- Avoid: adding extra people/objects not in brief.
- Fix: “single subject lock”, “no extra props”.

## [M] DECISION_MATRIX
- IF artifacts absent -> PASS
- IF negative constraints missing where expected -> WARN
- IF direct copy intent detected -> FAIL
- ELSE -> PASS

## [M] VIOLATIONS
- V.LIB.DIRECT_COPY
- V.LIB.MISSING_NEGATIVE
- V.LIB.EXTRA_SUBJECTS
- V.LIB.QUALITY_MIN

## [M] FAIL_CODES
- UE.FAIL.RULE_VIOLATION
- UE.FAIL.GATE_FAIL

## [M] KB SCOPE
- KB Inputs: [artifact hints and drafts]
- KB Outputs: [negative blocks + fixes]
- KB Boundaries: [не придумывать входы; не добавлять внешние ссылки]
- KB RAW refs: []

## [M] GATES
- PASS if: запреты и минимумы соблюдены
- FAIL if: обнаружено прямое копирование

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, QA_ENT, VAL_ENT]
- Handoff rules: FAIL -> stop; WARN -> patch; PASS -> continue
