# 02__CHK__QUALITY — MUSIC_PRODUCER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/02__MUSIC_PRODUCER_SPC/04__CHECKLISTS/02__CHK__QUALITY.md
SCOPE: KB — SPC Pro Pack — Music Producer — Checklist (Quality)
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS / 04__CHECKLISTS
DOC_TYPE: CHECKLIST
CHECKLIST_TYPE: QUALITY
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.CHK.QUALITY.001
OWNER: SPC (Music Producer)
ROLE: Verify structure, clarity, testability, and completeness of O1/O2 before gates.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Quality checklist initialized for Music Producer SPC pack."
- REASON: "Catch common defects before stricter gates."
- IMPACT: "Defines must-have blocks and quality signals."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MPROD.CHK.QUAL.001

---

## PASS/REWORK RULE
- PASS: all MUST items satisfied
- REWORK: any MUST item missing or non-testable

---

## O1 MUST (PRODUCER_TASK_CARD)
[ ] Q1 O1 includes GOAL (single sentence)
[ ] Q2 O1 includes DELIVERABLES (O1/O2/(O3))
[ ] Q3 O1 includes CONSTRAINTS (1–5)
[ ] Q4 O1 includes ACCEPTANCE that is testable (at least 2 checks)
[ ] Q5 O1 includes SCOPE (in/out)
[ ] Q6 O1 includes ROUTING notes (if role split exists)
[ ] Q7 O1 includes TRACE_MIN (task id + outputs list)

---

## O2 MUST (PRODUCTION_EXEC_PLAN)
### Structure blocks
[ ] Q8 Section map has timings (approx) + intent per section
[ ] Q9 Dynamics arc indicates peaks + contrast section
[ ] Q10 Seat plan defines foreground/mid/background roles
[ ] Q11 Hook plan exists (must-hear target + test cue)
[ ] Q12 Take direction exists IF vocal/lead present (else explicitly N/A)
[ ] Q13 Take acceptance triggers exist (PASS/REWORK conditions)
[ ] Q14 Validation route exists (checklists then gates order)
[ ] Q15 Trace block exists (TOPICS_LOADED + validations + next action)

---

## TESTABILITY CHECKS (MUST)
[ ] T1 Hook recognized check is defined (<=10s / <=12s etc)
[ ] T2 Intelligibility check is defined when vocal is relevant (phone speaker cue)
[ ] T3 Contrast check exists (explicit “where it dips/peaks”)
[ ] T4 “One lever change” rule is present if Hook B or variants exist

---

## QUALITY RED FLAGS (CAUSE REWORK)
If any true → REWORK:
[ ] R1 Overuse of vague words without actions ("круто", "мощно", "как обычно")
[ ] R2 No timings / no map (generic “intro/verse/chorus” only)
[ ] R3 Seat plan contains no decisions (only labels)
[ ] R4 No trace / no validation route

---

## OUTPUT OF THIS CHECKLIST
Record:
- QUALITY_STATUS: <PASS|REWORK>
- MISSING_ITEMS:
  - <list Q# / T#>
- RED_FLAGS:
  - <list R#>
- NEXT_ACTION:
  - if REWORK: PB-02 axis usually clarity/structure/completeness
  - if PASS: proceed to CHK-COMPLIANCE then gates

---

## REQUIRED UID REFERENCES
- PLAYBOOK (repair):
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.PB.DIAG_REWORK.001
- RUBRIC:
  - UE.KB.SPC.PACK.MUSIC_PRODUCER.RUBRIC.001

---
END
