# SPC PRO PACK — CHECKLISTS (README) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/12__CHECKLISTS/00__README__CHECKLISTS.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: README
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.CHECKLISTS.README.DRAFT.001
OWNER: SYSTEM
ROLE: Defines the checklist library for VOCAL_DIRECTOR Pro Pack: pre-run, during-run, and post-run checklists mapped to gates/tools. These are operational checklists (execution hygiene), not the gates themselves.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created CHECKLISTS README for VOCAL_DIRECTOR: checklist classes + mapping + file roadmap."
- REASON: "Need deterministic operational hygiene to reduce drift and missed steps."
- IMPACT: "More consistent runs; fewer regressions."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VD.CHECKLISTS.README.001

---

## 0) PURPOSE
Checklists are operator workflows that ensure the pack is executed consistently.

They do NOT replace:
- Tools (Txx) which generate artifacts
- Gates (Gx) which validate artifacts

They help:
- not missing required steps
- staying within scope
- enforcing one-axis patches

---

## 1) CHECKLIST CLASSES
### A) PRE-RUN (BEFORE ANY WORK)
Goal:
- ensure inputs and scope boundaries are clear
Maps to:
- G1, G9 (scope reminders)

### B) DURING-RUN (PIPELINE HYGIENE)
Goal:
- enforce correct order (G1→G9)
- enforce one-axis fixes
Maps to:
- T15 repair routing
- PB-xx playbooks

### C) POST-RUN (READY REVIEW)
Goal:
- final QA sweep before calling a pack READY
Maps to:
- G1..G9 recap + scope audit

---

## 2) MAPPING (CHECKLIST → GATES/TOOLS)
PRE-RUN:
- verify minimum inputs (G1) → T01
- verify scope boundaries (G9 rules) → T13/T14

DURING-RUN:
- must-hear build (G2) → T02/T03
- intelligibility (G3) → T04/T05
- profile coherence (G4) → T06/T07
- arc/contrast (G5) → T08
- breath/density (G6) → T09/T10
- stacking safe (G7) → T11
- take pack (G8) → T12
- scope audit (G9) → T13
- repair router (type→PB) → T15 + PB-01..PB-08

POST-RUN:
- threshold classification → T16
- output pack contract compliance → OUTPUT_PACKS (MIN/STD/FULL)

---

## 3) RULES (ABSOLUTE)
- Never rewrite lyrics inside VOCAL_DIRECTOR outputs.
- Never output mix/master plugin chains.
- If outside scope: escalate (T14 format).
- If multiple problems: one-axis patch only (PB-08 discipline).

---

## 4) NEXT FILES (ORDER)
Proceed in numeric order:
- 01__CHECKLIST__PRE_RUN_MIN_INPUTS_AND_SCOPE.md
- 02__CHECKLIST__DURING_RUN_GATE_ORDER_AND_ONE_AXIS.md
- 03__CHECKLIST__POST_RUN_READY_REVIEW.md

--- END.
