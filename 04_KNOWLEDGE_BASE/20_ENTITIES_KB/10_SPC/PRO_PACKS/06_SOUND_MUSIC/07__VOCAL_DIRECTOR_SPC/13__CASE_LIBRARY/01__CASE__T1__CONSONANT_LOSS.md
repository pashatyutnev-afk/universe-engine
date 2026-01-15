# SPC PRO PACK — CASE (T1) — CONSONANT LOSS / SWALLOW (P0 ATTACKS) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/13__CASE_LIBRARY/01__CASE__T1__CONSONANT_LOSS.md

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
UID: UE.KB.SPC.CASE.VOCAL_DIRECTOR.T1.CONSONANT_LOSS.001
OWNER: SYSTEM
ROLE: Case record for consonant attack loss/swallowing on P0 targets. Maps symptom to type T1 and a deterministic fix route (PB-03) with rerun gates.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Case T1: consonant loss/swallow (P0 attacks)."
- REASON: "Most intelligibility failures come from consonants disappearing under lift or fast delivery."
- IMPACT: "Faster triage and consistent repair actions."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.CASE.VD.T1.001

---

## CASE_HEADER
CASE_HEADER:
- CASE_ID: CASE.VD.T1.001
- type_code: T1
- severity: FAIL
- primary_gate_impacted: G3
- audible_symptom:
  - "P0 words are not recognized on first listen; consonants feel missing."
  - "Ends of words vanish; words blur into vowels/noise."
- typical_context:
  - "Chorus lift, half-time stomp, aggressive delivery, dense instrumental bed."

---

## DIAGNOSIS
DIAGNOSIS:
- why_this_type:
  - "Primary failure is articulation/attack, not breath placement."
  - "P0 loss occurs at consonant onsets or tails."
- evidence_checks:
  - 1) Identify which P0 words fail (list 2–6).
  - 2) Check if failure is onset consonant, final consonant, or both.
  - 3) Confirm breath is NOT splitting P0 phrases (if it is, treat as T2/T4).
  - 4) Confirm stacking is not masking (if yes, treat as T6).
  - 5) Confirm issue persists even at lower intensity (if not, consider T8 lever issue).

---

## FIX_ROUTE
FIX_ROUTE:
- primary_playbook: PB-03
- tools_to_run:
  - T05 (attack protection notes) (recommended)
- one_axis: A1
- patch_scope:
  - "Add target→directive mapping for failing P0 words (<=3 directives each) + pass tests."
- do_not_change:
  - "Do not change lyrics."
  - "Do not add mix/master chains."
  - "Do not change breath policy unless breath split is the root cause."
  - "Do not change stacking plan unless masking is the root cause."

---

## RERUN_GATES
RERUN_GATES:
- sequence:
  - G3
- verification:
  - "HF-1 must be cleared: P0 understood on first listen in hook."

---

## NEGATIVE_SPEC (WHAT TO AVOID)
NEGATIVE_SPEC:
- avoid:
  - "Trying to solve by rewriting words/lyrics."
  - "Trying to solve by EQ/compressor/plugin chains."
  - "Adding more layers to 'help' clarity (often worsens)."
  - "Giving >3 directives per target (performer overload)."

---

## NOTES (OPTIONAL)
NOTES:
- edge_cases:
  - "If consonant loss happens only because chorus intensity is too high, consider T8 and prune arc levers (PB-05) after PB-03 clears basic attacks."
- escalation_needed: NO

--- END.
