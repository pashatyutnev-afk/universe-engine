# SPC PRO PACK — PLAYBOOK (PB-08) — COMPLIANCE_ONE_AXIS_PATCH (F1..F5) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/08__PLAYBOOKS/08__PB-08__COMPLIANCE_ONE_AXIS_PATCH.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: PLAYBOOK
PLAYBOOK_ID: PB-08
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PB.VOCAL_DIRECTOR.PB08.COMPLIANCE_ONE_AXIS_PATCH.001
OWNER: SYSTEM
ROLE: One-axis compliance repair procedure: remove/convert scope violations using fixed forbidden classes (F1..F5). Uses T13 audit and T14 escalation formatting when ownership-bound content must be converted. Hard-fail remediation requires removing F1 (lyric rewrite) and F4 (mix/master chains). Rerun G9.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Playbook PB-08 COMPLIANCE_ONE_AXIS_PATCH for VOCAL_DIRECTOR."
- REASON: "Forbidden content breaks auditability and entity boundaries; must be removed deterministically."
- IMPACT: "Restores scope-safe outputs and prevents repeated drift."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PB.VD.PB08.001

---

## 0) PURPOSE (ONE AXIS)
Axis: A7 (Compliance / escalation-only)

Fixes:
- scope violations:
  - F1 lyric rewrite/replacement
  - F2 structure ownership language
  - F3 arrangement ownership language
  - F4 mix/master chain prescriptions
  - F5 guessing/unsupported claims

Does NOT fix:
- any craft axis (targets, attacks, breath, arc, stacking, take pack)

---

## 1) INPUTS REQUIRED
Must have:
- candidate output text (pack/notes/contracts) to audit

Tools used:
- T13 SCOPE_AUDIT_CHECKLIST
- T14 ESCALATION_NOTE_FORMATTER (only if converting ownership-bound content)

---

## 2) PATCH SCOPE (WHAT TO CHANGE)
You may change ONLY:
- remove forbidden text segments
- convert ownership-bound directives into ESCALATION_NOTES (principles-only)
- add/update SCOPE_AUDIT result

---

## 3) DO NOT CHANGE (PROTECTED)
Do NOT change these blocks in PB-08:
- MUST_HEAR targets
- intelligibility/breath/arc/stacking/take pack blocks
- any craft solutions

PB-08 is cleanup only.

---

## 4) PROCEDURE (STEPS)
Step 1 — Run scope audit (T13)
- Produce SCOPE_AUDIT (F1..F5)

Step 2 — Hard-fail removals (mandatory)
If F1=YES:
- remove all lyric rewrite/replacement content
If F4=YES:
- remove all mix/master chain prescriptions

Step 3 — Ownership conversion (if needed)
If F2=YES or F3=YES:
- convert those parts into ESCALATION_NOTES using T14:
  - owner
  - problem + evidence
  - request (principles-only)
  - must_keep
  - success_criteria
  - next_check

Step 4 — Guessing cleanup
If F5=YES:
- remove unsupported claims
- convert to GAP request / uncertainty statements (without inventing)

Step 5 — Re-run T13
- SCOPE_AUDIT must become all NO

Step 6 — Apply patch
- Ensure no new craft changes were introduced

---

## 5) RERUN GATES
Required rerun:
- G9

---

## 6) HARD STOPS
Stop if:
- after removal/conversion, F1 or F4 remain YES
- owner cannot be identified for escalation (request owner; do not guess)
- the run tries to “solve” craft problems during cleanup (violates PB-08 scope)

---

## 7) SUCCESS CRITERIA
PB-08 is successful when:
- SCOPE_AUDIT: F1..F5 all NO
- any ownership content is expressed only as ESCALATION_NOTES
- G9 passes

---

## 8) TRACE
TRACE:
- PLAYBOOK: PB-08
- AXIS: A7 (Compliance)
- TOOLS: T13 (+ T14 if conversion)
- RERUN: G9

--- END.
