# SPC PRO PACK — GATE (G3) — INTELLIGIBILITY PASS (P0/P1) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/05__KB_GATES/03__GATE__INTELLIGIBILITY_PASS.md

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
UID: UE.KB.SPC.GATE.VOCAL_DIRECTOR.INTELLIGIBILITY.001
OWNER: SYSTEM
ROLE: Gate G3 validates that the output pack contains explicit intelligibility PASS/FAIL criteria tied to MUST-HEAR targets (P0/P1), including breath protection and consonant clarity. This is the core “intelligibility-first” gate for VOCAL_DIRECTOR.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Gate G3: Intelligibility Pass (P0/P1) for VOCAL_DIRECTOR Pro Pack."
- REASON: "Without explicit intelligibility criteria, vocal direction cannot be validated and becomes subjective."
- IMPACT: "Enforces testable clarity outcomes and drives deterministic repair routing."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.GATE.VD.INTELL.001

---

## 0) PURPOSE
This gate answers:
- Does the pack define a testable intelligibility checklist that guarantees MUST-HEAR targets land?

This gate does NOT judge audio; it validates that the pack has:
- explicit pass/fail criteria
- repair routing
- protection rules for must-hear words/phrases

---

## 1) REQUIRED INPUTS
Prerequisites:
- G1 PASS (inputs exist)
- G2 PASS (must-hear targets exist)

Inputs to validate:
- MUST_HEAR_WORDS / MUST_HEAR_PHRASES (P0/P1)
- INTELLIGIBILITY_GATES_CHECKLIST (the artifact this gate requires)

---

## 2) PASS / REWORK / FAIL CONDITIONS
### PASS
PASS if ALL are true:
- INTELLIGIBILITY_GATES_CHECKLIST exists and includes at least:
  - A) P0 understood on first listen (YES/NO)
  - B) P1 understood by second listen (YES/NO) OR explicitly N/A
  - C) No breath splits inside P0 phrases (YES/NO)
  - D) Consonant attacks of P0 words are protected (YES/NO)
  - E) Chorus/hook P0 clarity ≥ verse P0 clarity (YES/NO)
- Checklist defines HARD FAIL triggers:
  - any P0 item not understood → FAIL
  - breath split inside P0 phrase → FAIL

### REWORK
REWORK if:
- checklist exists but missing one or more required checks
- no hard fail triggers declared
- checks are not tied to P0/P1 targets (generic “make clear”)
Fix route:
- PB-03 (intelligibility diagnose & repair) to generate/checklist + directives
- PB-04 if density/breath issues are flagged

### FAIL
FAIL if:
- checklist missing entirely
- must-hear targets exist but checklist contradicts them (e.g., allows breath breaks inside P0)
- pack attempts to solve intelligibility by prescribing mix/master chains (scope violation)
FAIL implies:
- NOT READY; must rebuild intelligibility layer.

---

## 3) REQUIRED EVIDENCE (WHAT MUST BE SHOWN)
EVIDENCE_BLOCK must exist in output pack:
- INTELLIGIBILITY_GATES_CHECKLIST:
  - Gate A (P0 first listen):
  - Gate B (P1 by second listen):
  - Gate C (no breath split inside P0):
  - Gate D (consonant attacks protected):
  - Gate E (chorus clarity >= verse):
- HARD_FAIL_TRIGGERS:
  - HF-1:
  - HF-2:
- REPAIR_ROUTE:
  - if fail type T1/T3/T5/T6 -> PB-03
  - if fail type T2/T4 -> PB-04
- NOTES:
  - short mapping to MUST_HEAR targets

---

## 4) FIX ROUTE (PLAYBOOK MAPPING)
If REWORK:
- Apply PB-03 to produce a complete checklist + repair directives.

If FAIL due to density/breath:
- Apply PB-04 (breath/density scan + escalation).

After fixes:
- rerun G3, then proceed to G4 only if PASS.

---

## 5) COMMON FAIL MODES
- “Clarity” is stated but not testable (no YES/NO criteria).
- Breath policy missing; phrases split randomly.
- Stacking/harmonies used without protected zones → consonants vanish.
- Intelligibility “fixed” by mixing advice (out of scope).

---

## 6) OUTPUT FORMAT (MANDATORY)
G3_RESULT:
- VERDICT: PASS | REWORK | FAIL
- EVIDENCE_BLOCK:
  - INTELLIGIBILITY_GATES_CHECKLIST:
  - HARD_FAIL_TRIGGERS:
  - REPAIR_ROUTE:
  - NOTES:
- NEXT_STEP:
  - if PASS: "Proceed to G4 DELIVERY PROFILE COHERENCE"
  - if REWORK/FAIL: "Apply PB-03/PB-04 and rerun G3"

--- END.
