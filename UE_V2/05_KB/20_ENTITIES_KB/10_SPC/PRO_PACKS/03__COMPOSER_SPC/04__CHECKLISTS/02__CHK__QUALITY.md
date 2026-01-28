# 02__CHK__QUALITY — COMPOSER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/03__COMPOSER_SPC/04__CHECKLISTS/02__CHK__QUALITY.md
SCOPE: KB — SPC Pro Pack — Composer — Checklist (Quality)
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS / 04__CHECKLISTS
DOC_TYPE: CHECKLIST
CHECKLIST_TYPE: QUALITY
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.COMPOSER.CHK.QUALITY.001
OWNER: SPC (Composer)
ROLE: Verify structure, clarity, testability, and completeness of O1/O2 (and optional motif/harmony/melody add-ons) before gates.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Quality checklist initialized for Composer SPC pack."
- REASON: "Catch composition defects before stricter gates."
- IMPACT: "Defines must-have blocks and composer quality signals."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.COMPOSER.CHK.QUAL.001

---

## PASS/REWORK RULE
- PASS: all MUST items satisfied
- REWORK: any MUST item missing or non-testable

---

## O1 MUST (COMPOSER_TASK_CARD)
[ ] Q1 O1 includes GOAL (single sentence)
[ ] Q2 O1 includes DELIVERABLES (O1/O2/(O3/O4/O5))
[ ] Q3 O1 includes CONSTRAINTS (1–5)
[ ] Q4 O1 includes ACCEPTANCE that is testable (>=2 checks)
[ ] Q5 O1 includes SCOPE (in/out)
[ ] Q6 O1 includes ROUTING notes (if role split exists)
[ ] Q7 O1 includes TRACE_MIN (task id + outputs list)

---

## O2 MUST (COMPOSITION_EXEC_PLAN)

### Structure blocks
[ ] Q8 Form map has timings (approx) + musical intent per section
[ ] Q9 Hook/motif plan exists (musical motif, not only “lyrics hook”)
[ ] Q10 Harmony logic exists (tonal center / modal color + tension/release notes)
[ ] Q11 Melody contour guide exists OR explicitly N/A (if instrumental/no lead)
[ ] Q12 Contrast plan exists (where/why changes happen)
[ ] Q13 Repetition control rules exist (identity vs variation)
[ ] Q14 Validation route exists (checklists then gates order)
[ ] Q15 Trace block exists (TOPICS_LOADED + validations + next action)

---

## TESTABILITY CHECKS (MUST)
[ ] T1 Hook motif recognition check is defined (<=10–12s placement or explicit rule)
[ ] T2 “Hummability/recognition after 1–2 repeats” test exists for motif
[ ] T3 Tonal center / modal color is not contradictory across sections (stated or intentionally shifted)
[ ] T4 One-lever change rule present if multiple motifs/variants exist

---

## QUALITY RED FLAGS (CAUSE REWORK)
If any true → REWORK:
[ ] R1 Vague wording without musical decisions (“красиво/мощно” без мотива/логики)
[ ] R2 No timings / no map (generic “intro/verse/chorus” only)
[ ] R3 Motif described as “some catchy melody” with no fingerprint (contour/rhythm cell)
[ ] R4 Harmony described as “nice chords” with no tonal logic
[ ] R5 No trace / no validation route

---

## OUTPUT OF THIS CHECKLIST
Record:
- QUALITY_STATUS: <PASS|REWORK>
- MISSING_ITEMS:
  - <list Q# / T#>
- RED_FLAGS:
  - <list R#>
- NEXT_ACTION:
  - if REWORK: PB-02 axis usually motif/harmony/melody/structure/clarity
  - if PASS: proceed to CHK-COMPLIANCE then gates

---

## REQUIRED UID REFERENCES
- PLAYBOOK (repair):
  - UE.KB.SPC.PACK.COMPOSER.PB.DIAG_REWORK.001
- RUBRIC:
  - UE.KB.SPC.PACK.COMPOSER.RUBRIC.001

---
END
