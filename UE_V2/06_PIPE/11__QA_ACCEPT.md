# FILE: UE_V2/06_PIPE/11__QA_ACCEPT.md
SCOPE: UE_V2
LAYER: 06_PIPE
DOC_TYPE: QA
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.QA.ACCEPT.001
OWNER: SYSTEM
TITLE: QA ACCEPT

## MARKERS
- [M] INTENT
- [M] SCORE_AXES
- [M] DECISIONS
- [M] OUTPUT

## [M] INTENT
Единый QA-гейт: превращать проверки в решение PASS/REWORK.

## [M] SCORE_AXES
- DOC: format integrity (VAL_DOC)
- DOMAIN: thresholds (VAL_AUD/VAL_VIS)
- DNA: “one entity” consistency (targets ok)
- CLONE: clone safety (Δ differs)
- NOISE: CTL_NOISE pass

## [M] DECISIONS
- PASS: все оси PASS
- REWORK_REQUIRED: любой FAIL
- STOP: только если CTL_READINESS вернул STOP (RAW missing / marker not confirmed / input absent)

## [M] OUTPUT
Acceptance Output (минимум):
- decision
- failed codes list (если REWORK)
- key metrics snapshot (если AUD/VIS)
