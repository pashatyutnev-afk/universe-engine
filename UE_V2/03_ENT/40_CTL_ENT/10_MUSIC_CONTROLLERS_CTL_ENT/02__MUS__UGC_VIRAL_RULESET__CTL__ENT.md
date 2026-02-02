FILE: UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS_CTL_ENT/02__MUS__UGC_VIRAL_RULESET__CTL__ENT.md
SCOPE: UE_V2 / 03_ENT / 40_CTL_ENT / 10_MUSIC_CONTROLLERS_CTL_ENT
DOC_TYPE: CTL_ENTITY
DOMAIN: MUS_CTL_ENT
UID: UE.V2.ENT.CTL.MUS.UGC_VIRAL_RULESET.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: CTL_ENT
NAV_RULE: No RAW in entity docs
---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_UGC_VIRAL_RULESET_CTL
- ENTITY_CLASS: CTL
- UID: UE.V2.ENT.CTL.MUS.UGC_VIRAL_RULESET.001

## [M] PURPOSE
Правила UGC/viral-ready. Применяется только когда brief явно про shortform, ugc, viral.

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [MUS_BRIEF, TRACK_PLAN, PROMPT_PACK, LYRICS_FINAL?]
- NON_GOALS: [PD/rights, коллизии]

## [M] INPUTS / OUTPUTS
- Inputs: [MUS_BRIEF, TRACK_PLAN?]
- Outputs: [CTL_DECISION, CTL_FINDINGS, REQUIRED_FIXES, FAIL_CODE?]

## [M] RULESET
- R1: Для shortform хук должен появиться рано (до 10 сек по структуре).
- R2: Один доминирующий вайб, без резких скачков.
- R3: Читабельные фразы, без перегруза текста.
- R4: Не применять если brief не про shortform.

## [M] DECISION_MATRIX
- IF brief не про ugc -> PASS
- IF нет TRACK_PLAN -> ASK
- IF хук поздно -> WARN
- ELSE -> PASS

## [M] VIOLATIONS
- V.UGC.HOOK_LATE
- V.UGC.CLUTTER

## [M] FAIL_CODES
- UE.FAIL.INPUT_ABSENT

## [M] KB SCOPE
- KB Inputs: [brief/plan]
- KB Outputs: [ugc findings]
- KB Boundaries: [не навязывать ugc]
- KB RAW refs: []

## [M] GATES
- PASS if: ugc условия соблюдены или контроллер не применим
- FAIL if: применим и структура противоречит цели без возможности фикса

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, QA_ENT]
- Handoff rules: WARN -> hook focus loop; PASS -> continue
