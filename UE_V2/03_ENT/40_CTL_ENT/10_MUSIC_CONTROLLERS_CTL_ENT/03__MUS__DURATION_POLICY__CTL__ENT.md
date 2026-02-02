FILE: UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS_CTL_ENT/03__MUS__DURATION_POLICY__CTL__ENT.md
SCOPE: UE_V2 / 03_ENT / 40_CTL_ENT / 10_MUSIC_CONTROLLERS_CTL_ENT
DOC_TYPE: CTL_ENTITY
DOMAIN: MUS_CTL_ENT
UID: UE.V2.ENT.CTL.MUS.DURATION_POLICY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: CTL_ENT
NAV_RULE: No RAW in entity docs
---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_DURATION_POLICY_CTL
- ENTITY_CLASS: CTL
- UID: UE.V2.ENT.CTL.MUS.DURATION_POLICY.001

## [M] PURPOSE
Диапазоны длительности по цели. Не навязывает, а предупреждает и просит закрепить выбор.

## [M] SCOPE
- TARGET_DOMAIN: MUS
- APPLIES_TO: [MUS_BRIEF, TRACK_PLAN]
- NON_GOALS: [качество аудио]

## [M] INPUTS / OUTPUTS
- Inputs: [MUS_BRIEF]
- Outputs: [CTL_DECISION, CTL_FINDINGS, REQUIRED_FIXES]

## [M] RULESET
- R1: shortform 15–45s (loopable допускается).
- R2: single 2:00–3:30 как базовый коридор.
- R3: album track 2:30–4:30 как базовый коридор.
- R4: точное значение из brief приоритетнее коридоров.

## [M] DECISION_MATRIX
- IF brief содержит duration -> PASS
- IF target unclear -> ASK
- IF duration вне коридора -> WARN
- ELSE -> PASS

## [M] VIOLATIONS
- V.DUR.UNSPECIFIED
- V.DUR.OUT_OF_BAND

## [M] FAIL_CODES
- UE.FAIL.INPUT_ABSENT

## [M] KB SCOPE
- KB Inputs: [brief]
- KB Outputs: [duration guidance]
- KB Boundaries: [без навязывания]
- KB RAW refs: []

## [M] GATES
- PASS if: duration определена или коридор согласован
- FAIL if: цель и duration неопределимы без входа

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT]
- Handoff rules: ASK/WARN -> brief уточнение; PASS -> continue
