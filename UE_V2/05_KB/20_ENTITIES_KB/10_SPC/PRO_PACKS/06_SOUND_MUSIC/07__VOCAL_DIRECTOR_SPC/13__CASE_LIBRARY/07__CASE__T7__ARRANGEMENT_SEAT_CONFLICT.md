# SPC PRO PACK — CASE (T7) — ARRANGEMENT SEAT CONFLICT (REQUIRES ESCALATION) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/13__CASE_LIBRARY/07__CASE__T7__ARRANGEMENT_SEAT_CONFLICT.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: CASE
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.CASE.VOCAL_DIRECTOR.T7.ARRANGEMENT_SEAT_CONFLICT.001
OWNER: SYSTEM
ROLE: Case record for arrangement/seat conflicts where intelligibility cannot be restored within VOCAL_DIRECTOR scope (no mix chains, no arrangement ownership). Requires escalation to Arranger/Producer using T14 format. Rerun G3 after owner response.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Case T7: arrangement seat conflict requiring escalation."
- REASON: "Some masking is structural (competing lead elements) and cannot be fixed by performance directives alone."
- IMPACT: "Forces ownership-safe escalation instead of illegal production prescriptions."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.CASE.VD.T7.001

---

## CASE_HEADER
CASE_HEADER:
- CASE_ID: CASE.VD.T7.001
- type_code: T7
- severity: FAIL
- primary_gate_impacted: G3 (and may affect G5/G7)
- audible_symptom:
  - "Even with clean articulation, P0 is masked by dominant lead elements."
  - "Hook words disappear under competing synth/guitar lead or dense midrange."
- typical_context:
  - "Dense chorus arrangement; lead synth/guitar competes with vocal hooks."

---

## DIAGNOSIS
DIAGNOSIS:
- why_this_type:
  - "Root cause is arrangement seat conflict, not performer technique."
  - "Fix requires arrangement/production ownership; VOCAL_DIRECTOR must escalate."
- evidence_checks:
  - 1) Confirm P0 targets are correct (if not, T3 first).
  - 2) Confirm breath splits are not the root cause (if yes, T2/T4 first).
  - 3) Confirm stacking is not the root cause (if yes, T6 first).
  - 4) Test a clean, low-intensity take: if P0 still masked, seat conflict is likely.
  - 5) Identify section/time-window where masking occurs (hook attacks, chorus downbeat).

---

## FIX_ROUTE
FIX_ROUTE:
- primary_playbook: NONE (escalation-only)
- tools_to_run:
  - T14 (escalation note formatter) (mandatory)
- one_axis: A7 (scope-safe escalation)
- patch_scope:
  - "Create escalation note to Arranger/Producer requesting perceptual space for P0 attacks (principles only)."
- do_not_change:
  - "Do not prescribe mix/master plugin chains."
  - "Do not prescribe exact instrumentation edits."
  - "Do not rewrite lyrics."

---

## RERUN_GATES
RERUN_GATES:
- sequence:
  - G3
- verification:
  - "After arrangement adjustment, P0 understood on first listen in hook."

Optional reruns:
- If stacking plan depends on arrangement: rerun G7
- If arc depends on arrangement contrast: rerun G5

---

## NEGATIVE_SPEC (WHAT TO AVOID)
NEGATIVE_SPEC:
- avoid:
  - "Suggesting EQ/compression/plugin chains as the fix."
  - "Owning arrangement decisions (adding/removing instruments)."
  - "Proceeding as if fixed without owner response."
  - "Vague escalation without section/time-window and success criteria."

---

## NOTES (OPTIONAL)
NOTES:
- escalation_needed: YES
- if escalation_needed:
  - owner: Arranger/Producer
  - next_check: "After owner response, rerun G3 (and G7/G5 if impacted)"
- example_escalation_principle:
  - "Request perceptual space on P0 consonant attacks in hook (principle-level)."

--- END.
