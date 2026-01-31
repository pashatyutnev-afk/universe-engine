FILE: UE_V2/07_DOM_AUD/00__PIPELINE_CONTRACT__DOM__AUD.md
SCOPE: UE_V2 / 07_DOM_AUD
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: DOM_AUD
UID: UE.V2.DOM.AUD.PIPELINE_CONTRACT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: Contract has no RAW

---

## [M] PURPOSE
Step-run contract for AUD domain.
Resolves AUD docs by KEY via INDEX_MANIFEST and executes minimal AUD workflow for mix/master decisions.

## [M] HARD_RULES
- No RAW inside this contract.
- Resolve targets via INDEX_MANIFEST only.
- Minimal opens first: AUD.MET.RI + AUD.MASTER.TARGETS (+ AUD.MIX.LOW if mix task).

## [M] REQUIRED_KEYS (must exist in INDEX_MANIFEST)
- INDEX_MANIFEST
- PIPELINE_CONTRACT
- AUD.MET.RI
- AUD.MASTER.TARGETS

## [M] STEP-RUN (high level)

S0) SANITY
- ensure TASK_TEXT exists
- resolve INDEX_MANIFEST
- validate REQUIRED_KEYS exist

S1) LOAD_CORE
- open: AUD.MET.RI
- open: AUD.MASTER.TARGETS

S2) OPTIONAL_LOAD (by need)
- if scoring requested -> open AUD.ORUM.A / AUD.ORUM.B
- if wear texture involved -> open AUD.MET.WTI
- if CF sync needed -> open AUD.MET.CF
- if loudness range / dynamics analysis -> open AUD.MET.LRA
- if change constraints -> open AUD.SPEC.DELTA
- if recovery needed -> open AUD.FAIL
- if anomaly calendar relevant -> open AUD.CAL.ANOM
- if low-end decisions -> open AUD.MIX.LOW

S3) OUTPUT
- emit AUD_TOKEN:
  - opened_keys
  - required_targets (master/mix constraints)
  - checks_required (metrics to validate)
- NEXT: "го"
