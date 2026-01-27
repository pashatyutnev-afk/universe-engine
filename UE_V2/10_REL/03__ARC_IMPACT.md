# FILE: UE_V2/10_REL/03__ARC_IMPACT.md
SCOPE: UE_V2
LAYER: 10_REL
DOC_TYPE: SPEC
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.REL.ARC.001
OWNER: SYSTEM
TITLE: RESONANCE ARC CONSTRUCTION (IMPACT CURVE)

## MARKERS
- [M] INTENT
- [M] INPUTS
- [M] TARGETS
- [M] SELECTION_RULES
- [M] TIEBREAKERS

## [M] INTENT
Построить 42-дневную кривую воздействия из готовых треков.

## [M] INPUTS
- Impact Predictor outputs per track:
  - Alienation%
  - Rage%
  - Hope/Resonance%
- readiness status
- phase targets (from CAL_A)

## [M] TARGETS
Phase 1: Alienation < 30
Phase 2: Rage 50–70
Phase 3: Alienation > 80 (+ LAW-13 allowed)

## [M] SELECTION_RULES
- Choose tracks whose predicted impact best matches phase target.
- Avoid repeating same “impact shape” > 2 days in a row.

## [M] TIEBREAKERS
1) Higher readiness confidence
2) Stronger contrast vs previous day (if allowed)
3) Unique sonic signature within DNA bounds (avoid clones)
