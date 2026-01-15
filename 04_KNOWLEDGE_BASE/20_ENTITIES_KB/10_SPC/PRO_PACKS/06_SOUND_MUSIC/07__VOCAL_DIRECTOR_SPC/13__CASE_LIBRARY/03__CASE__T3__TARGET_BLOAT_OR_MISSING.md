# SPC PRO PACK — CASE (T3) — MUST-HEAR TARGET BLOAT / MISSING (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/13__CASE_LIBRARY/03__CASE__T3__TARGET_BLOAT_OR_MISSING.md

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
UID: UE.KB.SPC.CASE.VOCAL_DIRECTOR.T3.TARGETS_BLOAT_OR_MISSING.001
OWNER: SYSTEM
ROLE: Case record for must-hear targets being missing, bloated, or filled with non-essential words. Maps symptom to type T3 and deterministic fix route (PB-02) with rerun gates G2→G3.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Case T3: must-hear target bloat/missing."
- REASON: "If targets are wrong, clarity and QA cannot be measured and work becomes subjective."
- IMPACT: "Rebuilds P0 priorities and phrase protection deterministically."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.CASE.VD.T3.001

---

## CASE_HEADER
CASE_HEADER:
- CASE_ID: CASE.VD.T3.001
- type_code: T3
- severity: FAIL
- primary_gate_impacted: G2 (and downstream G3)
- audible_symptom:
  - "Hook feels unclear because the system is trying to 'save' too many words."
  - "Key message not prioritized; listener doesn't know what to latch onto."
- typical_context:
  - "Initial target lists created ad-hoc or copied from full lyrics without pruning."

---

## DIAGNOSIS
DIAGNOSIS:
- why_this_type:
  - "Failure is at the target definition layer (P0 missing or bloated)."
  - "Downstream intelligibility rules cannot be applied consistently without a correct P0."
- evidence_checks:
  - 1) Check MUST_HEAR_WORDS exists (if not → T3 confirmed).
  - 2) Check P0 count: if >8 → bloat; if 0 → missing.
  - 3) Scan P0 for fillers (pronouns, function words) and duplicates.
  - 4) Check whether meaning is phrase-based (if yes, phrases must be promoted).
  - 5) Confirm CLARITY_TARGETS exist (Target A mandatory).

---

## FIX_ROUTE
FIX_ROUTE:
- primary_playbook: PB-02
- tools_to_run:
  - T02 (targets builder) (recommended)
  - T03 (phrase promotion helper) (recommended)
- one_axis: A1
- patch_scope:
  - "Rebuild MUST_HEAR_WORDS (P0 3..8) + MUST_HEAR_PHRASES (1..2 preferred) + CLARITY_TARGETS."
- do_not_change:
  - "Do not change delivery profile, breath policy, stacking, arc, take pack during this patch."
  - "Do not rewrite lyrics."

---

## RERUN_GATES
RERUN_GATES:
- sequence:
  - G2
  - G3
- verification:
  - "P0 is minimal and meaningful; Target A exists; intelligibility checks become testable."

---

## NEGATIVE_SPEC (WHAT TO AVOID)
NEGATIVE_SPEC:
- avoid:
  - "Putting every word of the hook into P0 'just in case'."
  - "Including fillers in P0 (weakens priorities)."
  - "Inventing phrases not present in lyrics."
  - "Fixing by lyric rewrite (forbidden) instead of correct targeting."

---

## NOTES (OPTIONAL)
NOTES:
- edge_cases:
  - "If hook is extremely short, P0 may be 2 with explicit note; prefer phrase promotion to keep meaning."
- escalation_needed: NO

--- END.
