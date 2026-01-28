# SPC PRO PACK — CASE (T6) — STACKING MASKING (LAYERS REDUCE P0 CLARITY) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/13__CASE_LIBRARY/06__CASE__T6__STACKING_MASKING.md

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
UID: UE.KB.SPC.CASE.VOCAL_DIRECTOR.T6.STACKING_MASKING.001
OWNER: SYSTEM
ROLE: Case record for stacking-induced masking where doubles/backs/harmonies reduce intelligibility of P0 targets. Maps symptom to type T6 with deterministic fix route PB-07 and rerun gates G7→G3.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Case T6: stacking masking reduces P0 clarity."
- REASON: "Layers often smear consonant attacks; safe stacking requires protected zones and QC fail triggers."
- IMPACT: "Enables lift without sacrificing word recognition."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.CASE.VD.T6.001

---

## CASE_HEADER
CASE_HEADER:
- CASE_ID: CASE.VD.T6.001
- type_code: T6
- severity: FAIL
- primary_gate_impacted: G7 (and verification in G3)
- audible_symptom:
  - "Hook feels bigger but words become less clear when layers enter."
  - "Consonant attacks smear; lead stops being the clear foreground."
- typical_context:
  - "Full-line doubling, harmonies over hook attacks, wide backs during chorus."

---

## DIAGNOSIS
DIAGNOSIS:
- why_this_type:
  - "Root cause is layers masking P0 attacks/phrases."
  - "Fix is placement/protection/QC, not lyric or mix chain."
- evidence_checks:
  - 1) Confirm stacking_used is YES (or layers are present).
  - 2) Identify where clarity drops: chorus line, phrase, or specific P0 word.
  - 3) Check whether stacking overlaps P0 attacks (if yes → primary cause).
  - 4) Check if protected zones exist and are explicit (if not → fail).
  - 5) Confirm breath splits are not the root issue (if yes, treat as T2/T4).

---

## FIX_ROUTE
FIX_ROUTE:
- primary_playbook: PB-07
- tools_to_run:
  - T11 (stacking safe planner) (recommended)
- one_axis: A5
- patch_scope:
  - "Rebuild stacking plan minimal-first + define explicit protected zones (P0 phrases + P0 attacks) + QC rules with fail triggers."
- do_not_change:
  - "Do not rewrite lyrics."
  - "Do not prescribe mix/master chains."
  - "Do not change arc/levers or breath policy in the same patch."

---

## RERUN_GATES
RERUN_GATES:
- sequence:
  - G7
  - G3
- verification:
  - "P0 first listen remains YES after layering."
  - "Fail trigger cleared: stacking no longer reduces P0 clarity."

---

## NEGATIVE_SPEC (WHAT TO AVOID)
NEGATIVE_SPEC:
- avoid:
  - "Full-line doubling across chorus."
  - "Layers over P0 attacks by default."
  - "Vague protected zones ('important words') instead of explicit lists."
  - "Fixing masking by adding more layers."

---

## NOTES (OPTIONAL)
NOTES:
- edge_cases:
  - "If arrangement has a competing lead element masking P0, treat as T7 (seat conflict) and escalate."
- escalation_needed: POSSIBLE
- if escalation_needed:
  - owner: Arranger/Producer
  - next_check: "After owner response, rerun G3 (and G7 if stacking changes)"

--- END.
