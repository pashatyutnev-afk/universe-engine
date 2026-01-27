# FILE: UE_V2/07_DOM_AUD/02__ORUM_B.md
SCOPE: UE_V2
LAYER: 07_DOM_AUD
DOC_TYPE: ENGINE_CONTRACT
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.AUD.ORUMB.001
OWNER: SYSTEM
TITLE: ORUM-B (ENERGY / CREST / IMPACT)

## MARKERS
- [M] INTENT
- [M] INPUTS
- [M] OUTPUTS
- [M] RULES
- [M] ENERGY_GATE

## [M] INTENT
Макроконтур: сохранить “удар” и драму, управляя пиками/динамикой так, чтобы трек был живым и хитовым, а не плоским.

## [M] INPUTS
- mix or loudness targets (LUFS not primary here)
- CF target window (default by profile)
- LRA target/range (default by profile)
- special mode flags (LAW-13)

## [M] OUTPUTS
- CF_3s_P50 value + pass/fail
- LRA value + mode legality
- transient policy (snare/kick impact) + “glitch impacts” allowance

## [M] RULES
- “tight low end” must remain stable while peaks hit
- CF is the energy truth: if CF collapses → “energetic defect” even if LUFS is perfect
- allow hard contrast drops only when they are declared as intent (LAW-08/13)

## [M] ENERGY_GATE
- default release readiness: CF_3s_P50 >= 11.5
- “big chorus hit” profile: target CF_3s_P50 12.5–14.0
- “Point Zero / anomaly” profile: CF_3s_P50 13.0–14.5 (see CAL_ANOM)
- if CF_3s_P50 < threshold → REWORK_REQUIRED (see FAIL_AUD)
