# FILE: UE_V2/10_REL/06__REWORK.md
SCOPE: UE_V2
LAYER: 10_REL
DOC_TYPE: SPEC
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.REL.REWORK.001
OWNER: SYSTEM
TITLE: REWORK_REQUIRED RULES

## MARKERS
- [M] INTENT
- [M] TRIGGERS
- [M] ACTIONS
- [M] RETURN_CRITERIA

## [M] INTENT
Единый протокол отправки трека на переработку и возврата в READY.

## [M] TRIGGERS
- RI_t < 0.62
- CF_3s_P50 < 11.5
- package incomplete (missing VIS or LOR when required)
- lore fails (CANON conflict / ungrounded)
- visual fails (forbidden elements / continuity break)

## [M] ACTIONS
- set status: REWORK_REQUIRED
- assign rework target: (READABILITY / ENERGY / MIX_LOW / VIS_SYNC / LORE_LOCK)
- generate rework note: 1–3 lines, strictly actionable

## [M] RETURN_CRITERIA
- hard gates PASS
- package completeness PASS
- updated logs present (RUN_LOG / QA_LOG minimal)
