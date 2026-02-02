FILE: UE_V2/03_ENT/30_ORC_ENT/02_CREATIVE_ORC_ENT/03__CRV__TREND_SYNTHESIZER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 02_CREATIVE_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: CRV_ORC_ENT
UID: UE.V2.ENT.ORC.CRV.TREND_SYNTHESIZER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: CRV_TREND_SYNTHESIZER
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.CRV.TREND_SYNTHESIZER.001

## [M] PURPOSE
Синтезирует TREND_TOKEN: паттерны трендов и “референсы как принципы”, а не как копирование.
Не делает веб-поиск сам по себе: работает с тем, что дано входом/пайпом.

## [M] INPUTS / OUTPUTS
- Inputs: [CREATIVE_BRIEF, IDENTITY_TOKEN, STYLE_TOKEN?]
- Outputs: [TREND_TOKEN, FAIL_CODE?]

## [M] TOKEN_SCHEMA (TREND_TOKEN)
- PATTERNS: [patterns]
- NOVELTY_LEVERS: [levers]
- AUDIENCE_SIGNALS: [signals]
- RISK_NOTES: [notes]
- FRESHNESS_HINT: string

## [M] INTERFACES (RAW only)
- Entry points (RAW):
- Dependencies (RAW):

## [M] KB SCOPE
- KB Inputs: [user-provided refs, domain norms]
- KB Outputs: [TREND_TOKEN]
- KB Boundaries: [no copying; principles only]

## [M] GATES
- PASS: тренды не конфликтуют с constraints и identity
- FAIL: тренд требует запретного или нарушает политику

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Handoff: TREND_TOKEN -> CONCEPT_TO_ARTIFACT_BRIDGE

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
