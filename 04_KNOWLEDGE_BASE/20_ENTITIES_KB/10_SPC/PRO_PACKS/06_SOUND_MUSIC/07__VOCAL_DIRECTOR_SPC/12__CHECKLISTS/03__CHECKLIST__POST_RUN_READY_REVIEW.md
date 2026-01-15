# SPC PRO PACK — CHECKLIST (03) — POST-RUN: READY REVIEW (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/12__CHECKLISTS/03__CHECKLIST__POST_RUN_READY_REVIEW.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: CHECKLIST
CHECKLIST_CLASS: POST_RUN
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.CHK.VOCAL_DIRECTOR.POST_RUN.001
OWNER: SYSTEM
ROLE: Post-run operational checklist: final READY review for VOCAL_DIRECTOR packs. Recaps gates G1..G9, uses threshold guide (T16), checks output-pack tier compliance, and enforces scope audit cleanliness.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created POST-RUN READY review checklist for VOCAL_DIRECTOR."
- REASON: "Need a deterministic final sweep before calling a pack READY."
- IMPACT: "Fewer accidental releases of non-compliant or incomplete packs."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.CHK.VD.POST.001

---

## 0) PURPOSE
Finalize the run:
- confirm gate verdicts
- classify borderline cases consistently
- confirm the output pack matches its tier contract
- confirm scope compliance

If any FAIL:
- do not call READY; route fixes via T15.

---

## 1) GATE RECAP (G1..G9)
[ ] G1 PASS (inputs)
[ ] G2 PASS (must-hear targets)
[ ] G3 PASS (intelligibility: no hard fails)
[ ] G4 PASS (delivery coherence)
[ ] G5 PASS (arc/contrast) (required only for FULL)
[ ] G6 PASS (breath/singability)
[ ] G7 PASS (stacking safe) (required only if stacking_used=YES; required for FULL)
[ ] G8 PASS (take pack) (required for FULL)
[ ] G9 PASS (scope compliance)

Hard rule:
- If any gate is FAIL → stop and repair (T15 + PB).

---

## 2) BORDERLINE CLASSIFICATION (T16)
If any gate is borderline:
[ ] Use T16 Threshold Guide to classify:
    - PASS vs REWORK vs FAIL
[ ] If REWORK:
    - patch one axis only (PB)
[ ] Rerun required gates after patch.

---

## 3) OUTPUT PACK TIER COMPLIANCE
[ ] Determine tier: MIN / STD / FULL
[ ] Verify required blocks exist for the tier (see OUTPUT_PACKS README):
    - MIN: inputs + must-hear + scope audit
    - STD: + intelligibility + profile + breath + stacking decision
    - FULL: all blocks + arc + stacking safe + take pack
[ ] Verify block order matches canonical assembly order.

---

## 4) SCOPE FINAL CHECK (G9)
[ ] No lyric rewrites (F1 = NO)
[ ] No mix/master chains (F4 = NO)
[ ] Any structure/arrangement notes are escalation-only (T14 format)
[ ] No guessing (F5 = NO)

If any violation:
- apply PB-08 (A7) and rerun G9.

---

## 5) READY DECLARATION RULE
A pack may be called READY only if:
- required gates for its tier are PASS
- output pack tier compliance is satisfied
- scope audit is clean

---

## 6) TRACE
TRACE:
- CHECKLIST: POST_RUN
- UID: UE.KB.SPC.CHK.VOCAL_DIRECTOR.POST_RUN.001
- THRESHOLDS: T16
- FINAL: READY only after PASS

--- END.
