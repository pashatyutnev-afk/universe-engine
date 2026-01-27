# FILE: UE_V2/10_REL/02__READINESS_MATRIX.md
SCOPE: UE_V2
LAYER: 10_REL
DOC_TYPE: SPEC
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.REL.READY.001
OWNER: SYSTEM
TITLE: GLOBAL READINESS MATRIX (42 OBJECTS)

## MARKERS
- [M] INTENT
- [M] REQUIRED_METRICS
- [M] GATES
- [M] FLAGS
- [M] OUTPUT

## [M] INTENT
Дать единый критерий “готов/на переработку” для планирования календаря.

## [M] REQUIRED_METRICS
Minimum required:
- RI_t
- CF_3s_P50

Recommended:
- LRA
- WTI_t
- ΔAIR, ΔLM

## [M] GATES
Hard gates:
- RI_t >= 0.62  → PASS else FAIL
- CF_3s_P50 >= 11.5 dB → PASS else FAIL

Soft gates (advisory):
- LRA >= 8 LU recommended (unless target is “flat”)
- ΔAIR within allowed band for “same entity, not clones” (see AUD Spec)

## [M] FLAGS
- OK
- REWORK_REQUIRED (any hard gate FAIL)
- HOLD (missing inputs / incomplete package)
- ANOMALY_ALLOWED (LAW-13 declared + conforms to anomaly profile)

## [M] OUTPUT
For each track UID:
- READY_STATUS
- FAIL_REASON (if any)
- REWORK_TARGET (what to fix: RI / CF / mix / arrangement / package)
