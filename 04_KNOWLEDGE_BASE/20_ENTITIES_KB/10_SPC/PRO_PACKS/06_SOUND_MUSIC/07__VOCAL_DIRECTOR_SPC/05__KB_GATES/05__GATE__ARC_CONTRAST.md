# SPC PRO PACK — GATE (G5) — ARC / VERSE→CHORUS CONTRAST (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/05__KB_GATES/05__GATE__ARC_CONTRAST.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: GATE
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.GATE.VOCAL_DIRECTOR.ARC_CONTRAST.001
OWNER: SYSTEM
ROLE: Gate G5 validates that a performance arc exists and that verse→chorus contrast is explicit, minimal (1–3 levers), and compatible with intelligibility targets. Prevents flat vocals and random intensity swings.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Gate G5: Arc / Verse→Chorus Contrast for VOCAL_DIRECTOR Pro Pack."
- REASON: "Strong vocals require a section arc; without it, chorus lift is accidental and often harms clarity."
- IMPACT: "Consistent lift moments, clear section roles, and repeatable dynamics across takes."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.GATE.VD.ARC.001

---

## 0) PURPOSE
This gate answers:
- Does the pack contain an explicit performance arc map and clear verse→chorus contrast?

This gate validates:
- PERFORMANCE_ARC_MAP
- CONTRAST_LEVERS (1–3)
- SECTION_DELIVERY_NOTES / take goals alignment

---

## 1) REQUIRED INPUTS
Prerequisites:
- G1 PASS (inputs exist)
- Recommended: G2/G3 PASS (must-hear + intelligibility criteria exist) so “lift” can be checked against clarity

Inputs to validate:
- PERFORMANCE_ARC_MAP (by section)
- CONTRAST_LEVERS (declared)
- (optional) TAKE_GOALS_BY_SECTION

---

## 2) PASS / REWORK / FAIL CONDITIONS
### PASS
PASS if ALL are true:
- PERFORMANCE_ARC_MAP exists and covers all sections (at least Verse + Chorus)
- Chorus/hook section is explicitly marked as the lift/release moment
- CONTRAST_LEVERS are declared and limited to 1–3
- Levers are performer-executable (energy/delivery/articulation/dynamics/timing feel)
- Arc does NOT contradict intelligibility:
  - chorus lift does not require masking P0 targets (no “scream through hook” if it kills words)

### REWORK
REWORK if:
- arc exists but is flat (no clear lift) OR
- contrast levers are too many (>3) OR
- levers are vague (“more emotion”) without executable settings OR
- levers accidentally conflict with must-hear clarity but can be fixed by pruning/rebalancing
Fix route:
- PB-05 (arc/contrast design)
- or PB-08 axis A2 (arc) minimal patch

### FAIL
FAIL if:
- PERFORMANCE_ARC_MAP missing entirely
- chorus/hook cannot be identified (should fail earlier via G1)
- contrast requires out-of-scope changes (rewriting lyrics, structure changes without escalation)
- arc instructions directly violate intelligibility requirements (e.g., mandates delivery mode that makes P0 unintelligible without any mitigation)
FAIL implies:
- NOT READY; rebuild arc layer with PB-05 before proceeding.

---

## 3) REQUIRED EVIDENCE (WHAT MUST BE SHOWN)
EVIDENCE_BLOCK must exist in output pack:
- PERFORMANCE_ARC_MAP:
  - Verse:
  - Chorus:
  - Bridge (if exists):
- CONTRAST_LEVERS (1–3):
  - lever:
    - verse setting:
    - chorus setting:
- QC_ARC_CHECKS:
  - chorus_lift_present: YES/NO
  - lever_count_ok (<=3): YES/NO
  - intelligibility_preserved: YES/NO
- NOTES:
  - short explanation of why these levers were chosen

---

## 4) FIX ROUTE (PLAYBOOK MAPPING)
If REWORK:
- apply PB-05
OR
- apply PB-08 (AXIS=A2) minimal patch
Then rerun G5.

Proceed to G6 only after PASS.

---

## 5) COMMON FAIL MODES
- Verse/chorus same delivery; no lift.
- Too many levers; performer overload.
- Lift achieved by sacrificing intelligibility (bad trade).
- Bridge becomes a new identity (breaks continuity).
- Vague “more emotion” without section settings.

---

## 6) OUTPUT FORMAT (MANDATORY)
G5_RESULT:
- VERDICT: PASS | REWORK | FAIL
- EVIDENCE_BLOCK:
  - PERFORMANCE_ARC_MAP:
  - CONTRAST_LEVERS:
  - QC_ARC_CHECKS:
  - NOTES:
- NEXT_STEP:
  - if PASS: "Proceed to G6 BREATH / SINGABILITY"
  - if REWORK/FAIL: "Apply PB-05 or PB-08(A2) and rerun G5"

--- END.
