# PLAYBOOK — FINAL QA PRECHECK (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/03__METHOD_PLAYBOOKS/08__PLAYBOOK__FINAL_QA_PRECHECK.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: PLAYBOOK
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.FINAL_QA_PRECHECK.001
OWNER: SYSTEM
ROLE: Deterministic final precheck before “release-ready” generation: validate prompt contract clarity, minimal drift risk, and alignment to QA/VAL criteria; apply at most one minimal patch if needed; emit trace.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created final QA precheck playbook: checklist + decision rules + last-min patch discipline."
- REASON: "Final pass must not regress; precheck catches obvious issues before burning generations."
- IMPACT: "Higher pass rate and fewer last-minute surprises."
- CHANGE_ID: UE.CHG.2026-01-14.KB.SPC.PACK.PROMPT.PB.FINAL.001

---

## 0) INPUTS (REQUIRED)
- CURRENT_BASELINE_PROMPT_CONTRACT (frozen)
- TARGET_RELEASE_CONTEXT:
  - full song / loop / short
  - language
  - vocal plan (A/B)
- TARGET_CRITERIA_UIDS (UID-only) (optional but preferred):
  - QA gates
  - VAL criteria
- LAST_PATCH_BUDGET:
  - max one patch
  - max 1–3 line edits

---

## 1) OUTPUTS
- PRECHECK_RESULT: PASS / REWORK / STOP
- TOP_ISSUES (0–3)
- LAST_PATCH (if allowed and needed)
- RECHECK_PLAN (what to rerun)
- TRACE_NOTES

---

## 2) PRECHECK CHECKLIST (FAST)
### C1 — Contract completeness
- [ ] STYLE_BLOCK present and non-contradictory
- [ ] STRUCTURE_BLOCK has explicit sections (if full song)
- [ ] VOCAL_INTENT_BLOCK clear roles (if multi-voice)
- [ ] NEGATIVE_SPEC_BLOCK targeted and not spam
- [ ] CONSTRAINTS_BLOCK includes duration/format

### C2 — Hook & structure sanity
- [ ] chorus/hook explicitly defined
- [ ] hook intent is clear (early/strong if required)
- [ ] verse vs chorus roles not blurred

### C3 — Vocal diversity sanity (if relevant)
- [ ] role ownership per section exists
- [ ] contrast levers present (2–3 max)
- [ ] negatives include “avoid same voice” if needed

### C4 — Repetition control sanity
- [ ] repetition allowed only in chorus/hook (if policy)
- [ ] verses have novelty constraint (if past issue)

### C5 — Style fingerprint sanity
- [ ] anchors count is reasonable (3–6)
- [ ] dominance rule exists if fusion used
- [ ] no conflicting descriptors

### C6 — Control density sanity
- [ ] prompt not overloaded (no “everything list”)
- [ ] changes since last baseline are traceable (one-axis discipline)

---

## 3) DECISION RULE (PASS/REWORK/STOP)
PASS:
- all C1 items PASS
- and no CRITICAL contradictions found
- and control density is acceptable

REWORK:
- 1–2 localized issues that can be fixed with ≤ 1 minimal patch
- examples:
  - chorus label missing
  - negatives missing for a known failure mode
  - voice contrast block too vague

STOP:
- missing core inputs OR prompt is contradictory/overloaded
- multiple critical issues that would require rewrite
→ go back to CORE WORKFLOW or DIAGNOSE & REWORK.

---

## 4) LAST PATCH DISCIPLINE (ONE PATCH MAX)
If REWORK and patch is allowed:
- choose one primary issue
- apply PATCH MINIMAL CHANGE (one axis)
- do not alter unrelated blocks

Allowed last patch examples:
- add explicit chorus hook line
- add 3–6 voice negatives
- reduce style anchors and add dominance rule
- add verse novelty constraint

Not allowed in last patch:
- rewrite all lyrics
- change genre + tempo + vocals together

---

## 5) RECHECK PLAN
If target criteria UIDs provided:
- rerun those UIDs after patch

If not provided:
- use internal mini recheck:
  - hook clarity
  - chorus distinctness
  - voice separation
  - repetition control
  - style consistency

---

## 6) PRECHECK REPORT (COPY)
PRECHECK_REPORT:
- DATE: YYYY-MM-DD
- BASELINE_ID:
- RESULT: PASS/REWORK/STOP
- TOP_ISSUES:
  - <issue>
- PATCH_APPLIED: YES/NO
- PATCH_AXIS:
- RECHECK_UIDS (UID-only):
  - <uid>
- NOTES:
- TRACE:
  - MEMORY_REUSE: YES/NO
  - WEB_LOOKUP_USED: YES/NO

---

## 7) HARD FAIL CONDITIONS
FAIL IF:
- precheck claims PASS while C1 is incomplete
- patch exceeds minimal delta rule
- stop conditions ignored (rewrite needed but patch attempted)

---

## 8) RELATED (UID-ONLY)
XREF:
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.PATCH_MIN.001 | WHY: last patch method
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.DIAG_REWORK.001 | WHY: escalation path
- UE.KB.QA.STD.CONNECTOR.001 | WHY: QA criteria and trace discipline

--- END.
