# FILE: UE_V2/10_REL/01__CAL_A.md
SCOPE: UE_V2
LAYER: 10_REL
DOC_TYPE: SPEC
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.REL.CALA.001
OWNER: SYSTEM
TITLE: CALENDAR A (42-DAY BREACH) — CONTRACT

## MARKERS
- [M] INTENT
- [M] INPUTS
- [M] OUTPUTS
- [M] PHASES
- [M] SCHEDULING_RULES
- [M] STOP_REASONS

## [M] INTENT
Сформировать 42-дневный выпуск как кривую воздействия, основанную на готовности и нейро-отклике.

## [M] INPUTS
- TRACK_SET: up to 42 objects (each has UID)
- readiness metrics: RI_t, CF_3s_P50, LRA, (optional: WTI, ΔAIR/ΔLM)
- Impact Predictor outputs: Alienation%, Rage%, Hope/Resonance%
- package completeness status: PACK.OK / PACK.MISS

## [M] OUTPUTS
- DAY_PLAN[1..42]:
  - DAY
  - TRACK_UID
  - TECH_PROFILE (RI/CF/LRA + key deltas)
  - VIS_PROMPT_REF (LAW-15)
  - LORE_TRIGGER_REF
  - FLAGS (OK/REWORK_REQUIRED/HOLD)

## [M] PHASES
Phase 1 (Day 1–14): NORMALIZATION
- target: Alienation < 30%

Phase 2 (Day 15–35): SYSTEM_EROSION
- target: Rage 50–70%

Phase 3 (Day 36–42): TOTAL_COLLAPSE
- target: Alienation > 80%
- enable: LAW-13 events allowed (Silence Point)

## [M] SCHEDULING_RULES
- Only READY tracks can be scheduled (see READINESS_MATRIX).
- If insufficient READY tracks for a phase:
  - fill with READY tracks nearest to target impact profile
  - or mark HOLD days (allowed), but must be explicit

## [M] STOP_REASONS
- missing readiness inputs for a track
- package missing for scheduled day (audio/vis/lore incomplete)
- UID invalid or duplicated
